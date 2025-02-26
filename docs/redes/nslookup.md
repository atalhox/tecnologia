# Comando nslookup

## 1. Introdução
O **nslookup** (“Name Server Lookup”) é uma ferramenta utilizada para interagir com servidores DNS e realizar consultas sobre domínios, endereços IP e outros registros DNS.

Este comando está disponível em sistemas Windows, Linux e macOS, sendo amplamente utilizado para testes e diagnósticos de problemas de resolução de nomes na rede.

## 2. Objetivo
O objetivo principal do **nslookup** é permitir que administradores de sistemas e redes consultem informações sobre servidores DNS e domínios, facilitando o diagnóstico de problemas de conectividade e configuração.

## 3. Público-Alvo
Esta documentação destina-se a:
- Administradores de redes
- Engenheiros de sistemas
- Profissionais de segurança da informação
- Desenvolvedores e DevOps
- Estudantes e entusiastas de tecnologia

## 4. Conteúdo
### 4.1. Sintaxe Básica
A sintaxe do **nslookup** segue o seguinte formato:

```sh
nslookup [opções] [domínio/endereço IP]
```

Exemplo:
```sh
nslookup exemplo.com
```

Isso retorna informações sobre o servidor DNS que respondeu à consulta e o endereço IP do domínio.

### 4.2. Modo Interativo
O **nslookup** pode ser executado em modo interativo, permitindo várias consultas sem sair do comando:
```sh
nslookup
> exemplo.com
> set type=MX
> google.com
> exit
```
Neste modo, pode-se alterar parâmetros e realizar consultas sucessivas sem precisar reiniciar o comando.

### 4.3. Tipos de Registros DNS
O **nslookup** permite consultar diferentes tipos de registros DNS utilizando a opção `set type`:

| Comando          | Descrição                            |
| ---------------- | ------------------------------------ |
| `set type=A`     | Endereço IPv4 do domínio             |
| `set type=AAAA`  | Endereço IPv6 do domínio             |
| `set type=MX`    | Registros de e-mail (Mail Exchange)  |
| `set type=NS`    | Servidores de nome do domínio        |
| `set type=CNAME` | Nome canônico (alias) do domínio     |
| `set type=PTR`   | Consulta reversa de IP para nome     |
| `set type=SOA`   | Informações de autoridade do domínio |
| `set type=TXT`   | Registros de texto (SPF, DKIM, etc.) |

### 4.4. Consultas a um Servidor DNS Específico
Para consultar um servidor DNS específico, utilize a seguinte sintaxe:
```sh
nslookup exemplo.com 8.8.8.8
```
Isso consulta o domínio `exemplo.com` usando o servidor DNS do Google (`8.8.8.8`).

### 4.5. Consulta Reversa (PTR)
Para descobrir o domínio associado a um endereço IP:
```sh
nslookup 8.8.8.8
```
Isso retorna o nome do domínio associado ao IP informado, caso exista um registro PTR configurado.

## 5. Guia de Uso
### 5.1. Diagnóstico de Problemas DNS
Se um domínio não estiver resolvendo corretamente, pode-se testar diferentes servidores DNS:
```sh
nslookup exemplo.com 1.1.1.1
```
Se um servidor DNS retorna informações corretas e outro não, pode haver um problema de propagação DNS.

### 5.2. Verificação de Registros MX (E-mail)
Para verificar os servidores de e-mail de um domínio:
```sh
nslookup -type=MX exemplo.com
```
Isso lista os servidores responsáveis por receber e-mails para o domínio.

### 5.3. Obtenção de Servidores Autoritativos
Para descobrir os servidores DNS autoritativos de um domínio:
```sh
nslookup -type=NS exemplo.com
```

### 5.4. Consulta de Registros TXT
Para verificar registros TXT (SPF, DKIM, etc.), execute:
```sh
nslookup -type=TXT exemplo.com
```
Isso é útil para verificar políticas de segurança de e-mail.

## 6. Referências
- [Documentação Oficial Microsoft](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup)
- [RFC 1034 - Domain Concepts and Facilities](https://tools.ietf.org/html/rfc1034)
- [RFC 1035 - DNS Implementation and Specification](https://tools.ietf.org/html/rfc1035)

## 7. Anexos
Nenhum anexo adicional foi incluído nesta documentação.

