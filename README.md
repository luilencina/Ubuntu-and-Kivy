## TUTORIAL UBUNTU AND KIVY


##algumas considerações antes de começar:
- Tem que ter o WSL 2 instalado e inicializado na máquina. 
- Se a instalação do WSL 2 ocorrer algum erro, tente forçar a atualização do windows.
- kivy não funciona no ubuntu versão 20.04.
- a versão apenas "ubuntu" na microsoft store está com alguns erros no código, cuidado! 
- recomendado(até o momento): versão 18.04 LTS 

abrindo terminal você vai cadastrar seu nome e uma senha.
Ok! terminal pronto pra uso. aos comandos: 

dar um upgrade e update no ubuntu:
```
sudo apt update && sudo apt -y upgrade 
``` 

nesse comando vamos instalar o xrdp:
```
sudo apt install xrdp
```

agora instalar o xfce4, uma **DICA** nessa parte. vai abrir um *janela de cor roxa* para especificar
a porta de saida. apenas apertar *ENTER* nessa parte. outra coisa, faça *os dois comandos*, 
por algum motivo um precisa do outro. 
```
sudo apt install -y xfce4
```
```
sudo apt install -y xfce4-goodies
```

os próximos comandos são apenas trocas e inicio, mas necesários:
```
sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
```
```
sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
```
```
sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
```
```
echo xfce4-session >~/.xsession 
```


Nesse comando temos que mudar algo que esta no arquivo, então ponha o seguinte:
```
sudo nano /etc/xrdp/startwm.sh
``` 

ele vai abrir o arquivo startwm.sh, você ira comentar as *duas últimas linhas*, exemplo:
```
#test -x /etc/X11/Xsession && exec /etc/X11/Xsession
#exec /bin/sh /etc/X11/Xsession
```

e ao final do código vai adicionar isto:
```
#xfce4
startxfce4
```

CNTRL + O para salvar (p.s: não mude o nome do arquivo ao salvar)
CNTRL + X para sair do arquivo e voltar ao inicio do terminal.

agora é so digitar o comando:
```
 sudo /etc/init.d/xrdp start 
``` 

e a seguinte mensagem deve aparecer pra você: 
> * Starting Remote Desktop Protocol server *




