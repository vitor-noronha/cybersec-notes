
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


---

# Subnetting e CIDR: Calculando Sub-redes Manualmente

## 1. Conceitos Básicos
*   **Endereço IP:** Composto por 32 bits (4 octetos de 8 bits). Ex: `192.168.1.0`
*   **Máscara de Rede:** Define qual parte do IP é a **Rede** (Network) e qual parte é o **Host** (dispositivo).
*   **CIDR (Classless Inter-Domain Routing):** É a barra (`/`) seguida de um número. Esse número indica quantos bits "1" existem na máscara.
    *   **/24** significa que os primeiros 24 bits são "1" e os últimos 8 são "0".

## 2. A Tabela de Referência (O Segredo)
Para calcular `/24`, `/25` e `/26`, estamos mexendo no **4º octeto**. Confira os valores possíveis de um octeto (8 bits):

| CIDR | Binário (4º octeto) | Máscara Decimal | Valor do "Salto" (Número Mágico) |
| :--- | :--- | :--- | :--- |
| `/24` | `00000000` | `.0` | **256** |
| `/25` | `10000000` | `.128` | **128** |
| `/26` | `11000000` | `.192` | **64** |
| `/27` | `11100000` | `.224` | **32** |

**Como achar o Número Mágico?**
Basta fazer: $256 - (\text{valor da máscara})$.
*   *Exemplo /26:* $256 - 192 = 64$.

## 3. Calculando na Prática
**IP base:** `192.168.1.0`

### Exemplo 1: `/24`
*   **Máscara:** `255.255.255.0`
*   **Número Mágico:** 256
*   **Cálculo:** Como o salto é 256, só existe uma única rede.
    *   **Endereço de Rede:** `192.168.1.0`
    *   **Primeiro Host:** `192.168.1.1`
    *   **Último Host:** `192.168.1.254`
    *   **Broadcast:** `192.168.1.255`
    *   **Total de IPs úteis:** $256 - 2 = 254$.

### Exemplo 2: `/25` (Divide a rede em 2)
*   **Máscara:** `255.255.255.128`
*   **Número Mágico:** 128
*   **Redes:** Começam no 0 e saltam de 128 em 128.

| Rede | Endereço de Rede | Primeiro Host | Último Host | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| **1ª** | `...1.0` | `...1.1` | `...1.126` | `...1.127` |
| **2ª** | `...1.128` | `...1.129` | `...1.254` | `...1.255` |

*   **Total de IPs úteis por sub-rede:** $128 - 2 = 126$.

### Exemplo 3: `/26` (Divide a rede em 4)
*   **Máscara:** `255.255.255.192`
*   **Número Mágico:** 64
*   **Redes:** Saltam de 64 em 64.

| Rede | Rede (ID) | Primeiro Host | Último Host | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| **1ª** | `...1.0` | `...1.1` | `...1.62` | `...1.63` |
| **2ª** | `...1.64` | `...1.65` | `...1.126` | `...1.127` |
| **3ª** | `...1.128` | `...1.129` | `...1.190` | `...1.191` |
| **4ª** | `...1.192` | `...1.193` | `...1.254` | `...1.255` |

*   **Total de IPs úteis por sub-rede:** $64 - 2 = 62$.

## 4. Resumo do Passo a Passo
1.  **Identifique o CIDR** (ex: `/26`).
2.  **Descubra a Máscara Decimal** (ex: `.192`).
3.  **Calcule o Número Mágico** ($256 - 192 = 64$).
4.  **Liste as Redes:** Comece do `.0` e some o número mágico sucessivamente (`0, 64, 128, 192...`).
5.  **Determine o Broadcast:** O Broadcast de uma rede é sempre um número antes do início da próxima rede.
    *   *Ex: Se a Rede 2 começa em `.64`, o Broadcast da Rede 1 é `.63`.*
6.  **Determine os Hosts:** Os hosts são todos os números entre a Rede e o Broadcast.

---

### 💡 Dica de Ouro (Fórmula de IPs)
Para saber quantos IPs totais existem em uma sub-rede sem fazer a tabela:

$$\text{IPs Totais} = 2^{(32 - \text{CIDR})}$$

*   **/24:** $2^{(32-24)} = 2^8 = 256$ IPs.
*   **/25:** $2^{(32-25)} = 2^7 = 128$ IPs.
*   **/26:** $2^{(32-26)} = 2^6 = 64$ IPs.

> **Lembre-se:** Subtraia sempre **2** para obter os IPs utilizáveis (o primeiro é a Rede e o último é o Broadcast).

---

# A Tríade CIA: A Base da Segurança da Informação

A **Tríade CIA** (do inglês *Confidentiality, Integrity, Availability*) é a base de toda a Segurança da Informação. Imagine que ela é um tripé: se qualquer uma dessas pernas for quebrada, a segurança do sistema como um todo desmorona.

> **Importante:** Não tem nada a ver com a agência de espionagem dos EUA, mas sim com três pilares fundamentais da tecnologia.

---

## 1. Confidencialidade (*Confidentiality*)

**O que é:** Garantir que a informação seja acessada **apenas por quem tem autorização**. É o ato de manter segredos. Se alguém não autorizado consegue ler um dado, a confidencialidade foi quebrada.

### Como se garante?
*   **Criptografia:** Transforma o texto em algo ilegível para quem não tem a chave.
*   **Controle de Acesso/Senhas:** Apenas usuários autenticados entram.
*   **MFA (Autenticação de Dois Fatores):** Uma camada extra de proteção.

### Exemplo Real
*   **WhatsApp:** Quando você envia uma mensagem, ela é criptografada de ponta a ponta. Nem o Facebook/Meta consegue ler o conteúdo; apenas você e o destinatário possuem a "chave" para a leitura.

### O que acontece se falhar?
*   **Vazamento de Dados:** Se um hacker invade um banco de dados e expõe as senhas ou CPFs de milhões de clientes, houve uma quebra de confidencialidade.

---

## 2. Integridade (*Integrity*)

**O que é:** Garantir que a informação seja **precisa, completa e não tenha sido alterada** de forma indevida. A informação deve ser confiável desde a origem até o destino.

### Como se garante?
*   **Hashing (Soma de Verificação):** Um código único gerado a partir de um arquivo. Se um único bit do arquivo mudar, o código (*hash*) muda completamente.
*   **Assinaturas Digitais:** Provam que o documento não foi alterado após a assinatura.
*   **Controle de Versão:** Registro de quem alterou o quê e quando.

### Exemplo Real
*   **Transferência Bancária:** Imagine que você transfere R$ 10,00 para um amigo. Se um hacker interceptar esse pacote de dados e alterar o valor para R$ 1.000,00, ele quebrou a integridade da transação. O banco usa mecanismos de integridade para garantir que o valor enviado seja exatamente o recebido.

### O que acontece se falhar?
*   **Informação Corrompida:** Um prontuário médico onde o tipo sanguíneo do paciente é alterado por erro ou malícia, podendo levar a um erro fatal em uma cirurgia.

---

## 3. Disponibilidade (*Availability*)

**O que é:** Garantir que a informação e os sistemas estejam **acessíveis e funcionando** sempre que o usuário autorizado precisar deles. De nada adianta um dado ser secreto e íntegro se você não consegue acessá-lo.

### Como se garante?
*   **Redundância:** Ter dois ou mais servidores fazendo a mesma coisa (se um cai, o outro assume).
*   **Backups:** Cópias de segurança para restaurar o sistema após uma falha.
*   **Proteção contra DDoS:** Sistemas que evitam que o servidor seja derrubado por excesso de acessos falsos.

### Exemplo Real
*   **Amazon na Black Friday:** Milhões de pessoas acessando ao mesmo tempo. Para manter a disponibilidade, a Amazon usa milhares de servidores espalhados pelo mundo (**Balanceamento de Carga**). Se o site ficasse fora do ar por 1 hora, a disponibilidade teria falhado e a empresa perderia milhões.

### O que acontece se falhar?
*   **Interrupção de Serviço:** Um ataque de *Ransomware* que sequestra os dados de um hospital. Os médicos não conseguem acessar as fichas dos pacientes. Os dados ainda estão lá (confidencialidade) e não foram alterados (integridade), mas não estão **disponíveis**.

---

## 📊 Resumo Comparativo

| Pilar | Objetivo Principal | Pergunta Chave | Ferramenta Comum | Exemplo de Falha |
| :--- | :--- | :--- | :--- | :--- |
| **Confidencialidade** | Sigilo | "Quem pode ver isso?" | Criptografia | Vazamento de senhas |
| **Integridade** | Precisão | "Isso foi alterado?" | Hash / Assinatura | Alteração de saldo bancário |
| **Disponibilidade** | Acesso | "O sistema está online?" | Redundância / Backup | Site fora do ar (DDoS) |

---

## ⚖️ O Equilíbrio da Tríade

Na vida real, é difícil ter 100% dos três pilares ao mesmo tempo. Existe sempre um ***trade-off*** (equilíbrio).

**Exemplo:** Se você colocar 50 camadas de senhas, biometria e reconhecimento facial para acessar um arquivo (**Confidencialidade máxima**), você tornará o acesso muito lento e difícil para o usuário, prejudicando severamente a **Disponibilidade**.

O profissional de segurança da informação decide onde colocar o peso do tripé dependendo do que é mais crítico para cada tipo de negócio.


---

# AAA Framework: Authentication, Authorization, and Accounting

O **AAA Framework** é um modelo conceitual utilizado para controlar o acesso a redes e recursos de computação. Ele define a arquitetura necessária para garantir que apenas pessoas autorizadas acessem um sistema, que elas façam apenas o que lhes é permitido e que todas as suas ações sejam registradas.

Imagine o AAA como o "sistema de segurança de um prédio empresarial": ele controla quem entra, onde a pessoa pode circular e registra a hora de entrada e saída.

---

## 1. Authentication (Autenticação)
**Pergunta chave:** *"Quem é você?"*

A autenticação é o primeiro passo. É o processo de verificar a identidade de um usuário, dispositivo ou sistema. O objetivo é garantir que a entidade é realmente quem ela diz ser.

*   **Como funciona:** O usuário fornece "algo" para provar sua identidade. Existem três fatores principais de autenticação:
    *   **Algo que você sabe:** Senhas, PINs, perguntas de segurança.
    *   **Algo que você tem:** Tokens físicos, cartões inteligentes, smartphones (SMS/Apps de autenticação).
    *   **Algo que você é:** Biometria (impressão digital, reconhecimento facial, íris).
*   **Exemplo Real:** Quando você digita seu usuário e senha no Gmail e depois confirma o acesso através de um código enviado ao seu celular (MFA).

---

## 2. Authorization (Autorização)
**Pergunta chave:** *"O que você pode fazer aqui?"*

Uma vez que o sistema sabe quem você é (autenticação), ele precisa decidir quais privilégios você possui. A autorização define as permissões de acesso aos recursos.

*   **Como funciona:** O sistema consulta uma lista de permissões ou perfis vinculados àquela identidade.
    *   **RBAC (Role-Based Access Control):** Controle de acesso baseado em funções. Ex: Um "Administrador" pode deletar arquivos, mas um "Visitante" pode apenas ler.
    *   **ACLs (Access Control Lists):** Listas que definem explicitamente quem pode acessar o quê.
*   **Exemplo Real:** Em um sistema de empresa, o funcionário do RH consegue ver a folha de pagamento de todos os funcionários, mas o desenvolvedor de software (embora autenticado no mesmo sistema) não tem permissão para acessar essa pasta.

---

## 3. Accounting (Accounting/Auditoria)
**Pergunta chave:** *"O que você fez e quando?"*

A contabilização (ou auditoria) é o processo de rastrear e registrar as atividades do usuário enquanto ele está no sistema. Isso é fundamental para segurança, faturamento e conformidade legal.

*   **Como funciona:** O sistema gera logs (registros) detalhados de cada ação.
    *   **O que é registrado:** Horário de login/logout, arquivos acessados, comandos executados e alterações feitas no sistema.
    *   **Finalidade:** Se ocorrer um ataque ou erro, o administrador pode olhar os logs para saber exatamente quem foi o responsável e como aconteceu.
*   **Exemplo Real:** Um log de servidor que mostra: *"O usuário 'admin_joao' alterou a configuração do Firewall às 14:30 do dia 10/05 através do IP 192.168.1.50"*.

---

## 🚀 Resumo Comparativo

| Pilar | Objetivo | Foco | Exemplo Prático |
| :--- | :--- | :--- | :--- |
| **Authentication** | Validar Identidade | **Identidade** | Digitar senha e usar biometria. |
| **Authorization** | Definir Permissões | **Privilégios** | Ter acesso à pasta "Financeiro", mas não à "RH". |
| **Accounting** | Monitorar Ações | **Rastreabilidade** | Log de auditoria registrando a alteração de um arquivo. |

---

## 🛠️ Protocolos Comuns de Implementação

Na prática, o AAA não é apenas um conceito, mas é implementado através de protocolos de rede. Os dois mais famosos são:

### 1. RADIUS (Remote Authentication Dial-In User Service)
*   **Uso:** Muito comum em Wi-Fis corporativos (WPA2/WPA3 Enterprise) e VPNs.
*   **Características:** Combina Autenticação e Autorização em um único passo. É mais simples e amplamente compatível.

### 2. TACACS+ (Terminal Access Controller Access-Control System Plus)
*   **Uso:** Administradores de rede configurando roteadores e switches (Cisco).
*   **Características:** Separa completamente a Autenticação, a Autorização e a Auditoria. É mais seguro e oferece controle granular sobre cada comando que o administrador pode digitar.

---

## 💡 Analogia Final para Memorizar

Imagine que você vai a um **Hotel**:

1.  **Autenticação:** Você chega na recepção e apresenta seu **RG**. O recepcionista confirma que você é você mesmo.
2.  **Autorização:** O recepcionista te entrega a **chave do quarto 204**. Essa chave abre a porta do seu quarto e a academia, mas **não abre** a porta da cozinha do hotel nem o escritório do gerente.
3.  **Accounting:** No final da estadia, o hotel gera a **conta**. Eles sabem que você usou o frigibar três vezes e pediu serviço de quarto na terça-feira. Tudo foi registrado.


---

# Guia de Ameaças à Segurança da Informação

No mundo da cibersegurança, as ameaças são geralmente divididas entre **técnicas** (software malicioso) e **humanas** (manipulação e comportamento). Para entender as ameaças, precisamos diferenciar a *ferramenta* usada do *método* de ataque.

---

## 1. Malware (Software Malicioso)
**O que é:** *Malware* é a abreviação de "Malicious Software". É um termo "guarda-chuva" que engloba qualquer programa desenvolvido para infiltrar-se, danificar, desativar ou roubar dados de um sistema sem o consentimento do usuário.

### Principais subtipos de Malware:
*   **Vírus:** Anexa-se a um arquivo legítimo e precisa de interação humana (como abrir um `.exe`) para se espalhar.
*   **Worm (Verme):** Diferente do vírus, o worm é autossuficiente. Ele explora vulnerabilidades de rede para se espalhar automaticamente de um computador para outro.
*   **Trojan (Cavalo de Troia):** Disfarça-se de um software útil (ex: um jogo grátis ou um antivírus falso) para enganar o usuário e abrir uma "porta dos fundos" (*backdoor*) para o invasor.
*   **Spyware:** Software espião que coleta informações (teclas digitadas, histórico de navegação) e as envia para terceiros.

---

## 2. Ransomware (O "Sequestrador")
**O que é:** Um tipo específico e extremamente perigoso de malware. O Ransomware não apenas infecta a máquina, mas **criptografa** os arquivos do usuário, tornando-os ilegíveis.

*   **Como funciona:** Após a criptografia, o atacante exibe uma mensagem exigindo o pagamento de um **resgate** (*ransom*), geralmente em criptomoedas (como Bitcoin), para liberar a chave de descriptografia.
*   **Ransomware 2.0 (Dupla Extorsão):** Hoje, os criminosos não apenas bloqueiam os dados, mas também ameaçam **vazar as informações** confidenciais na internet caso o resgate não seja pago.
*   **Exemplo Real:** O ataque *WannaCry*, que paralisou hospitais e empresas em todo o mundo em 2017.

---

## 3. Social Engineering (Engenharia Social)
**O que é:** A engenharia social não é um software, mas sim uma **técnica de manipulação psicológica**. O objetivo é enganar as pessoas para que elas entreguem informações confidenciais ou realizem ações que comprometam a segurança.

*   **O "Hacker Humano":** O atacante explora a confiança, a pressa, o medo ou a autoridade.
*   **Técnicas comuns:**
    *   **Pretexting:** Criar uma história convincente (ex: "Sou do suporte técnico e notei um erro na sua conta").
    *   **Baiting (Isca):** Deixar um pendrive infectado "perdido" no estacionamento de uma empresa para que alguém curioso o conecte ao computador.
    *   **Quid Pro Quo:** Oferecer um benefício em troca de informação (ex: "Faço a atualização do seu PC se você me der sua senha").

---

## 4. Phishing (A "Pesca" de Dados)
**O que é:** O *Phishing* é a aplicação mais comum da engenharia social. O termo vem de *fishing* (pescar), pois o atacante "lança a isca" esperando que alguém morda.

*   **Como funciona:** Envio de comunicações fraudulentas (e-mail, SMS, redes sociais) que imitam marcas ou pessoas confiáveis (bancos, Netflix, Governo).
*   **Variações:**
    *   **Spear Phishing:** Ataque focado em um alvo específico (ex: um e-mail personalizado para o Diretor Financeiro de uma empresa).
    *   **Smishing:** Phishing via SMS.
    *   **Vishing:** Phishing via voz (chamadas telefônicas).
*   **Exemplo Real:** Um e-mail dizendo: *"Sua conta foi bloqueada! Clique aqui para atualizar seus dados agora"*, levando a usuário a uma página falsa que rouba a senha.

---

## 5. Insider Threat (Ameaça Interna)
**O que é:** Diferente dos ataques externos, a *Insider Threat* ocorre quando a ameaça vem de **dentro da organização**. É alguém que já possui acesso legítimo aos sistemas (funcionários, ex-funcionários, contratados ou parceiros).

### Os três tipos de "Insiders":
1.  **O Malicioso:** O funcionário que rouba segredos industriais para vender ao concorrente ou que deleta dados por vingança após ser demitido.
2.  **O Negligente:** O funcionário que, sem intenção de causar mal, deixa a senha anotada em um post-it ou clica em um link de phishing, abrindo a porta para hackers.
3.  **O Infiltrado:** Um agente externo que consegue um emprego na empresa apenas para roubar dados de dentro.

---

## 📊 Resumo Comparativo

| Ameaça | Natureza | Método Principal | Alvo | Impacto Principal |
| :--- | :--- | :--- | :--- | :--- |
| **Malware** | Técnica | Código Malicioso | Sistema / Software | Instabilidade / Roubo |
| **Ransomware** | Técnica | Criptografia | Dados / Arquivos | Perda de Dados / Financeiro |
| **Soc. Engineering** | Humana | Manipulação | Psicologia Humana | Quebra de Confiança |
| **Phishing** | Humana | Comunicação Falsa | Credenciais (Senhas) | Roubo de Identidade |
| **Insider Threat** | Humana | Acesso Legítimo | Infraestrutura Interna | Espionagem / Sabotagem |

---

## 🛡️ Dicas de Prevenção (Resumo)

*   **Contra Malware/Ransomware:** Manter softwares atualizados e ter **Backups offline** regulares.
*   **Contra Phishing/Eng. Social:** Desconfiar de urgências excessivas, verificar o remetente e nunca clicar em links suspeitos.
*   **Contra Insider Threats:** Aplicar o **Princípio do Menor Privilégio** (dar ao usuário apenas o acesso necessário para sua função) e monitorar logs de acesso.

---

# 🛡️ Guia OWASP Top 10: As Vulnerabilidades Web Mais Críticas

## 📌 Introdução
O **OWASP Top 10** é um documento padrão para desenvolvedores e profissionais de segurança web. Ele identifica as dez vulnerabilidades de segurança de aplicações web mais críticas, baseando-se em dados de centenas de aplicações e milhares de especialistas.

**Importante:** O Top 10 não é uma lista exaustiva de todas as vulnerabilidades, mas sim um guia de conscientização sobre os riscos mais prevalentes.

---

## 🚀 As 10 Vulnerabilidades (Versão 2021)

### 1. A01:2021 – Broken Access Control (Quebra de Controle de Acesso)
Ocorre quando as restrições sobre o que as usuários autenticados podem fazer não são aplicadas corretamente. 

*   **O que é:** Um usuário consegue acessar dados ou funções que não deveria (ex: acessar a página de admin sendo um usuário comum).
*   **Exemplo:** Alterar a URL de `meusite.com/perfil/123` para `meusite.com/perfil/124` e conseguir ver os dados de outro usuário.
*   **Como prevenir:** 
    *   Implementar o **Princípio do Menor Privilégio**.
    *   Negar o acesso por padrão (Deny by default).
    *   Validar permissões no servidor em cada requisição.

### 2. A02:2021 – Cryptographic Failures (Falhas Criptográficas)
Anteriormente chamado de "Exposição de Dados Sensíveis". Foca na falha em proteger dados em repouso ou em trânsito.

*   **O que é:** Uso de algoritmos de criptografia fracos, senhas armazenadas em texto simples ou falta de HTTPS.
*   **Exemplo:** Armazenar senhas usando MD5 (algoritmo obsoleto e vulnerável) em vez de Argon2 ou BCrypt.
*   **Como prevenir:** 
    *   Criptografar todos os dados sensíveis.
    *   Usar protocolos modernos (TLS 1.3).
    *   Utilizar hashes fortes com *salt*.

### 3. A03:2021 – Injection (Injeção)
Acontece quando dados não confiáveis são enviados para um interpretador como parte de um comando ou consulta.

*   **O que é:** O atacante "injeta" código malicioso que o servidor executa. Inclui **SQL Injection (SQLi)** e **Cross-Site Scripting (XSS)**.
*   **Exemplo:** No campo de login, digitar `' OR '1'='1` para burlar a autenticação de um banco de dados.
*   **Como prevenir:** 
    *   Utilizar **Consultas Parametrizadas (Prepared Statements)**.
    *   Validar e sanitizar todas as entradas do usuário.
    *   Usar APIs seguras.

### 4. A04:2021 – Insecure Design (Design Inseguro)
Diferente de um erro de implementação, aqui o problema está na **arquitetura** da aplicação.

*   **O que é:** Falhas que ocorrem antes mesmo do código ser escrito, devido a requisitos de segurança mal planejados.
*   **Exemplo:** Um sistema de recuperação de senha que faz perguntas óbvias (ex: "Qual a cor do seu carro?"), permitindo que qualquer pessoa adivinhe.
*   **Como prevenir:** 
    *   Implementar **Modelagem de Ameaças (Threat Modeling)**.
    *   Utilizar bibliotecas de design de segurança comprovadas.
    *   Realizar revisões de design com especialistas.

### 5. A05:2021 – Security Misconfiguration (Configuração Incorreta de Segurança)
Ocorre quando as configurações de segurança não são definidas ou são configuradas de forma incorreta/padrão.

*   **O que é:** Deixar portas abertas desnecessariamente, usar senhas padrão de admin ou exibir mensagens de erro detalhadas para o usuário.
*   **Exemplo:** Um servidor Tomcat instalado com a conta `admin/admin` ativa.
*   **Como prevenir:** 
    *   Remover recursos e funcionalidades não utilizados.
    *   Alterar todas as senhas padrão imediatamente.
    *   Automatizar o processo de *hardening* (endurecimento) do sistema.

### 6. A06:2021 – Vulnerable and Outdated Components (Componentes Vulneráveis e Desatualizados)
Uso de bibliotecas, frameworks ou dependências que possuem vulnerabilidades conhecidas.

*   **O que é:** Manter versões antigas de softwares que já possuem "patches" (correções) disponíveis, mas não aplicados.
*   **Exemplo:** Usar uma versão do Log4j vulnerável ao *Log4Shell*.
*   **Como prevenir:** 
    *   Manter um inventário de todas as dependências (SBOM).
    *   Usar ferramentas de scan de dependências (ex: `npm audit`, Snyk).
    *   Atualizar componentes regularmente.

### 7. A07:2021 – Identification and Authentication Failures (Falhas de Identificação e Autenticação)
Problemas na confirmação da identidade do usuário.

*   **O que é:** Permitir senhas fracas, não ter proteção contra ataques de força bruta ou falhas na gestão de sessões.
*   **Exemplo:** Permitir que um usuário tente a senha 1.000 vezes sem bloquear a conta ou expirar a sessão.
*   **Como prevenir:** 
    *   Implementar **Autenticação de Múltiplos Fatores (MFA)**.
    *   Impor políticas de senhas fortes.
    *   Gerar IDs de sessão longos e aleatórios.

### 8. A08:2021 – Software and Data Integrity Failures (Falhas de Integridade de Software e Dados)
Ocorre quando o software assume que a integridade de um dado ou código e válida sem verificá-la.

*   **O que é:** Inclui a **Desserialização Insegura**, onde um objeto é reconstruído a partir de dados maliciosos.
*   **Exemplo:** Baixar uma atualização de software de um servidor sem verificar a assinatura digital do arquivo.
*   **Como prevenir:** 
    *   Utilizar assinaturas digitais para verificar a origem do código.
    *   Não aceitar objetos serializados de fontes não confiáveis.
    *   Implementar verificações de integridade (Checksum).

### 9. A09:2021 – Security Logging and Monitoring Failures (Falhas de Log e Monitoramento de Segurança)
A incapacidade de detectar, registrar e responder a ataques em tempo real.

*   **O que é:** Não ter logs dos eventos críticos ou ter logs que não são monitorados, permitindo que um invasor permaneça no sistema por meses.
*   **Exemplo:** Um atacante tenta 10 mil logins por hora, mas o sistema não gera nenhum alerta para o administrador.
*   **Como prevenir:** 
    *   Registrar falhas de autenticação e acessos a dados sensíveis.
    *   Utilizar sistemas de monitoramento centralizados (ex: SIEM, ELK Stack).
    *   Estabelecer alertas para atividades suspeitas.

### 10. A10:2021 – Server-Side Request Forgery (SSRF)
Ocorre quando uma aplicação web busca um recurso remoto sem validar a URL fornecida pelo usuário.

*   **O que é:** O atacante força o servidor a fazer requisições para endereços internos ou externos que deveriam ser inacessíveis.
*   **Exemplo:** Um site que gera preview de links. O atacante envia `http://localhost:8080/admin` para tentar acessar o painel interno do servidor.
*   **Como prevenir:** 
    *   Validar e sanitizar a URL de entrada.
    *   Usar uma *Allow-list* (lista permitida) de domínios.
    *   Isolar a rede do servidor web para que ele não acesse a rede interna.

---

## 🛠️ Resumo para Implementação Rápida

| Vulnerabilidade | Foco Principal | Solução Chave |
| :--- | :--- | :--- |
| **Access Control** | Permissões | Menor Privilégio |
| **Cryptographic Failures** | Proteção de Dados | Criptografia Forte / HTTPS |
| **Injection** | Entrada de Dados | Parametrização $\to$ Query |
| **Insecure Design** | Arquitetura | Modelagem de Ameaças |
| **Security Misconfig** | Configurações | Hardening / Automação |
| **Vulnerable Components** | Dependências | Atualizações / Scans |
| **Auth Failures** | Identidade | MFA / Senhas Fortes |
| **Integrity Failures** | Confiança no Código | Assinaturas Digitais |
| **Logging Failures** | Visibilidade | Monitoramento Ativo (SIEM) |
| **SSRF** | Requisições do Servidor | Allow-lists de URL |

---

## 📚 Recursos Adicionais
*   **Site Oficial:** [owasp.org](https://owasp.org)
*   **OWASP ZAP:** Ferramenta gratuita de scan de vulnerabilidades.
*   **Juice Shop:** Uma aplicação propositalmente vulnerável da OWASP para você praticar.