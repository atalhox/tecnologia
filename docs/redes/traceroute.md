# Traceroute

## 1. Introdução
O comando `traceroute` é uma ferramenta de diagnóstico de rede utilizada para mapear o caminho percorrido pelos pacotes até um destino específico. Ele auxilia na identificação de latências, roteadores intermediários e possíveis problemas de conectividade.

## 2. Objetivo
Esta documentação detalha o funcionamento, opções e exemplos práticos do comando `traceroute`, auxiliando administradores de redes e entusiastas em sua utilização.

## 3. Público-Alvo
- Administradores de redes
- Engenheiros de sistemas
- Profissionais de segurança da informação
- Estudantes de TI

## 4. Funcionamento
O `traceroute` envia pacotes ICMP ou UDP com valores de **TTL (Time To Live) incrementais** para descobrir cada salto até o destino final. Quando o TTL expira, o roteador intermediário retorna uma mensagem ICMP `Time Exceeded`, permitindo a identificação do caminho percorrido.

!!! tip "Dica"
    Para sistemas baseados em Windows, o equivalente ao `traceroute` é o comando `tracert`, que utiliza apenas pacotes ICMP.

## 5. Uso Básico
A sintaxe padrão do comando é:

```sh
traceroute <destino>
```

Exemplo:
```sh
traceroute google.com
```
Isso exibirá a lista de saltos até o servidor do Google.

!!! warning "Atenção"
    Algumas redes bloqueiam pacotes ICMP e UDP para evitar análise de rotas. Caso não obtenha resposta, tente utilizar outras opções de protocolo.

## 6. Opções Principais
| Opção    | Descrição                                           |
| -------- | --------------------------------------------------- |
| `-n`     | Exibe os endereços IP sem resolver os nomes de host |
| `-I`     | Usa pacotes ICMP Echo Request em vez de UDP         |
| `-T`     | Utiliza pacotes TCP SYN em vez de UDP               |
| `-m <n>` | Define o TTL máximo dos pacotes                     |
| `-q <n>` | Define o número de pacotes enviados por salto       |
| `-w <n>` | Define o tempo de espera por resposta (em segundos) |

!!! tip "Dica"
    Se você deseja identificar bloqueios de firewall, experimente a opção `-T` para usar TCP, pois ele é menos bloqueado do que UDP ou ICMP em algumas redes.

## 7. Exemplos Avançados
- **Executando `traceroute` sem resolver nomes de host:**

```sh
traceroute -n google.com
```
  Isso acelera a execução ao evitar consultas DNS.

- **Utilizando pacotes ICMP em vez de UDP:**

```sh
traceroute -I google.com
```

Útil quando UDP é bloqueado por firewall.

- **Ajustando o tempo de resposta para cada salto:**

```sh
traceroute -w 2 google.com
```

Define um tempo de espera menor para respostas, reduzindo atrasos.

!!! warning "Atenção"
    O uso de traceroute em redes empresariais pode acionar sistemas de detecção de intrusão (IDS). Sempre verifique a política da empresa antes de utilizar essa ferramenta.

## 8. Referencias

- Documentação Oficial do traceroute
- RFC 1393 - Traceroute Using an IP Option