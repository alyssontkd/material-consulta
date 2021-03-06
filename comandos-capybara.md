## Comando úteis para as implementações

```
opru4opup4r4p9u44u90ru094ur90u490ru409u04uu490ut904u9u490
```
##### Simulando a tecla ENTER
```
find('#id_componente').native.send_keys(:enter)
Ex: find('input[name=operacao]').native.send_keys(:enter)
```
##### Simulando a tecla TAB
```
find('#id_componente').native.send_keys(:tab)
Ex: find('input[name=operacao]').native.send_keys(:tab)
```

##### Clicando em um elemnto diferente de link ou botão
```
Clicando em um elemento do tipo SPAN e com Texto igual a "Login"
Ex: find("span[class='x-btn-button']", :text => 'Login').click

Ex: find("span[class='x-btn-button']").click
Ex: find("#btn-button']").click 
```
##### Buscando um seletor específico que contenha vários elemntos presentes na tela, e filtrando um componente pelo texto presente nele.
```
Filtrando o texto "Login" dentrio de um seletor que contenha vários elementos na tela.
Ex: have_selector "span[class='x-btn-button']", :text => "Login"
```
##### Quando preciso verificar se existe um determinado botão na página
`expect(page).to have_button('Texto do Botão')` ou `expect(page).to have_button('#id_componente')`
```
Verificando se existe o botão "Salvar" na página
Ex: expect(page).to have_button('Salvar')
```
##### Quando preciso verificar se não existe um determinado botão na página
`expect(page).to have_no_button('Texto do Botão')` ou `expect(page).to have_no_button('#id_componente')`
```
Ex: expect(page).to have_no_button('Salvar')
```
##### Quando preciso verificar se existe uma determinada mensagem na página
`expect(page).to have_content “mensagem”`
```
Ex: expect(page).to have_content “Bem vindo ao nosso Portal de Atendimento”
```
##### Quando preciso verificar se a página possui um botão ou link com uma determinada mensagem
`expect(page).to have_selector(:link_or_button, "mensagem")`
```
Ex: expect(page).to have_selector(:link_or_button, "Baixe o PDF aqui")
```
##### Clicar em um determinado botão presente na Tela (Pelo texto do botão)
`click_button 'Texto no Botão'`
```
Ex: click_button 'Acessar'
Ex: click 'Acessar'
```
##### Clicar em um determinado botão presente na Tela (Pelo identificador CSS)
`find('#id_componente').click`
```
Ex: find('#btn-login').click
```
##### Clicar em um determinado link presente na Tela (Pelo texto do link)
`click_link 'Texto do link'`
```
Ex: click_link 'Baixe o PDF aqui'
Ex: click 'Baixe o PDF aqui'
```
##### Buscar um componente do tipo INPUT pelo Seletor CSS e atribuir um valor
`find('#id_componente').set "valor"`
```
Ex: find('#senha').set senha
Ex: find('.obrigatotio').set "Este campo é de preenchimento obrigatório"
Ex: find('input[id=email]').set usuario
Ex: find('input[name=senha]').set senha
```
#### Para Marcar ou desmarcar um Checkbox
Marcar um checkbox `check('checkbox')`
Desmarcar um checkbox `uncheck('checkbox')`
```
Ex: check('#receber_noticias')
Ex: uncheck('#receber_noticias')
```
#### Escolher um Radio Button (Opção 1)
`fill_in('Texto Label do Radio', :with => 'Texto do radio')`
```
Ex: fill_in('Sexo', :with => 'Masculino')
```
#### Escolher um Radio Button (Opção 2)
`choose('#id_componente')`
```
Ex: choose('#turno_trabalho')
```
#### Escolher uma opção dentro do Combobox
`select('option', :from=>'#id_componente')` e `unselect`
```
Ex: select('Brasília - DF', :from=>'#cidades')
```
#### Anexar uma imagem
`attach_file('name_component', 'path_to_image')` ou `find('form input[type="file"]').set('path/to/file')`
```
Ex: attach_file('imagem', 'c:/imagens/minha_casa.png')
Ex: attach_file('data-file', 'c:/imagens/lista_cidades.csv')
Ex: find('form input[type="file"]').set('c:/imagens/lista_cidades.csv')
```
#### Executar um código javascript dentro da página
`page.execute_script("codigo javascript")`
```
Ex: page.execute_script("$('#area button.primary').click()")
```

#### Opções para enviar comandos de teclado (SendKeys)
```
null, cancel, help, backspace, tab, clear, return, enter, 
shift, left_shift, control, left_control alt, left_alt, pause, 
escape, space, page_up, page_down, end, home, left, arrow_left, 
uparrow_up, right, arrow_rightdown, arrow_down, insert, delete, 
semicolon, equals, numpad0, numpad1, numpad2, numpad3, numpad4, 
numpad5, numpad6, numpad7, numpad8, numpad9, multiply, add, 
separator, subtract, decimal, divide, f1, f2, f3, f4, f5, f6, 
f7, f8, f9, f10, f11, f12
```


Página de referência: `https://devhints.io/capybara`
