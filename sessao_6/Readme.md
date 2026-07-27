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

- `nmap`   
Foi digitado o comando `nmap-sV localhost` mas o output diz que não há conexão a internet, por isso não foi possível a execução do comando. 

  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/99e5b6f5bb4f226c096b5eae295c59e24c467e3b/sessao_6/nmap%201.png)

 ### 1.2 Auditoria de Contas: procurar por utilizadores com permissões excessivas, contas sem palavra-passe associada ou chaves públicas suspeitas em `authorized_keys`  

 Foi realizada a auditoria de contas do sistema para identificar privilégios excessivos, contas sem palavra-passe e chaves SSH não autorizadas, com os comandos `sudo cat /etc/shadow | awk -F: '($2==""){print $1}'` e `cat ~/.ssh/authorized_keys` (respetivamente):  

  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/332efbbcf0b59039f77bb6e1a9ad49b596869f5a/sessao_6/fase%201.2.png)
 

 

