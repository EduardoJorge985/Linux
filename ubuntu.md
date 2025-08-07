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
