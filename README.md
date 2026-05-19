
# 🛡️ CyberSec Notes: Fundamentos de Redes

## 1. O Modelo OSI (Open Systems Interconnection)
O **Modelo OSI** é um modelo conceitual criado para padronizar a comunicação entre diferentes sistemas de computadores. Ele funciona como um "manual de instruções" universal, permitindo que dispositivos de fabricantes diferentes (Apple, Dell, Linux) "conversem" entre si.

O modelo é dividido em **7 camadas**. 
- **Envio:** O dado desce do nível 7 para o 1.
- **Recebimento:** O dado sobe do nível 1 para o 7.

### Detalhamento das Camadas

#### 7. Camada de Aplicação (*Application*)
Interage diretamente com o usuário final. Fornece a interface para que softwares acessem a rede.
- **O que faz:** Identifica parceiros de comunicação e sincroniza a comunicação.
- **Protocolos:** `HTTP` (Web), `FTP` (Arquivos), `SMTP` (E-mail), `DNS`.
- **Analogia:** A pessoa escrevendo a carta.

#### 6. Camada de Apresentação (*Presentation*)
Atua como um "tradutor", garantindo que a informação seja legível para o receptor.
- **O que faz:** Formatação de dados, compressão e **criptografia**.
- **Exemplos:** `JPEG`, `MPEG`, `GIF`, `SSL/TLS`.
- **Analogia:** Decidir o idioma da carta ou se ela será escrita em código secreto.

#### 5. Camada de Sessão (*Session*)
Estabelece, gerencia e encerra as conexões entre as aplicações.
- **O que faz:** Controla o "diálogo". Se a conexão cair, pode tentar recuperar a partir de um ponto de verificação.
- **Analogia:** O aperto de mão inicial e a despedida ao final de uma conversa.

#### 4. Camada de Transporte (*Transport*)
Define como os dados serão enviados e cuida da integridade da entrega.
- **O que faz:** Divide os dados em **segmentos** e garante a ordem correta.
- **Principais Protocolos:** 
    - `TCP`: Confiável (confirma o recebimento).
    - `UDP`: Rápido (não verifica, ideal para jogos e streaming).
- **Analogia:** Escolher entre "Sedex com AR" (`TCP`) ou "Correio Simples" (`UDP`).

#### 3. Camada de Rede (*Network*)
Responsável pelo endereçamento e roteamento. Define o melhor caminho.
- **O que faz:** Opera com endereços **IP** e empacota segmentos em **Pacotes**.
- **Equipamento:** Roteador.
- **Analogia:** O endereço postal escrito no envelope (Rua, Número, CEP).

#### 2. Camada de Enlace de Dados (*Data Link*)
Foca no endereço físico da máquina na rede local.
- **O que faz:** Organiza pacotes em **Quadros (Frames)** e verifica erros físicos via endereço **MAC**.
- **Equipamento:** Switch.
- **Analogia:** O caminhão do correio que leva a carta da agência até a sua rua.

#### 1. Camada Física (*Physical*)
A parte tangível (hardware). A informação aqui são apenas **bits** (0 e 1).
- **O que faz:** Transmite bits através de meios físicos.
- **Exemplos:** Fibra óptica, Cabos Ethernet (RJ45), Wi-Fi, Hubs.
- **Analogia:** A estrada ou os fios de cobre por onde a carta viaja.

---

### 📊 Resumo Rápido: Modelo OSI

| Camada | Nome | Unidade de Dado | Função Principal | Exemplos |
| :--- | :--- | :--- | :--- | :--- |
| **7** | Aplicação     | Dados     | Interface com o usuário     | HTTP, Gmail |
| **6** | Apresentação  | Dados     | Tradução e Criptografia     | JPEG, SSL |
| **5** | Sessão        | Dados     | Controle de Diálogo         | Sockets |
| **4** | Transporte    | Segmentos | Confiabilidade e Fluxo      | TCP, UDP |
| **3** | Rede          | Pacotes   | Endereçamento e Rota        | IP, Roteador |
| **2** | Enlace        | Quadros   | Endereço Físico (Local)     | MAC, Switch |
| **1** | Física        | Bits      | Transmissão Elétrica/Óptica | Cabo, Wi-Fi |

> 💡 **Dica de Ouro:** Na prática, a internet usa o modelo **TCP/IP**, que é uma versão simplificada do OSI, mas o modelo OSI continua sendo a base fundamental para estudo e diagnóstico de redes.

---

## 2. O Modelo TCP/IP
Enquanto o OSI é um modelo teórico, o **TCP/IP é a implementação real** utilizada por toda a internet.

### As Camadas do TCP/IP (Versão Clássica de 4 Camadas)
1. **Application (Aplicação):** Engloba as funções de Aplicação, Apresentação e Sessão do OSI. (Ex: `HTTP`, `DNS`).
2. **Transport (Transporte):** Comunicação ponta a ponta e controle de fluxo. (Ex: `TCP`, `UDP`).
3. **Internet (Internet):** Endereçamento e roteamento de pacotes. Equivale à camada de Rede do OSI. (Ex: `IP`).
4. **Network Access (Acesso à Rede):** Define como os dados são fisicamente enviados. Engloba Enlace e Física do OSI. (Ex: `Ethernet`, `Wi-Fi`).

### 📦 O Encapsulamento (A "Matrioshka")
O encapsulamento é o processo onde cada camada "embrulha" os dados da camada superior com seus próprios cabeçalhos (*Headers*).

**Fluxo de Envio:**
`Dados (Aplicação)` -> `Segmento (Transporte)` -> `Pacote (Internet)` -> `Quadro (Acesso à Rede)` -> `Bits (Física)`

No destino, ocorre o **Desencapsulamento**: o receptor abre cada "caixa" na ordem inversa até chegar à mensagem original.

---

## 3. Comparativo: OSI vs TCP/IP

### Diferenças Gerais
| Característica | Modelo OSI | Modelo TCP/IP |
| :--- | :--- | :--- |
| **Natureza**      | Modelo Teórico / Referência | Modelo Prático / Implementação |
| **Complexidade**  | Mais complexo (7 camadas) | Mais simples (4 ou 5 camadas) |
| **Abordagem**     | Define rigorosamente cada função | Foca nos protocolos que funcionam |
| **Uso**           | Ensino e diagnóstico | Construção da Internet |

### Correlação de Camadas
| Camada OSI | Camada TCP/IP |
| :--- | :--- |
| 7. Aplicação / 6. Apresentação / 5. Sessão    | **Aplicação** |
| 4. Transporte                                 | **Transporte** |
| 3. Rede                                       | **Internet** |
| 2. Enlace / 1. Física                         | **Acesso à Rede** |

---

## 4. Protocolos e Portas
Para entender os protocolos, é preciso entender as **Portas**. 
- **Endereço IP** é como o Endereço do Prédio.
- **Porta** é como a Porta de entrada específica para cada serviço.

Todos os protocolos abaixo pertencem à **Camada de Aplicação**.

### 🔍 Principais Protocolos

*   **DNS (Domain Name System) - Porta 53**: A "lista telefônica" da web. Traduz nomes (`google.com`) para IPs.
*   **DHCP (Dynamic Host Configuration Protocol) - Portas 67/68**: O "recepcionista". Atribui IPs automaticamente aos dispositivos na rede.
*   **HTTP (Hypertext Transfer Protocol) - Porta 80**: Base da Web. Não é criptografado (como um cartão-postal).
*   **HTTPS (HTTP Secure) - Porta 443**: Versão segura do HTTP. Usa SSL/TLS para criptografar os dados (como um cofre blindado).
*   **FTP (File Transfer Protocol) - Porta 21**: Especializado em transferência de arquivos (Upload/Download).
*   **SSH (Secure Shell) - Porta 22**: Acesso remoto seguro e criptografado para administração de servidores.
*   **SMTP (Simple Mail Transfer Protocol) - Porta 25**: Protocolo para **envio** de e-mails.

### 📋 Tabela de Memorização de Protocolos

| Protocolo | Função Principal | Porta | Tipo de Dado |
| :--- | :--- | :--- | :--- |
| **DNS**   | Traduz Nome para IP           | 53    | Nomes de Domínio              |
| **DHCP**  | Entrega IPs automaticamente   | 67/68 | Configurações de Rede         |
| **HTTP**  | Navegação Web (Simples)       | 80    | Páginas Web (Texto/Img)       |
| **HTTPS** | Navegação Web (Segura)        | 443   | Páginas Web (Criptografadas)  |
| **FTP**   | Transferência de Arquivos     | 21    | Arquivos / Pastas             |
| **SSH**   | Acesso Remoto Seguro          | 22    | Comandos de Terminal          |
| **SMTP**  | Envio de E-mail               | 25    | Mensagens de E-mail           |


Subnetting e CIDR: Calculando Sub-redes Manualmente
1. Conceitos Básicos
Endereço IP: Composto por 32 bits (4 octetos de 8 bits). Ex: 192.168.1.0
Máscara de Rede: Define qual parte do IP é a Rede (Network) e qual parte é o Host (dispositivo).
CIDR (Classless Inter-Domain Routing): É a barra (/) seguida de um número. Esse número indica quantos bits "1" existem na máscara.
/24 significa que os primeiros 24 bits são "1" e os últimos 8 são "0".
2. A Tabela de Referência (O Segredo)
Para calcular /24, /25 e /26, estamos mexendo no 4º octeto. Confira os valores possíveis de um octeto (8 bits):

CIDR	Binário (4º octeto)	Máscara Decimal	Valor do "Salto" (Número Mágico)
/24	00000000	.0	256
/25	10000000	.128	128
/26	11000000	.192	64
/27	11100000	.224	32
Como achar o Número Mágico? Basta fazer: $256 - (\text{valor da máscara})$.

Exemplo /26: $256 - 192 = 64$.
3. Calculando na Prática
IP base: 192.168.1.0

Exemplo 1: /24
Máscara: 255.255.255.0
Número Mágico: 256
Cálculo: Como o salto é 256, só existe uma única rede.
Endereço de Rede: 192.168.1.0
Primeiro Host: 192.168.1.1
Último Host: 192.168.1.254
Broadcast: 192.168.1.255
Total de IPs úteis: $256 - 2 = 254$.
Exemplo 2: /25 (Divide a rede em 2)
Máscara: 255.255.255.128
Número Mágico: 128
Redes: Começam no 0 e saltam de 128 em 128.
Rede	Endereço de Rede	Primeiro Host	Último Host	Broadcast
1ª	...1.0	...1.1	...1.126	...1.127
2ª	...1.128	...1.129	...1.254	...1.255
Total de IPs úteis por sub-rede: $128 - 2 = 126$.
Exemplo 3: /26 (Divide a rede em 4)
Máscara: 255.255.255.192
Número Mágico: 64
Redes: Saltam de 64 em 64.
Rede	Rede (ID)	Primeiro Host	Último Host	Broadcast
1ª	...1.0	...1.1	...1.62	...1.63
2ª	...1.64	...1.65	...1.126	...1.127
3ª	...1.128	...1.129	...1.190	...1.191
4ª	...1.192	...1.193	...1.254	...1.255
Total de IPs úteis por sub-rede: $64 - 2 = 62$.
4. Resumo do Passo a Passo
Identifique o CIDR (ex: /26).
Descubra a Máscara Decimal (ex: .192).
Calcule o Número Mágico ($256 - 192 = 64$).
Liste as Redes: Comece do .0 e some o número mágico sucessivamente (0, 64, 128, 192...).
Determine o Broadcast: O Broadcast de uma rede é sempre um número antes do início da próxima rede.
Ex: Se a Rede 2 começa em .64, o Broadcast da Rede 1 é .63.
Determine os Hosts: Os hosts são todos os números entre a Rede e o Broadcast.
💡 Dica de Ouro (Fórmula de IPs)
Para saber quantos IPs totais existem em uma sub-rede sem fazer a tabela:

IPs Totais
=
2
(
32
−
CIDR
)
IPs Totais=2 
(32−CIDR)
 

/24: $2^{(32-24)} = 2^8 = 256$ IPs.
/25: $2^{(32-25)} = 2^7 = 128$ IPs.
/26: $2^{(32-26)} = 2^6 = 64$ IPs.
Lembre-se: Subtraia sempre 2 para obter os IPs utilizáveis (o primeiro é a Rede e o último é o Broadcast).

