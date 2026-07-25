# Laboratório — Sessão 5
## Análise de Vulnerabilidades em Linux e Ferramentas de Auditoria
### Contexto  
Execução de um exame de auditoria técnica automatizada para identificar desvios de conformidade em relação aos standards de segurança recomendados (CIS Benchmarks).  
O Ambiente Virtual utilizado foi o KillerCoda Ubuntu Playground.

---

### Passo 1

**Exercício 1** - Atualizar a árvore de pacotes e instalar o Lynis.    

Para realizar este exercício utilizei o comando `sudo apt update && sudo apt install lynis -y`.

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/5457b67ddcd491e719927d8945e4fe06c8eeceda/sessao_5/update%20install%20lynis.png).

---

### Passo 2

**Exercício 2** - Iniciar a auditoria completa do sistema operativo.  

Quando você executa o comando `sudo lynis audit system`, o Lynis realiza uma auditoria completa de segurança e conformidade diretamente no seu sistema operacional.   
![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/969aebfe6fa1c140d0f9db760b72d8cf68974715/sessao_5/lynis%20audit.png)

---

Após executar o comando `sudo lynis audit system`, é necessário aguardar a conclusão do processo e analisar minuciosamente o output exibido no terminal.  

Ao término do escaneamento, a ferramenta apresenta no terminal:  
- Hardening Index: A sua pontuação global de segurança (de 0 a 100);
  
  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/2b1b7cefa1993e200b4f0d9a5d760305d6a7ea3b/sessao_5/lynis%20details.png)

- Warnings (Alertas): Problemas de segurança críticos que exigem atenção imediata;
  
  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/649c699d3f12b894a84326ed7d2832cab595336c/sessao_5/warnings.png)

- Suggestions (Sugestões): Recomendações de boas práticas para aumentar a proteção do sistema.
  
  ![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/deac87ac83bbb13bbcd9b1a665ce4d49abd895f1/sessao_5/suggestions.png)

---

Como critério de entrega:
- Foi requisitado a escolha 2 Suggestions críticas apresentadas na área de Authentication ou Filesystem e pesquisar a correção recomendada (base de dados Cisofy).
  Abaixo Suggestion 1 e a devida correção:

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/628c524692671cdb467dfbb699ad68b771c4dacf/sessao_5/sugg%201.png)  
```
# How to solve
Install a tool like AIDE to help monitoring file changes. Good
monitoring will ensure that both authorized changes are properly
documented, and unauthorized changes are detected early.

Tip: when possible, link events to a (security) monitoring system, or
your ITIL problem management. Especially unauthorized changes
need a root cause analysis, or trigger incident response.
```

  Abaixo Suggestion 2 e a devida correção:

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/de8e6e60862e60f67b2ecfa3b7b126cf42006707/sessao_5/sugg%202.png)  
```
# How to solve
Passwords are a key component to authenticate users to Linux
systems. Passwords need to be of a good quality, to prevent so-
called brute-forcing attacks. In such case, easy passwords can be
quickly guessed, resulting in a possible intrusion. The strength of
passwords is determined by the length and variety of characters,
including capitals, numbers, and special characters.
Besides the strength, it is good to use password aging. This means a
password can only be used for a specific duration of time before the
user has to change it again. This enforces them to change it on a
regular basis, having hopefully a bigger variety in passwords used
on the system and other services.
Password aging is not always needed on the Linux system itself. For
example, when using two-factor authentication, central
authentication with LDAP or Radius.
For Lynis Enterprise users we have additional tests regarding
authentication and passwords. Consider upgrading if password
strength and aging are important aspects for your environment.
```

- Incluir excerto do relatório Lynis ( /var/log/lynis-report.dat ou output do terminal).

![image alt](https://github.com/evacatarina/M5_Linux_e_Ciberseguranca_Skodji-Digital/blob/27aa7a7171bad474bb0e18d53dc08fd8a351944e/lynus%20security%20scan%20details.png) 


