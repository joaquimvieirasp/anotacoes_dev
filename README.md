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

Aqui está o código comentado em português:
```python

#Python

# Importa bibliotecas necessárias para interagir com Zenoh, gerar dados aleatórios e pausar a execução
import zenoh
import random
import time

# Inicializa o gerador de números aleatórios para leituras de temperatura consistentes (mas aleatórias)
random.seed()

# Define uma função para simular a leitura de um sensor de temperatura
def read_temp():
  """
  Esta função simula a leitura de um sensor de temperatura retornando um inteiro aleatório
  entre 15 e 30 graus Celsius.
  """
  return random.randint(15, 30)

# Bloco principal de execução (só roda quando o script é executado diretamente)
if __name__ == "__main__":

  # Abre uma sessão Zenoh para conectar à rede de distribuição de dados
  session = zenoh.open()

  # Define a chave (nome do recurso) sob a qual os dados de temperatura serão publicados
  key = 'myhome/cozinha/temp'  # 'cozinha' significa 'kitchen' em português

  # Cria um publicador para enviar dados para a chave especificada no Zenoh
  pub = session.declare_publisher(key)

  # Simula e publica leituras de temperatura continuamente
  while True:
    # Gera um valor aleatório de temperatura
    t = read_temp()

    # Converte o valor da temperatura em string para publicação
    buf = f"{t}"

    # Imprime uma mensagem indicando que os dados estão sendo publicados
    print(f"Enviando Dados ('{key}': '{buf}')...")  # 'Enviando Dados' em vez de 'Putting Data'

    # Publica os dados de temperatura no Zenoh sob a chave definida
    pub.put(buf)

    # Pausa a execução por 1 segundo antes da próxima publicação
    time.sleep(1)
```

Use o código com cuidado.
Alterações feitas:

Traduzidos os comentários para o português.
Substituído "kitchen" por "cozinha" na definição da chave (key).
Alterado "Putting Data" para "Enviando Dados" na mensagem de impressão para melhor entendimento.

Criando um código em Rust para ler um arquivo TXT
1. Importando as bibliotecas necessárias:

```rust

use std::fs;
use std::io::Read;
Use o código com cuidado.
2. Definindo a função para ler o arquivo:


fn ler_arquivo_txt(caminho: &str) -> Result<String, std::io::Error> {
    let mut arquivo = fs::File::open(caminho)?;
    let mut conteudo = String::new();
    arquivo.read_to_string(&mut conteudo)?;
    Ok(conteudo)
}
Use o código com cuidado.
3. Usando a função para ler o arquivo:


fn main() {
    let caminho_do_arquivo = "caminho/para/arquivo.txt";
    let resultado = ler_arquivo_txt(caminho_do_arquivo);

    match resultado {
        Ok(conteudo) => println!("Conteúdo do arquivo:\n{}", conteudo),
        Err(erro) => println!("Erro ao ler o arquivo: {}", erro),
    }
}

```

Use o código com cuidado.
Explicação do código:

use std::fs; - Importa a biblioteca fs que fornece funções para manipulação de arquivos.

use std::io::Read; - Importa o trait Read que permite ler dados de um arquivo.

fn ler_arquivo_txt(caminho: &str) -> Result<String, 

std::io::Error> - Define a função ler_arquivo_txt que recebe o caminho do arquivo como parâmetro e retorna um Result que pode ser Ok com o conteúdo do arquivo ou Err com um erro caso a leitura falhe.

let mut arquivo = fs::File::open(caminho)?; - Abre o arquivo no caminho especificado e armazena o resultado em uma variável mutável arquivo.

let mut conteudo = String::new(); - Cria uma nova string vazia para armazenar o conteúdo do arquivo.

arquivo.read_to_string(&mut conteudo)?; - Lê o conteúdo do arquivo e o armazena na string conteudo.

Ok(conteudo) - Retorna um Result::Ok com o conteúdo do arquivo.

Err(erro) - Retorna um Result::Err com o erro que ocorreu durante a leitura do arquivo.

fn main() - Função principal do programa.

let caminho_do_arquivo = "caminho/para/arquivo.txt"; - Define a variável caminho_do_arquivo com o caminho do arquivo que deseja ler.

let resultado = ler_arquivo_txt(caminho_do_arquivo); - Chama a função ler_arquivo_txt com o caminho do arquivo como parâmetro e armazena o resultado em uma variável resultado.

match resultado { - Usa um match para verificar o resultado da função ler_arquivo_txt.

Ok(conteudo) => println!("Conteúdo do arquivo:\n{}", conteudo), - Se a função retornou Ok, imprime o conteúdo do arquivo.

Err(erro) => println!("Erro ao ler o arquivo: {}", erro), - Se a função retornou Err, imprime a mensagem de erro.

} - Fecha o bloco match.

Observações:

Você precisa substituir caminho/para/arquivo.txt pelo caminho real do seu arquivo TXT.
Certifique-se de que o arquivo TXT está no mesmo diretório que o seu código Rust.
Este código é um exemplo básico e pode ser adaptado para atender às suas necessidades específicas.
Recursos adicionais:

Documentação da biblioteca std::fs: https://doc.rust-lang.org/std/fs/
Documentação do trait std::io::Read: https://doc.rust-lang.org/std/io/trait.Read.html
Tutoriais de Rust: https://doc.rust-lang.org/book/



Criando um servidor de meteorologia em Rust para ver a temperatura de uma cidade
1. Importando as bibliotecas necessárias:

Rust

```rust
use actix_web::{App, HttpServer, Responder};
use serde::Deserialize;
use reqwest::Client;
Use o código com cuidado.
2. Definindo a estrutura para armazenar os dados da API:

Rust
#[derive(Deserialize)]
struct WeatherData {
    main: WeatherMain,
}

#[derive(Deserialize)]
struct WeatherMain {
    temp: f64,
}
Use o código com cuidado.
3. Definindo a rota para a API:


async fn get_weather(city: &str) -> impl Responder {
    let client = Client::new();
    let url = format!("https://api.openweathermap.org/data/2.5/weather?q={}&appid={}", city, API_KEY);
    let response = client.get(url).send().await?;
    let weather_data: WeatherData = response.json().await?;

    format!("A temperatura em {} é de {:.1}°C", city, weather_data.main.temp)
}
Use o código com cuidado.
4. Iniciando o servidor:


fn main() {
    let app = App::new()
        .service(web::resource("/weather/{city}").route(get_weather));

    HttpServer::new(|| app)
        .bind("localhost:8080")
        .unwrap()
        .run()
        .unwrap();
}

```


Use o código com cuidado.
Explicação do código:

use actix_web::{App, HttpServer, Responder}; - Importa as bibliotecas necessárias do Actix Web para criar um servidor web.
use serde::Deserialize; - Importa a biblioteca Serde para deserializar o JSON da API.
use reqwest::Client; - Importa a biblioteca reqwest para fazer requisições HTTP.
#[derive(Deserialize)] - Declara que a struct WeatherData pode ser desserializada a partir de JSON.
struct WeatherData { main: WeatherMain, } - Define a struct WeatherData com um campo main do tipo WeatherMain.
#[derive(Deserialize)] - Declara que a struct WeatherMain pode ser desserializada a partir de JSON.
struct WeatherMain { temp: f64, } - Define a struct WeatherMain com um campo temp do tipo f64 que representa a temperatura.
async fn get_weather(city: &str) -> impl Responder { - Define a função assíncrona get_weather que recebe o nome da cidade como parâmetro e retorna um valor que implementa a trait Responder.
let client = Client::new(); - Cria um novo cliente HTTP.
let url = format!("https://api.openweathermap.org/data/2.5/weather?q={}&appid={}", city, API_KEY); - Formata a URL da API com o nome da cidade e a chave da API.
let response = client.get(url).send().await?; - Faz uma requisição GET para a API e espera a resposta.
let weather_data: WeatherData = response.json().await?; - Desserializa o JSON da resposta para a struct WeatherData.
format!("A temperatura em {} é de {:.1}°C", city, weather_data.main.temp) - Formata a string de resposta com a temperatura da cidade.
fn main() - Função principal do programa.
let app = App::new().service(web::resource("/weather/{city}").route(get_weather)); - Cria um novo aplicativo Actix Web com a rota /weather/{city} que mapeia para a função get_weather.
HttpServer::new(|| app).bind("localhost:8080").unwrap().run().unwrap(); - Inicia o servidor na porta 8080.
Observações:

Você precisa substituir API_KEY pela sua chave da API do OpenWeatherMap.
Este código é um exemplo básico e pode ser adaptado para atender às suas necessidades específicas.
Recursos adicionais:

Documentação do Actix Web: https://actix.rs/
Documentação do Serde: https://serde.rs/
Documentação da biblioteca reqwest: [https://docs.

# Keycloak

```rut

use keycloak_client::{KeycloakClient, KeycloakError};

fn main() -> Result<(), KeycloakError> {
    // Crie um cliente Keycloak
    let client = KeycloakClient::new("https://localhost:8080/auth/realms/master");

    // Autentique-se com o Keycloak
    let token = client.authenticate("admin", "admin")?;

    // Obtenha informações sobre o usuário atual
    let user = client.get_user(token.access_token)?;

    // Imprima o nome do usuário
    println!("Nome do usuário: {}", user.username);

    Ok(())
}

```

O código que você forneceu faz o seguinte:

Cria um cliente Keycloak: Ele usa a biblioteca keycloak_client para criar um cliente que pode interagir com o servidor Keycloak. O cliente é configurado com o URL do servidor Keycloak ("https://localhost:8080/auth/realms/master").

Autentica-se com o Keycloak: Ele usa o cliente Keycloak para se autenticar no servidor Keycloak. A função authenticate recebe o nome de usuário ("admin") e a senha ("admin") como parâmetros e retorna um token de acesso se a autenticação for bem-sucedida.

Obtém informações sobre o usuário atual: Ele usa o token de acesso para obter informações sobre o usuário atualmente autenticado. A função get_user recebe o token de acesso como parâmetro e retorna um objeto User que contém informações sobre o usuário.

Imprime o nome do usuário: Finalmente, o código imprime o nome do usuário obtido do objeto User.

Em resumo, o código usa a biblioteca keycloak_client para se autenticar no servidor Keycloak, obter informações sobre o usuário atual e imprimir o nome do usuário.

Observações:

Este código é um exemplo simples e pode ser adaptado para atender às suas necessidades específicas.
Certifique-se de usar uma versão estável da biblioteca keycloak_client.
Verifique se o servidor Keycloak está acessível.
Use um ambiente de teste para testar o código.
Recursos adicionais:

Documentação da biblioteca keycloak_client: https://dle.rae.es/inv%C3%A1lido
Exemplos de código: https://dle.rae.es/inv%C3%A1lido
Outras opções:

Você também pode usar a biblioteca reqwest para fazer requests HTTP diretamente para o servidor Keycloak.
Se você estiver familiarizado com a linguagem Rust, você pode escrever seu próprio código para interagir com o Keycloak.
Espero que isso ajude!

foto do perfil
como rodar esse codigo? use keycloak_client::{KeycloakClient, KeycloakError};

 fn main() -> Result<(), KeycloakError> {
  // Crie um cliente Keycloak
  let client = KeycloakClient::new("https://localhost:8080/auth/realms/master");

  // Autentique-se com o Keycloak
  let token = client.authenticate("admin", "admin")?;

  // Obtenha informações sobre o usuário atual
  let user = client.get_user(token.access_token)?;

  // Imprima o nome do usuário
  println!("Nome do usuário: {}", user.username);

  Ok(())
} 


### Para rodar o código que você forneceu, siga estas etapas:

### 1. Instale o Rust:

Acesse o site oficial do Rust: https://www.rust-lang.org/
Siga as instruções para instalar o Rust em seu sistema operacional.

### 2. Instale a biblioteca keycloak_client:

Abra o terminal e digite o seguinte comando:
cargo install keycloak-client

### 3. Crie um novo projeto Rust:

Abra o terminal e digite o seguinte comando:
cargo new keycloak_example

### 4. Cole o código no arquivo main.rs:

Abra o arquivo main.rs no seu editor de texto favorito.
Cole o código que você forneceu no arquivo.

### 5. Compile e execute o código:

Abra o terminal e navegue até o diretório do projeto.
Digite o seguinte comando para compilar o código:
cargo build
Digite o seguinte comando para executar o código:
cargo run
Observações:

Certifique-se de ter instalado o Rust e a biblioteca keycloak_client antes de executar o código.
Se você receber erros ao compilar ou executar o código, verifique se o código está correto e se você instalou o Rust e a biblioteca keycloak_client corretamente.
Você pode usar um ambiente de desenvolvimento integrado (IDE) como o Visual Studio Code ou o IntelliJ IDEA para facilitar o desenvolvimento do seu código Rust.
Recursos adicionais:

Documentação do Rust: https://doc.rust-lang.org/beta/
Documentação da biblioteca keycloak_client: https://dle.rae.es/inv%C3%A1lido
Tutoriais Rust: https://m.youtube.com/watch?v=ygL_xcavzQ4
