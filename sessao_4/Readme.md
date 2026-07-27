# Laboratório — Sessão 4
## Gestão Segura de Acessos Remotos SSH em Linux
### Contexto  
Proteger o canal de gestão remota de um servidor Ubuntu, eliminando a autenticação tradicional por palavra-passe e migrando para autenticação criptográfica via chave Ed25519, além de alterar a porta padrão do serviço SSH.

---

### Passo 1

**Exercício 1** - Criar um novo utilizador de teste no sistema e configurar o ambiente para aceitar chaves.    

Para realizar este exercício utilizei comandos como: `sudo adduser aluno` para criar novo utilizador "aluno" no servido, `sudo usermod -aG sudo aluno` adicionar o utilizador ao grupo sudo e para garantir a criação e permissões corretas do diretório .ssh no servidor os comandos: `sudo su - aluno`, `mkdir -p ~/.ssh`, `chmod 700 ~/.ssh`, `touch ~/.ssh/authorized_keys` e `chmod 600 ~/.ssh/authorized_keys`. 

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/6026718e013c5ba2b39e58718bdebeecbe0d4c2f/sessao_4/add%20user.jpeg)

---

### Passo 2

**Exercício 2** - Gerar um par de chaves Ed25519 robustas.  

No sistema cliente, foi gerado um par de chaves assimétricas utilizando o algoritmo Ed25519.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/0e6f7f150e28234cf8d72927f435a0b0f9b63440/sessao_4/fase%202.jpeg)

---

### Passo 3

**Exercício 3** - Transferir a chave pública para o servidor alvo.  

A chave pública foi copiada para o utilizador no servidor alvo para permitir a autenticação criptográfica.  

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/78459fda92774920372b0e44819e7b965476b8d2/sessao_4/fase%203.jpeg)

---

### Passo 4

**Exercício 4** - Editar o ficheiro de configuração do daemon SSH com privilégios de superutilizador.  

Foi aplicado as seguintes alterações:
- PermitRootLogin no;  
- PasswordAuthentication no;  
- Port 2222.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/647aeefaa0a8192eba5b1b465a6d4887a66fa0a9/sessao_4/fase%204.jpeg)  

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/f06ac8e5874b97f71fe770f5c5ee4318b677a7ae/sessao_4/fase%204.1.jpeg)

---

### Passo 5

**Exercício 5** - Validar a sintaxe das alterações antes de reiniciar o serviço.  

Antes de reiniciar o serviço, foi executada a verificação de sintaxe para garantir que não existiam erros no ficheiro de configuração.  

![image alt]()

---

### Passo 6

**Exercício 6** - Reiniciar o serviço SSH.  

Após a confirmação sem erros de sintaxe, o serviço SSH foi reiniciado.  

![image alt]()

---

### Passo 7

**Exercício 7** - Num novo terminal, testar o acesso via chave privada e nova porta.  

Num novo terminal (mantendo a sessão original aberta por segurança), foi testado o acesso utilizando a chave privada e a nova porta configurada.  

![image alt]()


