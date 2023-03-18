# Automa-o-em-python
Projeto de automação em python 3, aonde automatiza o envio de relatório e calcula os gasto e enviado para o e-mail do chefe

import pyautogui
import time 

pyautogui.PAUSE = 1
#1 passo entrar no sistema da empresa
pyautogui.hotkey("ctrl", "t")
pyautogui.write("https://pages.hashtagtreinamentos.com/aula1-intensivao-sistema")
pyautogui.press("enter")

time.sleep(5)
#Fazer o login no sistema da empresa
#Clicar no espaço
pyautogui.click(x=3391, y=427)
pyautogui.write('meulogin')
#fazer a senha
pyautogui.click(x=3566, y=534)
pyautogui.write('minhasenha')
#acesssar na pag
pyautogui.click(x=3593, y=608)

time.sleep(3)

#exporta a base de dados
pyautogui.click(x=3037, y=447)
pyautogui.click(x=4276, y=183)
pyautogui.click(x=4108, y=592)

pyautogui.click(x=3619, y=850)
time.sleep(3)

import pandas as pd
tabela= pd.read_csv(r"C:\Users\Gabriel\Downloads\Compras.csv", sep=';')
display(tabela)
total_gasto = tabela['ValorFinal'].sum()
quantidade = tabela['Quantidade'].sum()
preco_medio = total_gasto/quantidade
print('O total gasto é R${}'.format(total_gasto))
print('A quantidade total é R${}'.format(quantidade))
print('O preço medio é R${}'.format(preco_medio))

import pyperclip
pyautogui.PAUSE= 1

pyautogui.hotkey('ctrl','t')
pyautogui.write('https://mail.google.com/mail/u/0/#inbox')
pyautogui.press('enter')
pyautogui.click(x=2672, y=207)
pyautogui.click(x=3899, y=397)
pyautogui.write('pythonimpresssionador@gmail.com') #destinatario
pyautogui.press('tab') #escolher o destinario

pyautogui.click(x=3807, y=457) #clicando no assunto
pyperclip.copy('Relatório de Vendas') #escrevendo o assunto no assunto
pyautogui.hotkey('ctrl', 'v')

pyautogui.press('tab') #passando para o corpo

texto= f"""
Prezados,
Segue o relatório de comprass

Total Gasto: R${total_gasto:,.2f}
Quantidade de Produtos: R${quantidade:,.2f}
Preço Médio: R${preco_medio:,.2f}

Qualquer dúvida
Att; Gabriel
"""



pyperclip.copy(texto)
pyautogui.hotkey('ctrl', 'v')
#enviar
pyautogui.hotkey('ctrl','enter')
