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
  ![image alt]()

- Suggestions (Sugestões): Recomendações de boas práticas para aumentar a proteção do sistema.
  ![image alt]()



