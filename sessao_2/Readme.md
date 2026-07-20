# Laboratório — Sessão 2
## Auditoria de Sistemas Linux e Análise Avançada de Logs
---
### Passo 1

**Exercício 1** - No lab Linux Server Forensics, navegar até à diretoria de logs do servidor
comprometido.    

Utilizei o comando `cd /var/log/`.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/e1e27017bf1fa1c912b616db826e2df12f8110a9/sessao_2/Captura%20de%20ecr%C3%A3%202026-07-19%20190219.png)

---

### Passo 2

**Exercício 2** - Isolar tentativas falhadas de login.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/e2ae9c667a08b0b5f3cb83bba3e4401e8645c7cb/sessao_2/Captura%20de%20ecr%C3%A3%202026-07-19%20191511.png)

---

### Passo 3

**Exercício 3** - Extrair e contar quais os IPs que mais tentaram autenticar-se no sistema.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/1c974429f057e9993f878150cabce9ed8419e988/sessao_2/Captura%20de%20ecr%C3%A3%202026-07-19%20191736.png)

---

### Passo 4

**Exercício 4** - Identificar se o atacante obteve sucesso.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/794ba13a3e30b51143444fd891404eaf8021cf09/sessao_2/Captura%20de%20ecr%C3%A3%202026-07-19%20191900.png)

---
Pode verificar na imagem do Passo 2:  
O IP do atacante identificado - 10.129.131.96  
A hora exata do comprometimento (timestamp) - 2026.07.19 T 20:07:23     
O utilizador afetado - ubuntu  
Breve linha temporal do ataque (tentativas falhadas → sucesso) - como tive apenas 1 tentativa, por falha do simulador, como constado na imagem.


