# Sessão 1: Reconhecimento e Enumeração de Portas com Nmap

Este documento regista as atividades de auditoria de segurança e enumeração de serviços realizadas no servidor alvo utilizando o Nmap, além de documentar a configuração de rede local.

---

##  1. Resultados da Varredura Nmap (Alvo: `10.129.168.208`)

A varredura foi realizada utilizando os parâmetros de detecção de serviço e scripts padrão (`nmap -sV -sC 10.129.168.208`).

### Resumo Técnico:
* **Número de portas abertas identificadas:** 5 portas tcp abertas.
* **Sistema Operacional do Alvo:** Microsoft Windows (Windows Server, provável build `10.0.17763`).

### Tabela de Portas e Serviços Detetados:

| Porta | Estado | Serviço | Versão Exata Detetada | Detalhes Adicionais / Configurações |
| :--- | :--- | :--- | :--- | :--- |
| **21/tcp** | Aberta | FTP | FileZilla ftpd | Login anônimo habilitado (`Anonymous FTP login allowed`). |
| **53/tcp** | Aberta | DNS | Simple DNS Plus | Servidor de DNS ativo. |
| **80/tcp** | Aberta | HTTP | Microsoft IIS httpd 10.0 | Servidor Web IIS padrão ativo. |
| **135/tcp** | Aberta | MSRPC | Microsoft Windows RPC | Serviço RPC de comunicação do Windows. |
| **3389/tcp**| Aberta | RDP | Microsoft Terminal Services | Área de Trabalho Remota ativa (Nome do Host: `WIN-SCAN`). |

---

## 2. Configuração e Estado do Ambiente Local

Para fins de auditoria interna, seguem as informações de rede locais extraídas da máquina de ataque.

###  Output do comando `ip a` (Interfaces de Rede)
```text
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP group default qlen 1000
    link/ether 0a:aa:62:14:0f:3b brd ff:ff:ff:ff:ff:ff
    inet 10.129.181.143/16 brd 10.129.255.255 scope global dynamic eth0
       valid_lft 3215sec preferred_lft 3215sec
    inet6 fe80::8aa:62ff:fe14:f3b/64 scope link 
       valid_lft forever preferred_lft forever
```text
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 ...
...
inet6 fe80::8aa:62ff:fe14:f3b/64 scope link
```

![image alt](https://github.com/evacatarina/sessao---01/blob/cca61dbf4f8dcb18d4c37950a1ce1556d7f806bc/Captura%20de%20ecr%C3%A3%202026-07-14%20205232.png)

![image alt](https://github.com/evacatarina/sessao---01/blob/70e8b066abb03da7c135f28477e5752c51597184/Captura%20de%20ecr%C3%A3%202026-07-14%20205458.png)

![image alt](https://github.com/evacatarina/sessao---01/blob/70e8b066abb03da7c135f28477e5752c51597184/Captura%20de%20ecr%C3%A3%202026-07-14%20205546.png)
