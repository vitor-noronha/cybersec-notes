"# cybersec-notes" 
O Modelo OSI (Open Systems Interconnection, ou Interconexão de Sistemas Abertos) é um modelo conceitual criado para padronizar a comunicação entre diferentes sistemas de computadores.

Imagine que ele é como um "manual de instruções" universal. Sem ele, um computador da Apple poderia não conseguir "conversar" com um computador da Dell ou um servidor Linux.

O modelo é dividido em 7 camadas. Quando você envia um dado, ele desce do nível 7 para o 1. Quando você recebe, ele sobe do 1 para o 7.

Aqui está a explicação detalhada de cada camada, do topo (usuário) para a base (hardware):

7. Camada de Aplicação (Application)
É a camada que interage diretamente com o usuário final. Ela fornece a interface para que os softwares (como o seu navegador ou cliente de e-mail) acessem a rede.

O que faz: Identifica os parceiros de comunicação e sincroniza a comunicação.
Exemplos de Protocolos: HTTP (Web), FTP (Arquivos), SMTP (E-mail), DNS.
Analogia: É como se fosse a pessoa escrevendo a carta.
6. Camada de Apresentação (Presentation)
Esta camada atua como um "tradutor". Ela garante que a informação enviada por um sistema seja legível para o outro.

O que faz: Formatação de dados, compressão e, principalmente, a criptografia. Ela transforma os dados da aplicação em um formato universal.
Exemplos: JPEG, MPEG, GIF, SSL/TLS (criptografia).
Analogia: É como decidir em qual idioma a carta será escrita ou se ela será escrita em código secreto.
5. Camada de Sessão (Session)
Sua função é estabelecer, gerenciar e encerrar as conexões entre as aplicações.

O que faz: Ela controla o "diálogo" entre os computadores. Se a conexão cair, a camada de sessão pode tentar recuperar a conexão a partir de um ponto de verificação.
Analogia: É como o aperto de mão inicial e a despedida ao final de uma conversa telefônica.
4. Camada de Transporte (Transport)
Aqui é onde se decide como os dados serão enviados. Ela cuida da integridade da entrega.

O que faz: Divide os dados em pedaços menores (segmentos) e garante que cheguem ao destino na ordem correta e sem erros.
Principais Protocolos:
TCP: Confiável (confirma se o dado chegou).
UDP: Rápido (envia e não verifica, usado em jogos e streaming).
Analogia: Decidir se você enviará a carta via "Sedex com aviso de recebimento" (TCP) ou "Correio Simples" (UDP).
3. Camada de Rede (Network)
Esta camada é responsável pelo endereçamento e roteamento. Ela decide qual o melhor caminho para o dado chegar ao destino.

O que faz: Aqui operam os endereços IP. Ela empacota os segmentos da camada anterior em "Pacotes".
Equipamento principal: Roteador.
Analogia: É o endereço postal escrito no envelope (Rua, Número, CEP).
2. Camada de Enlace de Dados (Data Link)
Enquanto a camada de rede olha o endereço global (IP), a de enlace olha o endereço físico da máquina na rede local.

O que faz: Organiza os pacotes em "Quadros" (Frames) e verifica erros físicos. Ela utiliza o endereço MAC (único de cada placa de rede).
Equipamento principal: Switch.
Analogia: É como o caminhão do correio que leva a carta da agência central até a sua rua específica.
1. Camada Física (Physical)
É a parte tangível, o hardware. Aqui a informação não é mais um "arquivo", mas sim bits (0 e 1).

O que faz: Transmite os bits através de meios físicos (cabos, ondas de rádio, luz).
Exemplos: Cabos de fibra óptica, cabos Ethernet (RJ45), Wi-Fi (ondas), Hubs.
Analogia: É a estrada, os trilhos ou os fios de cobre por onde a carta viaja fisicamente.
Resumo Rápido para Memorizar
Camada	Nome	Unidade de Dado	Função Principal	Exemplo
7	Aplicação	Dados	Interface com o usuário	HTTP, Gmail
6	Apresentação	Dados	Tradução e Criptografia	JPEG, SSL
5	Sessão	Dados	Controle de Diálogo	Sockets
4	Transporte	Segmentos	Confiabilidade e Fluxo	TCP, UDP
3	Rede	Pacotes	Endereçamento e Rota	IP, Roteador
2	Enlace	Quadros	Endereço Físico (Local)	MAC, Switch
1	Física	Bits	Transmissão Elétrica/Óptica	Cabo, Wi-Fi
Dica de ouro: Na prática, a internet hoje usa um modelo simplificado chamado TCP/IP, que agrupa algumas dessas camadas (ex: Aplicação, Apresentação e Sessão viram apenas "Aplicação"), mas o Modelo OSI continua sendo a base para estudar e entender como as redes funcionam.

Agora que você já conhece o Modelo OSI, entender o TCP/IP será muito mais fácil, pois ele é a aplicação prática de tudo aquilo.

Enquanto o OSI é um modelo teórico (está no papel para fins de estudo), o TCP/IP é o modelo real, implementado e utilizado por toda a internet hoje.

1. As Camadas do TCP/IP
O modelo TCP/IP é mais simplificado que o OSI. Dependendo do autor, ele é apresentado com 4 ou 5 camadas. A versão mais clássica e aceita possui 4 camadas:

Application (Aplicação): Aqui acontece tudo o que o usuário vê. Ela engloba as funções de Aplicação, Apresentação e Sessão do modelo OSI. (Ex: HTTP, DNS, SMTP).
Transport (Transporte): Responsável pela comunicação ponta a ponta e controle de fluxo. (Ex: TCP e UDP).
Internet (Internet): Responsável pelo endereçamento e roteamento dos pacotes através da rede. Equivale à camada de Rede do OSI. (Ex: IP).
Network Access (Acesso à Rede): Define como os dados são fisicamente enviados pelo meio. Ela engloba as camadas de Enlace e Física do OSI. (Ex: Ethernet, Wi-Fi).
2. O Encapsulamento (O conceito da "Matrioshka")
O encapsulamento é o processo onde cada camada "embrulha" os dados da camada superior com suas próprias informações (chamadas de Headers ou Cabeçalhos).

Imagine que você está enviando uma carta dentro de várias caixas:

Dados (Aplicação): Você escreve a mensagem. $\ Dado
Segmento (Transporte): Você coloca a mensagem em um envelope e escreve "Para a porta 80" (porta do servidor).  Segmento
Pacote (Internet): Você coloca esse envelope dentro de uma caixa maior e escreve o endereço IP de origem e destino.  Pacote
Quadro/Frame (Acesso à Rede): Você coloca a caixa dentro de um container de transporte e adiciona o endereço físico (MAC Address) da placa de rede.  Quadro
Bits (Física): O container é transformado em impulsos elétricos ou luz para viajar pelo cabo.  Bits
No destino, ocorre o "Desencapsulamento": O receptor abre cada "caixa" na ordem inversa até chegar à mensagem original.

3. Diferenças entre OSI e TCP/IP
Característica	Modelo OSI	Modelo TCP/IP
Natureza	Modelo Teórico / Referência	Modelo Prático / Implementação
Complexidade	Mais complexo (7 camadas)	Mais simples (4 ou 5 camadas)
Abordagem	Define rigorosamente o que cada camada faz	Foca nos protocolos que funcionam
Uso	Usado para ensino e diagnóstico	Usado para construir a Internet
Sessão/Apresentação	Tem camadas dedicadas para isso	Estas funções estão dentro da camada de Aplicação
4. Correlação: OSI  TCP/IP
Para você nunca mais esquecer, veja como as camadas se "fundem":

Camada OSI		Camada TCP/IP
7. Application		
6. Presentation		Application
5. Session		
4. Transport		Transport
3. Network		Internet
2. Data Link		
1. Physical		Network Access
Resumo final: Se alguém te perguntar a diferença, diga: "O OSI é o mapa detalhado de como a rede deveria ser; o TCP/IP é a estrada real que foi construída seguindo a lógica desse mapa, porém de forma mais simplificada."

Para entender os protocolos, primeiro você precisa entender o conceito de Portas.

Se o Endereço IP é o endereço do prédio, a Porta é a porta de entrada específica para cada serviço. Um servidor pode ter um único IP, mas ter várias "portas" abertas: a porta 80 para sites, a 25 para e-mails, a 22 para administração remota, e assim por diante.

Todos esses protocolos que você citou pertencem à Camada de Aplicação (do modelo OSI e TCP/IP).

Aqui está a explicação de cada um:

1. DNS - Domain Name System (Porta 53)
O DNS é a "lista telefônica" da internet. Os computadores se comunicam por números (IPs), mas humanos preferem nomes (como google.com).

O que faz: Traduz um nome de domínio (URL) em um endereço IP.
Exemplo: Você digita www.youtube.com  O DNS diz ao navegador: "O IP desse site é 142.250.xxx.xxx".
Analogia: Quando você procura "João" nos seus contatos e o celular disca o número do telefone dele.
2. DHCP - Dynamic Host Configuration Protocol (Portas 67 e 68)
O DHCP é o "recepcionista" da rede. Ele automatiza a configuração de rede dos dispositivos.

O que faz: Atribui automaticamente um endereço IP para cada aparelho que se conecta à rede (celular, notebook, smart TV). Sem ele, você teria que configurar o IP manualmente em cada dispositivo.
Exemplo: Quando você chega em um café e conecta no Wi-Fi, o DHCP te entrega um IP disponível na hora.
Analogia: Um recepcionista de hotel que te entrega a chave de um quarto disponível assim que você chega.
3. HTTP - Hypertext Transfer Protocol (Porta 80)
É a base da comunicação da Web.

O que faz: Transmite dados de páginas web (textos, imagens) do servidor para o seu navegador.
Observação: O HTTP é não criptografado. Qualquer pessoa no caminho pode "ler" o que está sendo enviado.
Analogia: Enviar um cartão-postal: qualquer pessoa que pegue o cartão no caminho consegue ler a mensagem.
4. HTTPS - HTTP Secure (Porta 443)
É a versão segura do HTTP.

O que faz: A mesma coisa que o HTTP, mas utiliza uma camada de criptografia (SSL/TLS). Os dados são embaralhados antes de serem enviados.
Exemplo: Sites de bancos, e-commerces e redes sociais usam HTTPS para proteger suas senhas.
Analogia: Enviar a mensagem dentro de um cofre blindado com senha.
5. FTP - File Transfer Protocol (Porta 21)
É o protocolo especializado em transferência de arquivos.

O que faz: Permite enviar (upload) e baixar (download) arquivos entre um cliente e um servidor.
Exemplo: Um desenvolvedor enviando os arquivos do site para o servidor de hospedagem.
Analogia: Um caminhão de mudança especializado em transportar caixas pesadas.
6. SSH - Secure Shell (Porta 22)
É o protocolo usado para acessar e administrar computadores remotamente de forma segura.

O que faz: Cria um canal criptografado para que um administrador possa digitar comandos em um servidor que está em outro país, por exemplo, como se estivesse sentado na frente dele.
Exemplo: Administradores de sistemas Linux usam o SSH para configurar servidores na nuvem (AWS, Azure, Google Cloud).
Analogia: Um túnel secreto e blindado que te leva direto para a sala de controle de um prédio.
7. SMTP - Simple Mail Transfer Protocol (Porta 25)
É o protocolo usado para o envio de e-mails.

O que faz: Leva o e-mail do seu computador (cliente) para o servidor de e-mail, e deste para o servidor do destinatário.
Atenção: O SMTP serve para enviar. Para receber (baixar) e-mails, usamos outros protocolos como POP3 ou IMAP.
Analogia: O carteiro que recolhe a carta na sua caixa de correio e a leva até a agência central.
Tabela Resumo para Memorização
Protocolo	Função Principal	Porta	Tipo de Dado
DNS	Traduz Nome  IP	53	Nomes de Domínio
DHCP	Entrega IPs automaticamente	67/68	Configurações de Rede
HTTP	Navegação Web (Simples)	80	Páginas Web (Texto/Img)
HTTPS	Navegação Web (Segura)	443	Páginas Web (Criptografadas)
FTP	Transferência de Arquivos	21	Arquivos / Pastas
SSH	Acesso Remoto Seguro	22	Comandos de Terminal
SMTP	Envio de E-mail	25	Mensagens de E-mail