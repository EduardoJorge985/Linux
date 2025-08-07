                                                        Documentação Linux Ubuntu 24.04 

Obs: Comando sudo concede privilegio de administrador
             apt: gerenciador de pacotes

- sudo apt update
- sudo apt upgrade
- sudo reboot
- sudo apt install build-essential dkms linux-headers-$(uname -r)
  Instala: build-essencial: ferramenta para compilar código-fonte 
           dkms: recompilador de aplicações para compatibilidade com Kernel do convidado (guest)
- cd /media/$USER/VBox_GAs_7.0.6
          Caminha até o diretório onde está o aplicativo para instalar recursos adicionais de convidado
          $USER é uma variável de ambiente que referencia o valor do usuário que está logado (nome de usuário)
- sudo ./VBoxLinuxAdditions.run
        Executa a aplicação disponível no diretório que acessou e instala os recursos
- lsmod grep vbox
       lsmod: Listar módulos carregados no Kernel
       grep: funciona como  um filtro para pesquisar apenas as linhas que contenham o texto que deseja pesquisar (nesse caso, vbox) 
       vbox: prefixo que inicia normalmente os nomes dos módulos do VirtualBox
