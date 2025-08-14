# Documentação Linux Ubuntu 24.04

**Obs:** *Comando* `sudo` *concede privilégio de administrador*  
**apt**: *gerenciador de pacotes*

---

## Comandos:

- **`sudo apt update`**  
- **`sudo apt upgrade`**  
- **`sudo reboot`**  
- **`sudo apt install build-essential dkms linux-headers-$(uname -r)`**  
  Instala:  
  - **build-essential**: ferramenta para compilar código-fonte  
  - **dkms**: recompilador de aplicações para compatibilidade com o Kernel do convidado *(guest)*

- **`cd /media/$USER/VBox_GAs_7.0.6`**  
  Caminha até o diretório onde está o aplicativo para instalar recursos adicionais de convidado  
  `$USER` é uma variável de ambiente que referencia o nome do usuário logado

- **`sudo ./VBoxLinuxAdditions.run`**  
  Executa a aplicação disponível no diretório acessado e instala os recursos adicionais

- **`lsmod | grep vbox`**  
  - **lsmod**: lista os módulos carregados no Kernel  
  - **grep**: filtra e exibe apenas as linhas que contenham o texto desejado *(vbox, neste caso)*  
  - **vbox**: prefixo comum dos nomes dos módulos do VirtualBox

---

Criação de uma nova pasta na máquina física *(host)* no caminho `C:\VirtualBox-PastaCompartilhada`.  

Na configuração da VM *(guest)*, acesse a guia **Pasta Compartilhada** e crie uma referência para a pasta física com o mesmo caminho para que a VM possa acessá-la.  

Após ligar a VM, adicione o usuário atual ao grupo `vboxsf` com:  
`sudo usermod -aG vboxsf $USER`  
Reinicie a VM com:  
`sudo reboot`  

Acesse o diretório na VM que referencia a pasta criada na máquina física (ex.: `/media/sf_VirtualBox-PastaCompartilhada` ou `/media`) com:  
`ls /media`  

Para criar um arquivo na pasta compartilhada:  
`echo "Sua mensagem aqui" > /media/sf_VirtualBox-PastaCompartilhada/arquivo.txt`  

Teste na máquina física se o arquivo criado pela VM está presente e crie também um segundo arquivo na pasta compartilhada.  

Na VM, para leitura simples:  
`cat /media/sf_VirtualBox-PastaCompartilhada/nome_do_arquivo`  

Para editar com o editor padrão:  
`nano nome_do_arquivo`  

Para instalar o Vim:  
`sudo apt update`  
`sudo apt install vim`

---
 

**`cd /media/sf_VirtualBox-PastaCompartilhada/`** – Entra na **PastaCompartilhada**  

---

**`ls`** – lista a pasta  

---

**`ls -l`** – abre colunas mostrando a última modificação do arquivo (hora, data, etc.) e o grupo que pode acessar  

---

**`rwx`** (*read, write, execute*):  
- permissões para **leitura**  
- permissões para **gravar**  
- permissões para **executar**  

---

**`chmod`** – altera permissões  
**`chown`** – mudar o proprietário  

---

**`groups`** – mostra os grupos do usuário  

---

**`sudo groupadd grupo`** – adiciona grupo  
**`sudo adduser $USER grupo`** – adiciona o usuário ao grupo  
OU  
**`sudo usermod -aG usuario grupo`**  

**`sudo usermod -aG nome_do_usuario nome_do_grupo`**  
**`sudo usermod -aG nome_do_grupo $USER`**  
> **Obs:** `-aG` adiciona o usuário a um grupo sem removê-lo de outro  

**`mkdir`** – cria um novo diretório  

Para mudar o grupo proprietário de um diretório:  
**`sudo chown :nome_do_grupo nome_da_pasta`**  

---


# SO Linux Ubuntu – Comandos de permissão

**Usuários:**  
- **root** (administrador)  

**Grupos:**  
- **sudo** (*super user do*)  

---

Para verificar **todos os grupos existentes**:  
**`cat /etc/group`**  

Para verificar **somente os grupos dos quais o usuário logado faz parte**:  
**`groups`**  

Para criar um novo grupo:  
**`sudo groupadd nome`**  

Para anexar um usuário a um grupo:  
**`sudo usermod -aG nome_do_grupo nome_do_usuario`**  

**Exemplo:** usuário deseja instalar o aplicativo “vim”  
Digite o comando:  
**`sudo apt install vim`**  
Será exigida a senha para verificar se o usuário faz parte do grupo `sudo`.  

---

## CHMOD
- 1º bloco: define as permissões do **usuário proprietário**  
- 2º bloco: define as permissões do **grupo proprietário**  
- 3º bloco: define as permissões de **outros** (isto é, não pertencem ao grupo nem são o dono)
