# Medusa-Attack PT/BR
Minha tentativa de ataque usando medusa no kali linux.

É importante destacar que todas as ações praticadas no desenvolvimento deste código foram, exclusivamente, para fins didáticos na aplicação do conteúdo ministrado.
Após assistir as aulas da prof. Isadora Ferrão sobre Brute Force, Medusa, Password-spraying como forma de consolidar as informações transmitidas, fui praticar seguindo todas as orientações e cuidados necessários para tal.

Baixei o arquivo do sistema Metaesploitable2 juntamente com a imagem ISO do Kali Linux, feitas as instalações e configurações, iniciei o uso dessas ferramentas.

Ao iniciar o terminal no Meta com o seu login e senha convencional: login: msfadmin e senha: msfadmin, busquei qual o endereço de IP daquela VM que retornou um com final 103.

Com esse IP, abri no Kali o terminal e iniciei um scan com o nmap, durante essa etapa foi descoberto que as portas udp 2049, 111 estavam abertas sendo elas responsáveis pelo serviço de NFS ou Network File System, para compartilhamento de arquivos, descobri que a porta 53 também estava aberta, essa é a porta padrão para protocolo de nomes de dominio (DNS), sendo usada para traduzir os dominhios em endereços de IP, adicionalmente encontrou-se uma abertura na porta 137 de NetBios, permitindo a descoberta de computadores e recursos, possuindo funções semelhantes ao DNS.

Com tais fragilidades escaneadas, fui enumerar tais aberturas para verificar se realmente estavam abertas e qual a versão dos serviços instalados. Se tais falhas estivessem presentes em um IP real, ele estaria exposto a uma série de ataques e interações, principalmente no root, sabe-se que no caso do no-root-smash estar ativado o atacante poderia criar um script e executa-lo concedendo acesso de administrador e escalando provilégios dentro da rede.

Após encontrar tais vulnerabilidades, foquei nas portas onde seriam solicitadas uma forma de autenticação como a ftp, ssh, http. Criei uma wordlist com usernames e passwords, que compartilhei no repositório.

Como forma de isolar a porta alvo do ataque, realizei um novo scan, dessa vez especifico para a porta 21 (ftp) e na sequência a sua enumeração para determinar a versão do serviço.

Diante da resposta, utilizei o Medusa para iniciar o ataque unindo as duas wordlists no prompt, defini uma threat de 20 simultaneamente, gerando resultado positivo.

Para confirmar que foi descoberto o login e senha para acesso, tentei conectar na porta ftp com o login e senha tidos como certos, recebi a mensagem de login sucessful. 

Conexão estabelecida usando o Brute Force.

# Medusa-Attack EN

My attempt at an attack using Medusa on Kali Linux.

It is important to emphasize that all actions performed in the development of this code were exclusively for **didactic purposes** in the application of the content taught. After watching the classes given by Prof. Isadora Ferrão on Brute Force, Medusa, and Password Spraying as a way to consolidate the information transmitted, I proceeded to practice, following all the necessary guidelines and precautions.

I downloaded the **Metaesploitable2 system file** along with the **Kali Linux ISO image**. After installations and configurations were complete, I began to use these tools.

Upon starting the terminal in Meta with its conventional login and password: **login: `msfadmin` and password: `msfadmin`**, I searched for the IP address of that VM, which returned one ending in **103**.

With this IP, I opened the terminal in Kali and initiated a scan with **nmap**. During this stage, it was discovered that **UDP ports 2049 and 111** were open, which are responsible for the **NFS (Network File System)** service for file sharing. I also discovered that **port 53** was open; this is the standard port for the **DNS (Domain Name System)** protocol, used to translate domains into IP addresses. Additionally, an opening was found on **port 137 (NetBios)**, which allows for the discovery of computers and resources and has functions similar to DNS.

With these weaknesses scanned, I went on to enumerate these openings to verify if they were truly open and what version of the installed services they were running. If such flaws were present on a real IP, it would be exposed to a series of attacks and interactions, especially on the root. It is known that if **no-root-squash** is activated, an attacker could create a script and execute it, granting administrator access and escalating privileges within the network.

After finding these vulnerabilities, I focused on the ports that would require some form of authentication, such as **FTP, SSH, and HTTP**. I created a wordlist with usernames and passwords, which I shared in the repository.

To isolate the target attack port, I performed a new scan, this time specific to **port 21 (FTP)**, and subsequently, its enumeration to determine the service version.

Based on the response, I used **Medusa** to start the attack, combining the two wordlists in the prompt, and set a **thread count of 20** simultaneously, which generated a **positive result**.

To confirm that the login and password for access were discovered, I attempted to connect to the FTP port with the supposedly correct login and password, and I received the **"login successful"** message.

**Connection established using Brute Force.**
