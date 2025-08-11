# Documentação Linux Ubuntu 24.04

Obs: Comando sudo concede privilégio de administrador  
apt: gerenciador de pacotes

---

## Comandos:

- sudo apt update  
- sudo apt upgrade  
- sudo reboot  
- sudo apt install build-essential dkms linux-headers-$(uname -r)  
  Instala:
  - build-essential: ferramenta para compilar código-fonte  
  - dkms: recompilador de aplicações para compatibilidade com o Kernel do convidado (guest)

- cd /media/$USER/VBox_GAs_7.0.6  
  Caminha até o diretório onde está o aplicativo para instalar recursos adicionais de convidado  
  $USER é uma variável de ambiente que referencia o nome do usuário logado

- sudo ./VBoxLinuxAdditions.run  
  Executa a aplicação disponível no diretório acessado e instala os recursos adicionais

- lsmod | grep vbox  
  - lsmod: lista os módulos carregados no Kernel  
  - grep: filtra e exibe apenas as linhas que contenham o texto desejado (vbox, neste caso)  
  - vbox: prefixo comum dos nomes dos módulos do VirtualBox

---

- Criação de uma nova pasta na máquina física.(host)
  - Caminho: C:\VirtualBox-PastaCompartilhada
-Configuração da VM(guest)
 -Acesso à guia denominada Pasta Compartilhada
 -Criação de uma referência com o caminho C:\VirtualBox-PastaCompartilhada para acessar esta pasta pela VM

- Após ligar a VM:
  -Adicionada um novo usuário no grupo vboxsf: sudo $USER -aG vboxsf ubuntu
  -VM reiniciada: sudo reboot
  -Acesso ao diretório na VM que referencia a pasta criada na máquina física: ls /media
   -Foi utilizado um comando para imprimir/gravar uma mensagem em um novo arquivo: QUAL O COMANDO PARA IMPRIMIR A MENSAGEM? COMO FOI CRIADO O ARQUIVO COM MENSAGEM? 

  -Testamos na máquina física se o novo arquivo criado estava lá
   -Criamos na máquina física um segundo arquivo

-Novamente na VM:
 -Utilizando um comando de leitura: qual? vim ~/.vimrc
 -Utilizamos um aplicativo de editor de texto instalado por padrão no Ubuntu para abrir o arquivo e editá-lo: qual comando? nano nome_do_arquivo
 -Baixamos um segundo aplicativo de editor de texto/código: com qual comando instalamos? 

 ---

 
