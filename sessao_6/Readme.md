# Laboratório — Sessão 6
## Desafio Prático Integrador — Mini-CTF Defensivo Linux
### Contexto  
Auditoria e enrijecimento do servidor Ubuntu ("Linux Agency")

---

## Fase 1: Identificação e Triagem

### 1.1 Análise de Rede e Portas: identificar quais os portos e serviços ativos que estão expostos desnecessariamente

Para verificar os serviços e portas ativos no sistema, foram executados os comandos `ss` e `nmap`:

- `ss`: ss-tuln  
![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/8bb2a8178e380388c5e655e6c6d0958302c573a2/sessao_6/ss%20tuln.png).

Com o output desse comando foi possível analisar as Portas e Serviços:  
Portas expostas externamente (0.0.0.0):  
Porta 22/tcp (SSH) — Ativa para gestão remota;  
Porta 80/tcp (HTTP) — Servidor Web ativo na rede.
Serviços locais (Loopback 127.0.0.1):  
Porta 5901/tcp (VNC) e 631/tcp (CUPS Printer) a rodar localmente.  
Como recomendação, é necessário que a firewall UFW deva garantir o bloqueio de tráfego de entrada em todas as portas não essenciais (como a porta 80, se o objetivo for manter apenas acesso administrativo por SSH na porta 22).  


- `nmap`   
Foi digitado o comando `nmap-sV localhost` mas o output diz que não há conexão a internet, por isso não foi possível a execução do comando. Na 2ª imagem, é possível visualizar que houve uma tentativa de instalar o `nmap` mas sem sucesso.  

  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/99e5b6f5bb4f226c096b5eae295c59e24c467e3b/sessao_6/nmap%201.png)

  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/b4a0420671503959941951e08ffd0354174bd512/sessao_6/nmap%202.png)
  

 ### 1.2 Auditoria de Contas: procurar por utilizadores com permissões excessivas, contas sem palavra-passe associada ou chaves públicas suspeitas em `authorized_keys`  

 Foi realizada a auditoria de contas do sistema para identificar privilégios excessivos, contas sem palavra-passe e chaves SSH não autorizadas, com os comandos `sudo cat /etc/shadow | awk -F: '($2==""){print $1}'` e `cat ~/.ssh/authorized_keys` (respetivamente):  

  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/332efbbcf0b59039f77bb6e1a9ad49b596869f5a/sessao_6/fase%201.2.png)  

  Para o comando `sudo cat /etc/shadow | awk -F: '($2==""){print $1}`que verifica contas sem palavra-passe: nenhum utilizador sem password foi identificado.  
  Para o comando `cat ~/.ssh/authorized_keys` que mostra as chaves SSH Autorizadas: foram identificadas 4 chaves públicas ativas (`amiOpenVPN`, `cmnatic`, `saqib.shabbir` e `eu-west-3-vuln-vms`). É recomendado a revisão e remoção de chaves não reconhecidas para impedir acessos remotos não autorizados.  

  ---

 ## Fase 2: Contenção

### Ativar a firewall UFW, bloqueando todas as portas que não sejam estritamente necessárias para o negócio

Para a realização dessa fase, foram usadas os seguintes comandos: `sudo ufw default deny incoming`, `sudo ufw allow 22/tcp` e `sudo ufw enable`.

 ![image alt]()  
 

 

