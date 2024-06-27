# Anotacoes_dev
# Anotações de desenvovimento
# Vue
Para corrigir o uso do v-for com a diretiva v-bind:key, você deve atribuir uma chave única para cada elemento gerado pelo loop v-for. Isso é importante para o Vue.js poder identificar cada elemento de forma eficiente e realizar atualizações no DOM de maneira adequada.

Aqui está como você pode corrigir a função:

```vue

<template>
    <ul>
        <li v-for="(nome, index) in nomes" :key="index">{{ nome }}</li>
    </ul>
</template>
```
Neste exemplo:

v-for="(nome, index) in nomes" itera sobre o array nomes, onde nome é o valor do elemento atual e index é o índice desse elemento no array.
:key="index" atribui index como a chave única para cada <li> gerado pelo loop v-for. Usar o índice como chave é uma abordagem comum quando os itens em nomes não têm uma propriedade única identificável por chave.
No entanto, se os itens em nomes possuem uma propriedade única (como um ID) que pode ser usada como chave, é preferível usar essa propriedade em vez do índice. Por exemplo:

```vue

<template>
    <ul>
        <li v-for="nome in nomes" :key="nome.id">{{ nome }}</li>
    </ul>
</template>
```
Neste caso, assumimos que cada objeto nome dentro de nomes possui uma propriedade id que é única. É sempre melhor usar uma chave única e estável sempre que possível, para garantir um desempenho ideal e evitar problemas potenciais com a renderização e a reatividade no Vue.js.

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

Comando Systemd				Comando Sysvinit

systemctl start service_name		service service_name start

systemctl stop service_name             service service_name stop

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

# Atualizar a URL do repositório remoto:
Se o repositório foi renomeado ou movido para uma nova localização, você precisará atualizar o URL do repositório remoto no seu ambiente local. Para fazer isso, use o seguinte comando no terminal (substituindo o URL pelo novo URL, se aplicável):
![image](https://github.com/joaquimvieirasp/anotacoes_dev/assets/77693436/c920921d-880a-4867-9062-286c3a30f29b)

bash
Copiar código
```git

git remote set-url origin https://github.com/novo-usuario/novo-repositorio.git

```

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

 Crie um Dockerfile chamado "Dockerfile" com o seguinte conteúdo:
FROM alpine

RUN echo "Hello from my container!"

CMD ["echo", "Hello from my container!"]

 Construa a imagem
podman build -t my-image .

 Execute a imagem
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

```rust

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



# Animações básicas na linha de comando com Rust

### Existem diversas maneiras de criar animações na linha de comando com Rust. Aqui estão algumas opções:

1. Usando o módulo crossterm:

O módulo crossterm fornece APIs para controlar o cursor, limpar a tela e outras funcionalidades úteis para criar animações simples.

Exemplo:

```rust
// Rust
use crossterm::{cursor, terminal};

fn main() {
    let mut stdout = terminal::stdout();

    for i in 0..10 {
        cursor::move_to(&mut stdout, (i, 0)).unwrap();
        stdout.write(b"█").unwrap();
        std::thread::sleep(std::time::Duration::from_millis(100));
    }

    cursor::show(&mut stdout).unwrap();
}

```
Este código cria uma barra de progresso simples que se move da esquerda para a direita na tela.

2. Usando o módulo tui:

O módulo tui fornece uma biblioteca gráfica de alto nível para criar interfaces de usuário na linha de comando.

Exemplo:

```rust

use tui::{
    backend::CrosstermBackend,
    layout::{Constraint, Direction, Layout},
    style::{Color, Modifier, Style},
    text::{Span, Text},
    widgets::{Block, Borders, Gauge},
    Frame, Terminal,
};

fn main() {
    let mut terminal = Terminal::new(CrosstermBackend::new()).unwrap();
    terminal.clear().unwrap();

    let gauge = Gauge::default()
        .block(Block::default().title("Carregando..."))
        .borders(Borders::ALL)
        .style(Style::default().fg(Color::Red).modifier(Modifier::BOLD));

    let layout = Layout::default()
        .direction(Direction::Horizontal)
        .constraints([Constraint::Percentage(80), Constraint::Length(10)])
        .margin(1)
        .split(gauge);

    let mut frame = Frame::new(terminal, layout);

    for i in 0..100 {
        frame.render(&mut terminal).unwrap();
        gauge.set_ratio(i as f64 / 100.0);
        std::thread::sleep(std::time::Duration::from_millis(10));
    }

    frame.set_text(
        Text::raw("Concluído!").style(Style::default().fg(Color::Green)),
    );
    frame.render(&mut terminal).unwrap();
}

```

Este código cria um indicador de carregamento que aumenta de 0% a 100%.

3. Usando o módulo ggez:

O módulo ggez fornece uma biblioteca gráfica 2D completa para criar jogos e outras aplicações com animações complexas.

Exemplo:

```rust

use ggez::{
    conf,
    event::{self, Event},
    graphics::{self, Color, DrawParam},
    Context, GameResult,
};

fn main() -> GameResult {
    let (ctx, event_loop) = &mut conf::Conf::new().init()?;

    let mut circle = graphics::Mesh::new_circle(
        &ctx,
        graphics::DrawMode::fill(),
        (0.0, 0.0),
        100.0,
        1.0,
        Color::WHITE,
    )?;

    let mut rotation = 0.0;

    event::run(ctx, event_loop, move |ctx, event| {
        match event {
            Event::Quit(_) => true,
            Event::Update(_) => {
                rotation += 0.01;
                circle.set_rotation(rotation);

                graphics::clear(ctx, Color::BLACK);
                graphics::draw(ctx, &circle, DrawParam::new());
                graphics::present(ctx)?;
            }
            _ => false,
        }
    })
}

```

Este código cria uma animação de um círculo girando na tela.

Recursos adicionais:

Documentação do módulo crossterm: https://docs.rs/crossterm/
Documentação do módulo tui: https://docs.rs/tui/
Documentação do módulo ggez: https://docs.rs/ggez/
[Tutoriais de animações na linha de comando com Rust](https://doc.rust-lang.org/book/ch19-00-advanced-features.html

# Servidor de mapas em Rust

como criar um servidor de mapas em rust usando o leaflet?
ChatGPT
Para criar um servidor de mapas em Rust usando Leaflet, você pode seguir estas etapas básicas:

Escolha de Framework Web em Rust: Você pode usar frameworks como Rocket ou Actix para criar um servidor web em Rust.

Instale as dependências necessárias: No seu arquivo Cargo.toml, você precisará adicionar as dependências necessárias para o servidor web e para o Leaflet, juntamente com outras dependências que você possa precisar.

Crie o Servidor Web: Use o framework web escolhido para configurar rotas para servir seus arquivos estáticos e lidar com solicitações dos clientes.

Prepare os Arquivos Estáticos: Isso inclui HTML, JavaScript e CSS necessários para renderizar o mapa Leaflet no navegador do cliente. Certifique-se de incluir a biblioteca Leaflet neste passo.

Configure a Integração com Leaflet: No seu código JavaScript, você precisa configurar o Leaflet para exibir o mapa desejado. Isso envolve a definição da localização inicial do mapa, a adição de camadas de mapa e quaisquer marcadores ou outras sobreposições desejadas.

Aqui está um exemplo básico de como você pode estruturar seu projeto:

plaintext
Copy code
meu_projeto/
  |- Cargo.toml
  |- src/
      |- main.rs
  |- static/
      |- index.html
      |- script.js
      |- style.css
Um exemplo básico de Cargo.toml pode ser:

```rust

toml

[package]
name = "meu_projeto"
version = "0.1.0"
edition = "2018"

[dependencies]
actix-web = "4.0"
Um exemplo básico de main.rs usando Actix pode ser:

```


```rust

use actix_web::{web, App, HttpResponse, HttpServer, Responder, Result};
use std::fs::File;
use std::io::Read;

async fn index() -> Result<HttpResponse> {
    Ok(HttpResponse::Ok()
        .content_type("text/html")
        .body(get_file_content("static/index.html")?))
}

async fn get_static_file(path: web::Path<String>) -> impl Responder {
    let file_path = format!("static/{}", path);
    HttpResponse::Ok().body(get_file_content(&file_path).unwrap_or_else(|_| "".to_string()))
}

fn get_file_content(file_path: &str) -> std::io::Result<String> {
    let mut file = File::open(file_path)?;
    let mut contents = String::new();
    file.read_to_string(&mut contents)?;
    Ok(contents)
}

#[actix_web::main]
async fn main() -> std::io::Result<()> {
    HttpServer::new(|| {
        App::new()
            .route("/", web::get().to(index))
            .route("/{file:.*}", web::get().to(get_static_file))
    })
    .bind("127.0.0.1:8080")?
    .run()
    .await
}

````

No exemplo acima, index() serve o arquivo index.html e get_static_file() serve arquivos estáticos como JavaScript e CSS.

Você precisará ajustar o código acima para incluir a configuração específica do Leaflet e seus mapas. Certifique-se de incluir o script do Leaflet no seu arquivo HTML e configurá-lo conforme necessário.

User
onde esta o arquivo javascript?
ChatGPT
Peço desculpas pela omissão do arquivo JavaScript no exemplo anterior. Vou ajustar o exemplo para incluir o arquivo JavaScript e a configuração do Leaflet.

Aqui está a estrutura atualizada do projeto:

plaintext
Copy code
meu_projeto/
  |- Cargo.toml
  |- src/
      |- main.rs
  |- static/
      |- index.html
      |- script.js
      |- style.css
E aqui está um exemplo básico de index.html:

```html

html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mapa com Leaflet</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        #map {
            height: 400px;
            width: 100%;
        }
    </style>
</head>
<body>
    <div id="map"></div>
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script src="script.js"></script>
</body>
</html>

```

E o conteúdo básico de script.js:

```javascript

javascript

var map = L.map('map').setView([51.505, -0.09], 13);
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

```

O arquivo script.js contém a configuração básica do Leaflet, que cria um mapa usando dados do OpenStreetMap. Certifique-se de ajustar conforme necessário para atender às suas necessidades específicas de mapa.

Com essa estrutura e configuração básica, você deve ser capaz de iniciar um servidor web em Rust que serve o arquivo HTML e o arquivo JavaScript estático, permitindo que você visualize um mapa Leaflet no navegador.

User
o arquivo javascript precisa estar no mesmo diretório que o arquivo main.rs?
ChatGPT
Não necessariamente. O arquivo JavaScript pode estar em qualquer lugar dentro da sua estrutura de projeto. No exemplo que forneci, o arquivo JavaScript script.js está localizado dentro do diretório static/. O importante é garantir que o servidor web consiga servir esse arquivo estático quando uma solicitação for feita.

No exemplo atualizado que forneci, quando uma solicitação é feita para qualquer URL que corresponda a um arquivo estático (por exemplo, http://localhost:8080/script.js), a função get_static_file() será chamada e tentará encontrar e servir o arquivo solicitado.

Portanto, se você preferir manter o arquivo JavaScript em um diretório diferente, como src/, por exemplo, basta ajustar o caminho no arquivo HTML para corresponder ao novo local:

html
Copy code
<script src="../src/script.js"></script>
E também atualize a função get_static_file() para procurar no caminho correto:

rust
Copy code
async fn get_static_file(path: web::Path<String>) -> impl Responder {
    let file_path = format!("src/{}", path);
    HttpResponse::Ok().body(get_file_content(&file_path).unwrap_or_else(|_| "".to_string()))
}
Com essas mudanças, seu servidor web Rust continuará a servir o arquivo JavaScript corretamente, independentemente de onde ele esteja localizado dentro do seu projeto.

No exemplo fornecido, o arquivo Rust (main.rs) contém o código para criar um servidor web usando o framework Actix-web. Aqui está a função principal desse arquivo:

Criação do Servidor Web: O arquivo main.rs define um servidor web usando o framework Actix-web. Ele configura rotas para servir arquivos estáticos, como o arquivo HTML, JavaScript e CSS necessários para exibir o mapa Leaflet no navegador.

Manuseio de Solicitações: O servidor web é configurado para lidar com solicitações HTTP, incluindo aquelas para o arquivo HTML principal (index.html) e para outros arquivos estáticos, como JavaScript e CSS. Ele responde a essas solicitações servindo os arquivos correspondentes.

Configuração do Roteamento: O código define rotas para responder a diferentes tipos de solicitações. Por exemplo, a rota / é configurada para servir o arquivo HTML principal, enquanto outras rotas são configuradas para servir arquivos estáticos específicos.

Funções Auxiliares: O código também inclui funções auxiliares, como get_static_file(), que são usadas para ler e servir arquivos estáticos.

Em resumo, o arquivo Rust (main.rs) funciona como o ponto de entrada do servidor web e contém a lógica necessária para configurar e iniciar o servidor, bem como para lidar com solicitações HTTP e servir arquivos estáticos.

### Marcador para Vila Olimpia 

```javascript

var map = L.map('map').setView([-23.5917, -46.6850], 15);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

var vilaOlimpiaMarker = L.marker([-23.5917, -46.6850]).addTo(map);
vilaOlimpiaMarker.bindPopup("<b>Vila Olímpia</b>").openPopup();

```

### Marcador para Parque Paulistano 

```javascript

// Adiciona marcador para o bairro Parque Paulistano
var parquePaulistanoMarker = L.marker([/* coordenadas do Parque Paulistano */]).addTo(map);
parquePaulistanoMarker.bindPopup("<b>Parque Paulistano</b>").openPopup();

```

Neste exemplo, as coordenadas [-23.5917, -46.6850] representam a localização aproximada da Vila Olímpia em São Paulo. Um marcador é adicionado a essas coordenadas no mapa Leaflet, e um balão de informações com o texto "Vila Olímpia" é vinculado a esse marcador.

Atualize a Página HTML: Certifique-se de que o arquivo HTML (index.html) esteja referenciando corretamente o arquivo script.js.
Depois de fazer esses ajustes e recarregar a página no navegador, você deve ver o mapa Leaflet com um marcador indicando a localização da Vila Olímpia em São Paulo. O balão de informações "Vila Olímpia" deve ser exibido quando você clicar no marcador. Certifique-se de ajustar as coordenadas para refletir a localização precisa da Vila Olímpia.

### Obter temperatura atual da regiao

Como mostrar a temperatura atual da cidade de São paulo e Vila olimpia

Para exibir a temperatura atual da cidade de São Paulo e da Vila Olímpia, você precisará usar uma API de previsão do tempo para obter os dados de temperatura atual para essas localidades e, em seguida, exibir esses dados no seu aplicativo. Uma API comum usada para isso é a OpenWeatherMap.

Aqui está uma abordagem básica de como você pode fazer isso:

Obter Chave da API: Primeiro, você precisa se inscrever no serviço da OpenWeatherMap para obter uma chave de API.

Fazer Requisições à API: Você usará a chave de API para fazer requisições à API da OpenWeatherMap para obter os dados de temperatura atual para a cidade de São Paulo e a Vila Olímpia.

Exibir Dados no Seu Aplicativo: Após receber os dados da API, você pode exibir a temperatura atual no seu aplicativo, por exemplo, ao lado dos marcadores no mapa Leaflet.

Aqui está um exemplo de como você pode fazer isso usando JavaScript para fazer as requisições à API da OpenWeatherMap e exibir os dados no mapa Leaflet:

```javascript

var map = L.map('map').setView([-23.5505, -46.6333], 12);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

// Adiciona marcador para a cidade de São Paulo
var saoPauloMarker = L.marker([-23.5505, -46.6333]).addTo(map);
saoPauloMarker.bindPopup("<b>São Paulo</b>").openPopup();

// Adiciona marcador para a Vila Olímpia
var vilaOlimpiaMarker = L.marker([-23.5917, -46.6850]).addTo(map);
vilaOlimpiaMarker.bindPopup("<b>Vila Olímpia</b>").openPopup();

// Função para obter a temperatura atual
function getTemperature(lat, lon, marker) {
    var apiKey = 'SUA_CHAVE_DE_API';
    var apiUrl = 'https://api.openweathermap.org/data/2.5/weather?lat=' + lat + '&lon=' + lon + '&units=metric&appid=' + apiKey;

    fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
            var temperature = data.main.temp;
            console.log("Temperatura atual:", temperature + "°C");
            // Exibe a temperatura ao lado do marcador no mapa Leaflet
            marker.bindPopup("Temperatura: " + temperature + "°C").openPopup();
        })
        .catch(error => console.log("Erro ao obter temperatura:", error));
}

// Obtém e exibe a temperatura para São Paulo
getTemperature(-23.5505, -46.6333, saoPauloMarker);

// Obtém e exibe a temperatura para a Vila Olímpia
getTemperature(-23.5917, -46.6850, vilaOlimpiaMarker);


```

### Integração com Keycloak

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicativo Protegido pelo Keycloak</title>
</head>
<body>
    <h1>Aplicativo Protegido pelo Keycloak</h1>
    
    <script src="https://cdn.keycloak.org/12.0.4/keycloak.js"></script>
    <script>
        var keycloak = Keycloak({
            url: 'URL_DO_KEYCLOAK',
            realm: 'NOME_DO_REALM',
            clientId: 'NOME_DO_CLIENTE'
        });

        keycloak.init({ onLoad: 'login-required' }).then(function(authenticated) {
            if (authenticated) {
                console.log('Usuário autenticado');
                // Aqui você pode adicionar o código para exibir o conteúdo protegido pelo Keycloak
            } else {
                console.log('Falha na autenticação');
            }
        }).catch(function() {
            console.log('Erro ao inicializar o Keycloak');
        });
    </script>
</body>
</html>

```

Aqui estão os passos básicos para usar o Keycloak em seu aplicativo da web:

Configuração do Realm no Keycloak: Primeiro, você precisa configurar um Realm no Keycloak e definir as configurações de clientes e usuários. Você precisará criar um cliente no Keycloak para representar seu aplicativo da web.

Configuração do Cliente no Aplicativo: No lado do seu aplicativo da web, você precisa configurar o cliente Keycloak para autenticação. Isso geralmente envolve incluir o adaptador Keycloak para JavaScript em seu código e configurá-lo para se comunicar com o servidor Keycloak.

Autenticação do Usuário: Ao acessar o aplicativo da web, os usuários serão redirecionados para o servidor Keycloak para autenticação. Depois de fazer login com sucesso, eles serão redirecionados de volta para o seu aplicativo da web com um token de acesso.

Autorização e Proteção de Recursos: Você pode usar os tokens de acesso recebidos do Keycloak para proteger recursos em seu aplicativo da web. Isso envolve verificar os tokens de acesso recebidos do Keycloak para garantir que os usuários tenham permissão para acessar determinados recursos.

Aqui está um exemplo básico de como você pode configurar o Keycloak em seu aplicativo da web usando JavaScript:

Certifique-se de substituir 'URL_DO_KEYCLOAK', 'NOME_DO_REALM' e 'NOME_DO_CLIENTE' pelos valores correspondentes da sua configuração do Keycloak.

Este é um exemplo básico para começar. Dependendo das suas necessidades específicas e do fluxo de autenticação que você deseja usar (por exemplo, OpenID Connect, OAuth2), pode ser necessário ajustar a configuração e o código para se adequar ao seu caso de uso específico. Além disso, você pode precisar configurar e proteger recursos em seu aplicativo da web com base nas permissões dos usuários.

### Melhorias para o htmal 

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mapa com Menu</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        #map {
            height: 400px;
            width: 100%;
        }
        
        #menu {
            width: 200px;
            float: left;
        }
        
        #menu ul {
            list-style-type: none;
            padding: 0;
        }
        
        #menu li {
            margin-bottom: 10px;
        }
        
        #menu a {
            display: block;
            padding: 10px;
            background-color: #f4f4f4;
            border: 1px solid #ddd;
            text-decoration: none;
            color: #333;
        }
        
        #menu a:hover {
            background-color: #ddd;
        }
    </style>
</head>
<body>
    <div id="menu">
        <h2>Menu</h2>
        <ul>
            <li><a href="#">Opção 1</a></li>
            <li><a href="#">Opção 2</a></li>
            <li><a href="#">Opção 3</a></li>
        </ul>
    </div>
    <div id="map"></div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script>
        var map = L.map('map').setView([-23.5505, -46.6333], 12);
        
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);
    </script>
</body>
</html>

```

### Javascript com keycloak

```javascript

// Inicializa o Keycloak
var keycloak = Keycloak({
    url: 'URL_DO_KEYCLOAK',
    realm: 'NOME_DO_REALM',
    clientId: 'NOME_DO_CLIENTE'
});

// Inicializa o mapa apenas se o usuário estiver autenticado
keycloak.init({ onLoad: 'login-required' }).then(function(authenticated) {
    if (authenticated) {
        console.log('Usuário autenticado');
        initializeMap();
    } else {
        console.log('Falha na autenticação');
    }
}).catch(function() {
    console.log('Erro ao inicializar o Keycloak');
});

// Função para inicializar o mapa
function initializeMap() {
    var map = L.map('map').setView([-23.5505, -46.6333], 12);

    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
    }).addTo(map);

    // Adiciona marcador para a cidade de São Paulo
    var saoPauloMarker = L.marker([-23.5505, -46.6333]).addTo(map);
    saoPauloMarker.bindPopup("<b>São Paulo</b>").openPopup();

    // Adiciona marcador para o Bairro Jardim Helena
    var jardimHelenaMarker = L.marker([/* coordenadas do Bairro Jardim Helena */]).addTo(map);
    jardimHelenaMarker.bindPopup("<b>Bairro Jardim Helena</b>").openPopup();
}

```

### Adicioanar video ao mapa

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mapa com Câmera ao Vivo</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <style>
        #map {
            height: 400px;
            width: 100%;
        }
    </style>
</head>
<body>
    <div id="map"></div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script>
        var map = L.map('map').setView([-23.5505, -46.6333], 12);

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        // URL do vídeo ao vivo
        var videoUrl = "URL_DO_STREAMING_DE_VIDEO";

        // Adiciona a camada de vídeo ao vivo ao mapa
        var videoLayer = L.videoOverlay(videoUrl, [[-23.5505, -46.6333], [-23.55, -46.63]], { opacity: 0.7 }).addTo(map);

        // Adiciona controles de reprodução do vídeo
        videoLayer.getElement().autoplay = true;
        videoLayer.getElement().controls = true;
    </script>
</body>
</html>

```
Substitua "URL_DO_STREAMING_DE_VIDEO" pelo URL da transmissão de vídeo ao vivo. Certifique-se de usar um URL compatível com o formato de vídeo suportado pelo navegador.

L.videoOverlay() é usado para criar uma camada de vídeo ao vivo. Ele recebe o URL do vídeo, a extensão do mapa e algumas opções, como opacidade.


videoLayer.getElement().autoplay = true; e videoLayer.getElement().controls = true; são usados para habilitar os controles de reprodução do vídeo, como play, pause e volume.

Com este código, você poderá adicionar uma câmera ao vivo ao seu mapa Leaflet e exibir o vídeo em tempo real sobre o mapa. Certifique-se de ter uma conexão de internet estável e o URL de streaming de vídeo correto para que o vídeo seja exibido corretamente.

### Geofabrik - INSTRUÇÕES DE USO

Para instalar geofabrik:


https://hub.docker.com/r/postgis/postgis/

podman run --network host --name meu-postgis -e POSTGRES_PASSWORD=SUASENHA -d postgis/postgis

Depois de baixar os mapas do geofabrik executar o comando:

osm2pgsql ~/Downloads/brazil-latest.osm.pbf -d osm -U postgres -H localhost -P 5432 -S /usr/share/osm2pgsql/default.style --hstore

Com o postgis aberto, criar um banco de dados com o nome osm, criar as seguintes tabelas:

CREATE EXTENSION postgis;
CREATE EXTENSION hstore;

Caso a porta 5432 esteja em uso, execute os seguints comandos para verificar se a porta 5432 esteja em uso, execurte os seguintes comandos:
Para descobrir o servico do postgres se estiver rodando no hospedeiro :
sudo systemctl  | grep post

No meu caso o serviço era: postgresql.service
Para parar:
sudo systemctl stop postgresql.service

Para verificar se parou :
sudo systemctl status postgresql.service
○ postgresql.service - PostgreSQL RDBMS
    Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
    Active: inactive (dead) since Mon 2024-04-29 11:04:18 -03; 3s ago
   Process: 292184 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
  Main PID: 292184 (code=exited, status=0/SUCCESS)
       CPU: 2ms
Mostra Acitve: inactive

Então verifiquei o container: 
podman ps -a
CONTAINER ID  IMAGE                                    COMMAND               CREATED      STATUS                    PORTS                   NAMES
cd6b45db39f7  localhost/test_apache_containter:latest  apache2ctl -D FOR...  7 weeks ago  Exited (137) 7 weeks ago  0.0.0.0:8888->80/tcp    inspiring_clarke
04dda8865c06  localhost/iac_firstservice:latest        iac_firstservice      6 weeks ago  Exited (137) 6 weeks ago                          focused_colden
f17afe0b51e8  docker.io/postgis/postgis:latest         postgres              13 days ago  Created                   0.0.0.0:5432->5432/tcp  joe-postgis

Para startar o container: 
       podman start joe-postgis

 podman ps
CONTAINER ID  IMAGE                             COMMAND     CREATED      STATUS            PORTS                   NAMES
f17afe0b51e8  docker.io/postgis/postgis:latest  postgres    13 days ago  Up 4 seconds ago  0.0.0.0:5432->5432/tcp  joe-postgis      
