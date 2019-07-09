Abra o Excel e pressiona `Alt + F11` para abrir o Visual Basic, cole o código abaixo e pressione o RUN.

```
Sub prcTrannsferir()

    Dim wbkDestino As Workbook
    Dim wBase As Worksheet
    Dim wDestino As Worksheet
    
    Dim intQtdGruposEnviados As Integer
    Dim intQtdItensPorPlanilha As Integer
    Dim intQtdItensEnviados As Integer
    Dim lngQtdItens As Double
    
    Set wBase = ThisWorkbook.Sheets("Plan1")  'Altere para o nome da sua guia que contens os dados
    
    lngQtdItens = wBase.Range("A65536").End(xlUp).Row
    
    intQtdItensPorPlanilha = 10 ' Informe aqui a quantidade de itens por planilha
    intQtdItensEnviados = 0  'não precisa alterar
    intQtdGruposEnviados = 0 ' não precisa alterar
    
    For x = 2 To lngQtdItens   'altere o valor 2 para a linha inicial dos dados da sua planilha
            
        If intQtdItensEnviados = 0 Then
            
            'Cria uma nova guia e cria um cabeçalho na primeira linha
            Set wbkDestino = Workbooks.Add
            Set wDestino = wbkDestino.Sheets.Add
            wDestino.Name = "Grupo " & intQtdGruposEnviados + 1
            
            wDestino.Cells(1, 1).Value = "Cod"
            wDestino.Cells(1, 2).Value = "Nome"
            wDestino.Cells(1, 3).Value = "Data"
            
            i = 2
        
        End If
        
        If intQtdItensEnviados < intQtdItensPorPlanilha Then
            
            'Se nao chegou ao limite de itens por planilha, copia os dados
            
            wDestino.Cells(i, 1).Value = wBase.Cells(x, 1).Value
            wDestino.Cells(i, 2).Value = wBase.Cells(x, 2).Value
            wDestino.Cells(i, 3).Value = wBase.Cells(x, 3).Value
        
            intQtdItensEnviados = intQtdItensEnviados + 1
            i = i + 1
        
        End If
        
        If intQtdItensEnviados = intQtdItensPorPlanilha Or x = lngQtdItens Then
            
            'Se chegou ao limite, inicia o contador de itens enviados e incrementa a quantidade de grupos
            wbkDestino.SaveAs ThisWorkbook.Path & "\" & wDestino.Name
            wbkDestino.Close
            intQtdItensEnviados = 0
            intQtdGruposEnviados = intQtdGruposEnviados + 1
            
        End If        
    Next x
End Sub
```
