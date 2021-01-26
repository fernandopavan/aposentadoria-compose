# Projeto de cálculo de score

Aplicação para realizar cálculo de aposentadoria para beneficiários. 
<br>

<b> Demonstração: </b> https://aposentadoria-app.herokuapp.com - <b>Obs.:</b> esperar subir a aplicação;
<br/>
    <b> Login: </b> `email: maria@gmail.com` | `senha: 123`

<br>

### Funcionalidades e tecnologias

- Cadastro de beneficiários
- Cadastro de administradores
- Java 11
- Spring Boot
- Spring Cloud
- Spring Gateway
- Autenticação Spring Security e JWT
- RabbitMQ (AMQP) ou CloudAMQP
- Maven 
- Angular 8 - TypeScript
- API Swagger 
    http://localhost:8080/api/beneficiario/swagger-ui.html <br>
    http://localhost:8080/api/caixa-eletronico/swagger-ui.html <br>
    https://aposentadoria-gateway.herokuapp.com/api/caixa-eletronico/swagger-ui.html <br>
    https://aposentadoria-gateway.herokuapp.com/api/beneficiario/swagger-ui.html  <br>
- QueryDSL 
- Websocket
- JPA - Hibernate
- Testes unitários e testes de integração
- Padrão de projeto Builder com Generics
- Banco de dados PostgreSQL
- Bean Validation
- REST com JSON 
- ControllerAdvice (NOT_FOUND, BAD_REQUEST, UNPROCESSABLE_ENTITY, FORBIDDEN)
- Etc

#### Execução via `docker-compose`

- Para rodar o projeto em seu computador, clone este repositório no mesmo, execute esse comando no terminal `docker-compose up` dentro do diretório do projeto.
- <b>Obs.:</b> é necessário ter o docker (~19.03.8) instalado no seu computador.

- Para usar, no navegador, digite a seguinte URL: http://localhost:9000
<br><b> Login: </b> `email: maria@gmail.com` | `senha: 123`
    
- Para ver o gerenciador do RabbitMQ, no navegador, digite a seguinte URL: http://localhost:15672


#### Execução em ambiente `local`


##### Para rodar o front-end:

- Clone este repositório: https://github.com/fernandopavan/aposentadoria-front
- Execute os seguintes comandos na raiz do projeto: `npm install` e depois `npm start`
- <b>Obs.:</b> é necessário ter o `node: ~v13.12.0` e o `npm: ~6.14.4` instalado no seu computador.


##### Para rodar o back-end:

- Clone os repositórios abaixo:
    https://github.com/fernandopavan/aposentadoria-commons <br>
    https://github.com/fernandopavan/aposentadoria-gateway-api  <br>
    https://github.com/fernandopavan/aposentadoria-caixa-api <br>
    https://github.com/fernandopavan/aposentadoria-beneficiario-api <br>

- Execute o seguinte comando em cada raiz dos repositórios clonados: `mvn install`.

- Criar e configurar o banco de dados Postgres (localhost:5432): `usuario=aposentadoria_owner` | `senha=123456` | `banco=aposentadoria` 
  <br><b>OU</b>  criar com Docker com o comando: 
`docker run --name banco-aposentadoria -e POSTGRES_USER=aposentadoria_owner -e POSTGRES_PASSWORD=123456 -e POSTGRES_DB=aposentadoria -p 5432:5432 -d postgres`.

- Rodar o RabbitMQ via Docker executando o comando : `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management` 
  <br><b>OU</b> via CloudAMQP, descomentando a var `app.amqp.url` em `application-dev.properties` e comentando as `spring.rabbitmq.*`.  
Descomentar também a parte comentada na classe `CalculoAMQPConfig.java`. Fazer isso para os dois projetos: `aposentadoria-beneficiario-api` e `aposentadoria-caixa-api`

- Após, execute o seguinte comando na raiz dos repositórios `aposentadoria-beneficiario-api`,
`aposentadoria-caixa-api` e `aposentadoria-gateway-api `: `java -jar target/alterar_por_nome_projeto.jar`

- <b>Obs.:</b> é necessário ter o Docker, Java 11 e Maven instalados no seu computador. Também ter as váriaveis de ambiente configuradas.


- Para usar, no navegador, digite a seguinte URL: http://localhost:9000 
<br><b> Login: </b> `email: maria@gmail.com` | `senha: 123`

- Para ver o gerenciador do RabbitMQ quando executado local, no navegador, digite a seguinte URL: http://localhost:15672


### Dúvidas:
`email: fernando.pavan@outlook.com`
