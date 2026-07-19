# Laboratório — Sessão 3
## Hardening de Redes Linux e Configuração de Firewalls
---
### Passo 1

**Exercício 1** - Verificar o ´status´atual do UFW.    

Utilizei o comando 'sudo ufw status' para verificar o estado da firewall.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/c84d83c7200a4246bfa794de1ababa4037bab947/sessao_3/estado%20atual.png).

### Passo 2

**Exercício 2** - Alterar as políticas padrão: bloquear entrada, permitir saída.  

Usei configuração padrão de segurança, bloqueando por padrão as de entradas e permitindo apenas as requisições de saída.  
Alterei as políticas padrão — bloquear entrada com o comando ´sudo ufw default deny incoming´ e permitir saída com o comando ´sudo ufw default allow outcoming´.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/80b30589113f62c773fdf53fba081e21f18f7910/sessao_3/politicas%20padrao.png)

### Passo 3 
**Exercício 3** - Criar uma regra específica para permitir acesso SSH apenas na porta padrão.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/d9e06edd0f62477d2cd763186942ea758222536d/sessao_3/porta%20padrao.png)

### Passo 4
**Exercício 4** - Simular o bloqueio de um IP malicioso fictício na chain INPUT do iptables.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/a0fe9d6f9e7a7c63a156e4a90edc8f0158d302e7/sessao_3/simulacao%20bloqueio.png)

Para verificar o bloqueio, executei o comando abaixo em que teve esta saída.  
Em que o IP malicioso ´203.0.113.50´ foi bloqueado e ignorado silenciosamente pelo comando ´DROP´, assim o firewall está blindado contra este endereço. Se o IP fictício estivesse tentando enviar pacotes, a coluna pkts (pacotes) começaria a aumentar.  

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/523010f2609895129543e781ef595265374b88de/sessao_3/conf%20simulacao.png).

### Passo 5 
**Exercício 5** - Guardar o estado persistente do iptables.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/00ddf7a8e26efeb0196ac5b2ba9822884f361d76/sessao_3/iptables%20save.png)

Para finalizar também foi solicitado os outputs dos comandos ´ufw status verbose´ e ´iptables -L -v´.
