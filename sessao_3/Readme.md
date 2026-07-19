# Laboratório — Sessão 3
## Hardening de Redes Linux e Configuração de Firewalls
---
### Passo 1
Utilizei o comando 'sudo ufw status' para verificar o estado da firewall.
```text
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 ...
...
inet6 fe80::8aa:62ff:fe14:f3b/64 scope link
```
![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/c84d83c7200a4246bfa794de1ababa4037bab947/sessao_3/estado%20atual.png).

### Passo 2
( colocar o print)
Alterarei as políticas padrão — bloquear entrada com o comando ´sudo ufw default deny incoming´ e permitir saída com o comando ´sudo ufw default allow outcoming´.
