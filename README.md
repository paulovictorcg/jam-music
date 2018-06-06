# Prova Prática ThoughtWorks

Este teste foi desenvolvido utilizando a plataforma ASP.NET Core. Esta tecnologia é livre e independente de plataforma. Logo o sistema está hábil para ser executado em ambiente Windows, Linux e MacOS. (Entretanto, por uma questão de tempo meus testes, foram feitos exclusivamente no Windows). Também foi utilizado [Docker](https://www.docker.com/products/docker) como recomendado nas instruções.

## Dos Requisitos

Esta prova requer [Docker 18.03](https://docs.docker.com/release-notes/docker-ce) ou superior (Caso queira executa-lo utilizando contêiners). Você também ira precisar da última versão do Windows 10 ou Windows Server 2016 para usar [Windows containers](http://aka.ms/windowscontainers). E o [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/core).

## Da Compilação e Execução Rápida
Você pode compilar e executar a aplicação com  [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/core) localmente sem o Docker usando os seguintes comandos: (Os comandos assumem que você está no diretório raíz da aplicação). 

```console
cd ThoughtWorks
dotnet run
```

Depois da execução dos comandos, você pode ver a aplicação na  URL `http://localhost:3000`
obs.: Lembre-se, se já houver algo escutando nessa porta será gerado uma exceção.

# Compilação e execução para Docker com Windows Contêniner
Você pode compilar e executar o Docker em um Windows Contêiner usando os seguintes comandos no terminal: (Os comandos assumem que você está no diretório raíz da aplicação)

```console
cd thoughtworks
docker build -t thoughtworks .
docker run -it --rm -p 3000:80 thoughtworks
```
Não se esqueça do "ponto" após o comando. Estes comandos podem demorar.

Depois disso, você pode iniciar a aplicação pela url `http://localhost:3000` no seu navegador.
Nota: O  argumento `-p` mapeia a porta 3000 na sua máquina local para a porta 80 no contêiner. Veja a [referência do Docker](https://docs.docker.com/engine/reference/commandline/run/) para mais informações sobre linhas de comando.


 Você deve visualizar um resultado algo como:

![Você deve ver algo como isso:](https://raw.githubusercontent.com/paulovictorcg/jam-music/master/json.PNG)
Imagem 1 - JSON de resultado exibido no navegador. 


## Da Arquitetura e Padrão de desenvolvimento

O sistema foi dividido em camadas, representadas pelos projetos
BLL, DAL. 

O Projeto BLL representa a camada de negócio enquanto o projeto DAL 
representa a camada de acesso aos dados. 

O Projeto ThoughtWorks apenas gerencia as rotas e requisições e mostra o retorno.

![solucao](https://github.com/paulovictorcg/jam-music/blob/master/solucao.PNG?raw=true)
Imagem 2 - A solução vista do Visual Studio 2017

Os Testes foram separados em outra pasta, como é comum em projetos orientado a testes. 
Foi criado uma classe Mock para auxiliar os testes junto com injeção de dependência.
Para a pirâmide de testes, foi usado apenas uma classe para teste unitário, devido ao tamanho e simplicidade do projeto.

## Das considerações finais
 -  Não foi gerado um MakeFile devido a simplicidade dos comandos (apenas 2) no windows e a impossibilidade de instalar via linha de comando o Docker. 
 
 - O código está escalável. Você pode trocar a organização que calcula o desempenho das linguagens, bastando apenas trocar o parâmetro passado por padrão ao método.
 - É possível executar a aplicação no Visual Studio 2015 em diante apenas abrindo o arquivo Sln dentro do Visual Studio

## Recursos relacionados

* [Começando com ASP.NET Core](https://www.asp.net/get-started)
* [.NET Core Docker ](../dotnetapp-prod/README.md)
* [.NET Core Docker Exemplos](../README.md)
* [.NET Framework Docker samples](https://github.com/Microsoft/dotnet-framework-docker-samples)

