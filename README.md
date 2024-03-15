# Anotacoes_dev
# Anotações de desenvovimento
# Node
Instalar node com nvm (node version manager)
Instalar o node com o nvm é possível trocar de versão a qualquer momento, é possível setar uma versão do node globalamente na máquina ou instalar um versão do node somente em um projeto expecífico.
Comandos:

Installing and Updating
Install & Update Script
To install or update nvm, you should run the install script. To do that, you may either download and run the script manually, or use the following cURL or Wget command:

wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash 

Depois de instalado o nvm, pode instalar o node da seguinte forma:
	- nvm install node        => esse comando instala a última versão do node.js
	- node -v                 => confirma a versão do node instalada.
	- nvm use global 18.17    => esse comando instala uma versão global expecífica do node, nesse caso a versão 18.17 é a latest.
	- nvm alias default 18.17 => define uma versão default para o computador
	- nvm use default         => depois de usar o comando acima (nvm alias default 18.17) quando usar o comando nvm default, ele instala a versão do alias.
	- nvm use 19              => esse comando troca a versão do node, basta escolher a versão, e pra voltar para a versão default basa
# Rust
Instalar o script de instalação do Rust, usando o curl.
Esse script baixa e instala o rust.

Comandos: 

	sudo curl https://sh.rustup.rs -sSf | sh => baixa e instala o rust.
	rustc -V => mostra a versão instalada do rust.
	cargo -V => mostra a versão do gerenciador de pacotes do rust (cargo).
	rustup self uninstall => desintala o rust do computador.
	
Fonte: https://www.youtube.com/watch?v=eTaaegF0AgQ	(Bóson Treinamentos)

Se o sistema for novo ou formatado rescentemente ou nunca foi feito um instalação para desenvovimento de software, provavelemte não tenha o compilador adequado para rodar os códigos.
Para evitar problemas vamos instalar um pacote de compilação essencial com o comando:

	sudo apt install build-essential

Testando o rust, criando um programa de teste.

	Usando o nano:
	
	nano primeiroProgramaRust.rs
	Quando o nano abrir, digitar o seguinte código:
	
	fn main() {
		println!("Criando o primeiro código em rust");
		}
		
Salve o código com o comando ctrl+o depois feche o nano com o comando ctrl+x.
Agora para verificar o código que criamos digitamos ls na pasta onde salvamos o script do rust, assim vai aparecer nosso código.
Para compliar nosso programa em rust usamos o comando:
	rustc + nome no nosso programa, no caso aqui seria primeiroProgramaRust.rs
	Então ficaria rustc primeiroProgramaRust.rs
	Se tudo estiver certo o terminal naõ vai retornar nada, se tiver algo errado ele vai mostrar alguma mensagem de erro.
	Agora se dermos um ls o terminal vai mostrar nos código como um programa executavél.
	Para rodar o programa, basta digitar ./primeiroProgramaRust e o terminal vai retornar a mensangem que colocamos dentro do println (Criando o primeiro código)
	
Criar um projeto utilizando o cargo:

fonte: https://www.youtube.com/watch?v=Pifhr4-5V1w&list=PLucm8g_ezqNr29-gbyyGIhStUBng-YTW2&index=2

Dentro da sua pasta, use o comando cargo new + o nome do seu projeto, ex: cargo new projeto_rust
Após dar enter, será criado seu projeto, um projeto binário, com um arquivo Cargo.toml e uma pasta src.
Segundo passo:
	- com o projeto criado, precisamos compilar nosso projeto, para isso usamos, cargo build
	- em seguida para rodar nosso projeto depois de compilar, basta usar o comando cargo run
	
	
	Extenções para Rust:
	 - CodeLLDB -> debugger para rust 
	
# Systemctl 
	
Corrigindo o erro "System has not been booted with systemd as init system"
Se você está seguindo algum tutorial na internet e usou o comando systemd como sudo systemctl start.

Para sua surpresa, o comando resulta em um erro como este:

System has not been booted with systemd as init system (PID 1). Can't operate.

Razão: Seu sistema Linux não está usando o systemd

O motivo é que você está tentando usar o comando systemd para gerenciar serviços no Linux, mas seu sistema não usa systemd e (provavelmente) usa o sistema SysV init (sysvinit) clássico.

Mas como isso é possível? Você está usando o Ubuntu e o tutorial também é para a mesma versão do Ubuntu. Como é que não está funcionando para você?

Se você estiver usando o Ubuntu dentro do Windows usando WSL, terá SysV em vez de systemd e seu sistema reclamará quando você executar o comando systemctl (destinado a sistemas Linux com sistema init systemd).

Como saber qual sistema init você está usando? Você pode usar este comando para saber o nome do processo associado ao PID 1 (o primeiro processo executado em seu sistema):

ps -p 1 -o comm=

Deve mostrar init ou sysv (ou algo parecido) na saída. Se você vir init, seu sistema não está usando systemd e você deve usar os comandos init conforme explicado na próxima seção.

Como corrigir o erro 'O sistema não foi inicializado com o systemd'?
A resposta simples é não usar o comando systemctl. Em vez disso, use o comando sysvinit equivalente.

Não é muito complicado e ambos os comandos têm uma sintaxe um tanto semelhante.

Esta tabela deve ajudá-lo.

Comando Systemd						Comando Sysvinit
systemctl start service_name		service service_name start
systemctl stop service_name			service service_name stop
systemctl restart service_name		service service_name restart
systemctl status service_name		service service_name status
systemctl enable service_name		chkconfig service_name on
systemctl disable service_name		chkconfig service_name off

Seja qual for o tutorial que você está seguindo, tente usar os comandos equivalentes e você não verá a mensagem "O sistema não foi inicializado com o systemd como sistema init (PID 1). Não é possível operar".

 Fonte: https://linuxhandbook.com/system-has-not-been-booted-with-systemd/

# Github

Comandos pelo terminal:
 
Na raiz do projeto, seguir o seguintes passos;

git init

git remote add origin + https://github.com/joaquimvieirasp/treinamento_rust2024.git

git add .

git commit -m "mensagem do commit"

git push

# Github - Subir código em um repositório já exitente

git init

git add .

git commit -m "msg do commit"

git remote add origin + https://github.com/joaquimvieirasp/treinamento_rust2024.git (exemplo) (precisa digitar usuário e senha)

git push

<img width="875" alt="image" src="https://github.com/joaquimvieirasp/anotacoes_dev/assets/77693436/a9c384b0-ae78-4360-8209-ae82c065bdb8">


fonte: https://www.youtube.com/watch?v=aINs3ouaoJk

# Github - Criar uma branch

git checkout -b + nome da branch a ser criada 

_esse comando cria uma nova branch e já muda pra ela_

# Postgres

Principais comandos para acessar o postgres:

sudo -u postgres psql postgres - entra no postgres

\q - sair do postgres

criar senha para o usuario padrão do postgres

\password postgres

Instalar o pacote ADMIN PACK do Postgres ( instala algumas ferramentas adicionais para administração do banco)

 CREATE EXTENSION adminpack;
 
 Criar um usuário especifico no postgres
 
 sudo -u postgres createuser -D -A -P joaquim
 
# Instalação Podman

Instalando o Podman no Debian 12
Opção 1: Usando o repositório oficial:

Atualize a lista de pacotes:
sudo apt update
Instale o Podman e seus pacotes de dependência:
sudo apt install podman
Opção 2: Instalando a versão mais recente:

Adicione o repositório Podman:
echo "deb https://download.opensuse.org/repositories/devel:/podman/Debian_12/ /" | sudo tee /etc/apt/sources.list.d/devel:podman.list

Importe a chave GPG do repositório:
sudo wget -q https://download.opensuse.org/repositories/devel:/podman/Debian_12/Release.key -O- | sudo apt-key add -

Atualize a lista de pacotes e instale o Podman:
sudo apt update
sudo apt install podman

Verificação da instalação:
podman --version

Opções adicionais:

Podman Compose:
sudo apt install podman-compose

Buildah:
sudo apt install buildah

Recursos:

Documentação oficial do Podman: https://podman.io/
Guia de instalação do Podman no Debian: [URL inválido removido]
Observações:

A versão do Podman no repositório oficial do Debian pode ser mais antiga que a versão disponível no repositório OpenSUSE.
Certifique-se de escolher a opção de instalação mais adequada para suas necessidades.
Exemplo de uso:

podman run hello-world
Este comando executará a imagem "hello-world" do Docker Hub.

Dica:

Para mais informações sobre como usar o Podman, consulte a documentação oficial ou utilize o comando podman --help

# Testando o Podman
1. Verificando a versão:

podman --version
2. Executando um container simples:

podman run hello-world
Este comando executará a imagem "hello-world" do Docker Hub e imprimirá a mensagem "Hello from Docker!".

3. Executando um container com comandos:

podman run -it --rm alpine sh
Este comando executará a imagem "alpine" e abrirá um shell interativo dentro do container. Você pode executar comandos dentro do container e sair com o comando exit.

4. Criando e executando um container a partir de um Dockerfile:

# Crie um Dockerfile chamado "Dockerfile" com o seguinte conteúdo:
FROM alpine

RUN echo "Hello from my container!"

CMD ["echo", "Hello from my container!"]

# Construa a imagem
podman build -t my-image .

# Execute a imagem
podman run my-image
Este comando criará uma imagem chamada "my-image" a partir do Dockerfile, e executará a imagem, imprimindo a mensagem "Hello from my container!".

5. Testando comandos Podman:

podman images: Lista as imagens disponíveis.
podman ps: Lista os containers em execução.
podman run: Executa um container.
podman build: Constrói uma imagem a partir de um Dockerfile.
podman inspect: Mostra informações sobre um container.
podman rm: Remove um container.
Recursos adicionais:

Documentação oficial do Podman: https://es.wiktionary.org/wiki/removido
Tutoriais do Podman: https://es.wiktionary.org/wiki/removido
Exemplos de uso do Podman: https://es.wiktionary.org/wiki/removido
Observações:

Certifique-se de ter o Podman instalado antes de executar os comandos.
Utilize o comando podman --help para obter mais informações sobre cada comando.
Dicas:

Experimente executar diferentes comandos para se familiarizar com o Podman.
Utilize o Docker Hub para encontrar imagens que você pode usar para testar o Podman.
Consulte a documentação oficial para obter mais informações sobre como usar o Podman.






