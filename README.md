
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