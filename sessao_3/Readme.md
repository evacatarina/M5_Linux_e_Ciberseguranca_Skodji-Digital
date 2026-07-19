# Laboratório — Sessão 3
## Hardening de Redes Linux e Configuração de Firewalls
---
### Passo 1

**Exercício 1** - Verificar o`status atual`do UFW.    

Utilizei o comando `sudo ufw status` para verificar o estado da firewall.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/c84d83c7200a4246bfa794de1ababa4037bab947/sessao_3/estado%20atual.png).

### Passo 2

**Exercício 2** - Alterar as políticas padrão: bloquear entrada, permitir saída.  

Usei configuração padrão de segurança, bloqueando por padrão as de entradas e permitindo apenas as requisições de saída.  
Alterei as políticas padrão — bloquear entrada com o comando `sudo ufw default deny incoming` e permitir saída com o comando `sudo ufw default allow outcoming`.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/80b30589113f62c773fdf53fba081e21f18f7910/sessao_3/politicas%20padrao.png)

### Passo 3 
**Exercício 3** - Criar uma regra específica para permitir acesso SSH apenas na porta padrão.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/d9e06edd0f62477d2cd763186942ea758222536d/sessao_3/porta%20padrao.png)

### Passo 4
**Exercício 4** - Simular o bloqueio de um IP malicioso fictício na chain INPUT do iptables.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/a0fe9d6f9e7a7c63a156e4a90edc8f0158d302e7/sessao_3/simulacao%20bloqueio.png)

Para verificar o bloqueio, executei o comando abaixo em que teve esta saída.  
Em que o IP malicioso `203.0.113.50` foi bloqueado e ignorado silenciosamente pelo comando `DROP` assim o firewall está blindado contra este endereço. Se o IP fictício estivesse tentando enviar pacotes, a coluna pkts (pacotes) começaria a aumentar.  

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/523010f2609895129543e781ef595265374b88de/sessao_3/conf%20simulacao.png).

### Passo 5 
**Exercício 5** - Guardar o estado persistente do iptables.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/00ddf7a8e26efeb0196ac5b2ba9822884f361d76/sessao_3/iptables%20save.png)

Para finalizar também foi solicitado os outputs dos comandos:  
-`ufw status verbose`:  

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/4501b0a2193d2047a7d80c9494252d2e77f1d187/sessao_3/status%20verbose.png)

-`iptables -L -v`:

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/f6c092d703058baccc5eba51400f3602b4fb1439/sessao_3/iptables%20L%20V.png)

### Explicação da Política de Segurança Aplicada
A política de segurança implementada baseia-se no princípio do privilégio mínimo e na estratégia de defesa em profundidade, combinando a simplicidade do UFW (Uncomplicated Firewall) com o controlo granular do iptables.

Abaixo detalha-se o que está bloqueado, o que está permitido e as respetivas justificações técnicas:

## Tráfego de Entrada (Incoming): Bloqueado por Padrão
O que foi feito: Configuração da política padrão para rejeitar conexões de entrada (sudo ufw default deny incoming).

Porquê: Esta é a regra de ouro da segurança de redes. Ao bloquear todo o tráfego de entrada por omissão, blindamos o sistema contra varreduras de portas (port scanning) e tentativas de ligação não autorizadas a serviços internos que possam estar vulneráveis ou mal configurados.

## Tráfego de Saída (Outgoing): Permitido por Padrão
O que foi feito: Configuração da política padrão para permitir conexões de saída (sudo ufw default allow outgoing).

Porquê: Garante que o próprio servidor e os seus utilizadores legítimos possam comunicar com o exterior sem restrições imediatas (para atualizações de sistema, consultas de DNS, navegação web, etc.), mantendo a operacionalidade do sistema.

## Acesso SSH (Porta Padrão): Exceção Permitida
O que foi feito: Criação de uma regra específica para abrir a porta padrão do SSH (geralmente a porta 22/tcp).

Porquê: Como o tráfego de entrada está todo bloqueado, foi necessário abrir uma exceção controlada para que os administradores não perdessem o acesso remoto ao servidor. O SSH é a única "porta de entrada" legítima mantida aberta nesta fase.

## Bloqueio Direto de IP Malicioso (iptables): Filtragem Alvo
O que foi feito: Adição de uma regra na chain INPUT do iptables para barrar especificamente o IP fictício 203.0.113.50 usando a ação DROP.

O que significa o DROP: Ao contrário da ação REJECT (que avisa o remetente de que a ligação foi recusada), o DROP descarta o pacote de forma completamente silenciosa. O atacante fica sem saber se o servidor está online ou se há uma firewall a protegê-lo, o que atrasa a análise do invasor e consome os seus recursos computacionais.
