# Integrar dados de uma API para um Banco MongoDB com NiFi

## Compilar e rodar Nifi + MongoDB 
`docker-compose -f stack.yml up`

## Dados de acesso do mongo-express
- URL: **localhost:8081**
- Informe o usuário: **root**
- Informe a senha: **abc123**

## Dados de acesso do mongoDB
- URL: **localhost:27017**
- Informe o usuário: **root**
- Informe a senha: **abc123**

## Dados de acesso do NiFi
- URL: **localhost:8080**

## O que fazer no mongoDB
- Acesse o mongo-express
- Crie um Database com nome **pokemon**

## O que configurar no NiFi
- Crie um resource group 
- Configure um GetHTTP
    - Configure um controller service
    - Local do certificado https (caminho do volume): **/storage/certs**
    - Senha do certificado: **senha123**
    - Keystore type: **JKS**
    - URL da API: **https://pokeapi.co/api/v2/pokemon/1**
- AttributesToJSON
- PutMongo
    - Configurar Client Server
    - Configurar nome do Database
    - Configurar nome da Collection
    - Client Auth: **NONE**

## Troubleshooting
### Problema de network entre containers
- docker run -it nifi bash
- apt-get update
- apt-get install telnet
- apt-get install curl
- telnet localhost 8081
- telnet localhost 27017
- curl localhost:8081