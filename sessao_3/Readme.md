# Laboratório — Sessão 3
## Hardening de Redes Linux e Configuração de Firewalls
---
### Passo 1
Utilizei o comando 'sudo ufw status' para verificar o estado da firewall.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/c84d83c7200a4246bfa794de1ababa4037bab947/sessao_3/estado%20atual.png).

### Passo 2
Usei configuração padrão de segurança, bloqueandopor padrão as de entradas e permitindo apenas as requisições de saída.
*Alterei as políticas padrão — bloquear entrada com o comando ´sudo ufw default deny incoming´ e permitir saída com o comando ´sudo ufw default allow outcoming´.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/80b30589113f62c773fdf53fba081e21f18f7910/sessao_3/politicas%20padrao.png)
