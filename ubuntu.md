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

- Criação de uma nova pasta na máquina física (host):  
  Caminho: `C:\VirtualBox-PastaCompartilhada`

- Configuração da VM (guest):  
  - Acesse a guia denominada **Pasta Compartilhada** nas configurações da VM.  
  - Crie uma referência para a pasta física com o caminho `C:\VirtualBox-PastaCompartilhada` para que a VM possa acessá-la.

- Após ligar a VM:  
  - Adicione o usuário atual ao grupo `vboxsf` para permitir acesso à pasta compartilhada, com o comando:  
    `sudo usermod -aG vboxsf $USER`  
  - Reinicie a VM para aplicar as mudanças:  
    `sudo reboot`  
  - Acesse o diretório na VM que referencia a pasta criada na máquina física (normalmente em `/media/sf_VirtualBox-PastaCompartilhada` ou `/media`):  
    `ls /media`  
  - Para imprimir/gravar uma mensagem em um novo arquivo dentro da pasta compartilhada, utilize o comando:  
    `echo "Sua mensagem aqui" > /media/sf_VirtualBox-PastaCompartilhada/arquivo.txt`  
    Esse comando cria um arquivo chamado `arquivo.txt` com o conteúdo especificado.

- Testamos na máquina física se o novo arquivo criado pela VM está presente na pasta compartilhada.  
- Criamos na máquina física um segundo arquivo dentro da pasta compartilhada.

- Novamente na VM:  
  - Para leitura simples de arquivos, um comando comum é:  
    `cat /media/sf_VirtualBox-PastaCompartilhada/nome_do_arquivo`  
  - Para abrir e editar um arquivo usando o editor de texto padrão do Ubuntu, use:  
    `nano nome_do_arquivo`  
  - Para instalar um segundo editor de texto/código, como o Vim, utilize os comandos:  
    `sudo apt update`  
    `sudo apt install vim`
 
