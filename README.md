# {BANCO DE DADOS}

### <O que é Banco de Dados?>
 
Banco de dados, é uma coleção organizada de dados de uma determinada empresa, 
separadas e armazenadas por pastas e protegidas, a fim de evitar acessos indevidos. 

Para se ter acesso ao Bd deve haver autorização da organização da empresa provedora desses dados, o acesso ocorre por meio de sistemas e usuários. Os dados podem ser coletados isoladamente ou em conjunto (lista), após serem tratados e processados transformam-se em informações.


### <Entidades e atributos> 

Quando construímos um Bd para determinada empresa, é importante fazer um levantamento de necessidades e partes envolvidas que irão contribuir com dados, Essas “partes envolvidas” chamamos de *entidades*. Os dados que caracterizam aquela entidade são chamados de *atributos*.

Exemplo: No app Ifood, a finalidade é oferecer um serviço que disponibiliza uma lista de restaurantes delivery para clientes comprarem refeições. 

*Quais são as entidades e atributos do Ifood?*

|   ENTIDADE     |    ATRIBUTOS                        |
|----------------|-------------------------------------|
| Cliente        | nome; CPF; e-mail; endereço; cartão |
| Restaurante    | nome; CNPJ; endereço; classificação |
| Entregador(a)	 | nome; CPF; fone; tipo veículo; placa|



### <Sistemas de gerenciamento> 

O Banco de dados precisa de uma estrutura de armazenamento, para poder manipular e controlar as permissões existe os sistemas de gerenciamento. Existe os sistemas de gerenciamento de código aberto e código fechado. 

Os sistemas mais conhecidos são: Oracle, MySQL, MicrosoftSQL Server,PostgreSQL, MongoDB, 

*SQL significa: Standard Query Language*


### Um sistema de gerenciamento pode ser Relacional(SQL) e Não relacional(NoSQL).


#### No modelo relacional 

É preciso criar uma estrutura parecida com as tabelas de excel, com colunas e linhas determinadas e organizadas separadamente, visualmente trás um entendimento melhor e conseguimos garantir qualidade a integridade de dados, determinando as regras para adicionar os dados.

![image](https://user-images.githubusercontent.com/93724227/143956969-18d55337-841b-436b-b6c5-ffd68796d7d1.png)


#### No modelo não relacional
 
A estrutura dos bancos é dinâmico e não precisam de estrutura previa, a estrutura pode variar de uma base de dados para outra. Tem sua estrutura a medida do seu uso.
 
 ![image](https://user-images.githubusercontent.com/93724227/143957319-f66ad832-5100-4293-b187-b8255c36f484.png)


  
 ## Comandos do MongoDB no terminal CMD/MONGOSHEL 
 
  
 - Para iniciar o serviço do mongo, abra p terminal CMD e digite: #### mongod
 
 - Agora você inicia o mongo shell, deixando o terminal disponível para a execução de comandos, abra outro terminal CMD e digite: #### mongo


#### Para criar o banco de dados
 
use <NOME_DO_DATABASE>
 
 
#### Para apagar o banco de dados

db.dropdatabase(NOME_DO_DATABASE)
 
 
#### Para criar uma collection

db.createcollection("NOME_DA_COLLECTION")
 

#### Para buscar todos os registros sem filtro algum utilizamos o comando find:

db.collectionName.find()
 

#### Para buscar registros a partir de um filtro:

 db.collectionName.find({filtros})
 

#### Para inserir registros novos dentro do banco de dados:

db.collectionName.inserMany/insertOne({objeto a ser inserido})
 

#### Para atualizar registros dentro do banco de dados:

db.collectionName.updateMany/updateOne({filtros},{ $set: {campos a serem atualizados}})
 

#### Para remover regisros dentro do banco de dados:

db.collectionName.deleteOne/deleteMany({filtros})
 

Vimos também que quando incluímos um registro no mongo, ele gera um Id único, chamado Object_id, que nada mais é do que um identificador único gerado no momento que o registro é salvo no banco de dados, esse object id é composto pela data e hora que o registro foi incluído no banco.


### Integração com projeto Node.js

Anteriormente, nos projetos vistos até então vocês utilizavam um arquivo .json para representar o banco de dados, correto?

Pensando na arquitetura de um sistema, precisamos que os dados não fiquem dentro da aplicação, e sim em uma camada destinado aos dados.


#### banco1

Para aplicar os conceitos aprendidos até então e alterar o nosso projeto para que ele busque os dados do banco de dados e NÃO mais do aquivo .json, realizamos os passos abaixo:


- Mongoose

Realizamos a instalação da dependência mongoose, que é a nossa interface da aplicação node.js para o banco de dados Mongo.

Para instalar o mongoose no projeto executamos:

npm install mongoose
Obs.: não esquecer de importar no mongo essa nova dependência:

const mongoose = require("mongoose")


- String de Conexão

Para realizar a conexão com o servidor que está rodando localmente no seu computador, precisamos referenciar a string de conexão com o respectivo banco que iremos utilizar no projeto:


mongoose.connect("mongodb://localhost:27017/reprograma", { 
  useNewUrlParser: true, 
  useUnifiedTopology: true 
});


Obs.: a porta padrão de comunicação do mongo é a 27017, e a informação contida após esse número é o nome do banco de dados.
Para capturar o erro ou o sucesso na conexão, utilizamos a seguinte sintaxe:

//Conexão com o mongo

let db = mongoose.connection;

// Captura de erro ou sucesso na conexão

db.on("error", console.log.bind(console, "connection error:"))
db.once("open", function (){
  console.log("conexão feita com sucesso.")
})

- Schema

Um esquema nada mais é do que a estrutura mapeada dos atributos da sua entidade. Ela é uma representação dos registros que estão salvos dentro do banco de dados, e é através dela que iremos realizar acesso ao banco.

Um schema também pode ser comparado a um model, que dentro da estrutura MVC é a camada das suas classes/entidades do projeto.


scheema

Segue abaixo um exemplo de Scheema visto nas aulas anteriores:

const mongoose = require('mongoose');

//estrutura do seu model (atributos da sua entidade)

const tarefasSchema = new mongoose.Schema({
    id : { type : Number},
    descricao: { type: String },
    dataInclusao: { type: String },
    concluido: { type: Boolean },
    nomeColaboradora: { type: String }
},{
    //gera por padrão uma versão para cada atualização do documento

    versionKey: false
});

// atribuindo o esquema a uma collection
// estou definindo o nome da collection que irei salvar no banco

const tarefas = mongoose.model('tarefas', tarefasSchema);

// exportar o model para ser utilizado

module.exports = tarefas;


Após definir o schema, devemos referenciá-lo na nossa controller e remover a referência do arquivo .json (apagá-lo também).

Para isso, dentro da controller correspondente ao model:

const <nomeDoSchema> = require('../models/<nomeDoSchema>');


Implementação dos Métodos através da controller

Até o momento, vimos os métodos, find, insert, delete e update, mas, qual é a relação deles com os nossos métodos HTTP?


### CRUD

Basicamente, podemos relacionar os métodos http com os comandos do mongo:

INSERT / POST
UPDATE / PUT
DELETE / DELETE
FIND / GET
Agora, alguns exemplos de implementação dos métodos http através das rotas:

GET /entidade

    entidade.find(function(err, retorno){
        if(err) { 
            res.status(500).send({ message: err.message })
        }else{
            res.status(200).send(retorno);
        }
    })

POST /entidade

    let entidade = new entidade(req.body)

    entidade.save(function(err){
        if(err) { 
            res.status(500).send({ message: err.message })
        }else{
            res.status(201).send(entidade.toJSON())
        }
    })

DELETE /entidade

    entidade.deleteMany({ filtros }, function (err) {
        if (!err) {
            res.status(200).send({ message: 'removido com sucesso', status: "SUCCESS" })
        }else{
            return res.status(424).send({ message: err.message })
        }
    })
  }

UPDATE /entidade

   entidade.updateMany({ filtros }, { $set : req.body }, function (err) {
        if (err) {
          res.status(500).send({ message: err.message })
        }else{
            res.status(200).send({ message: "Registro alterado com sucesso"})
        }
      })

 
 
 #### *Autora: Tereza Oliveira*
 
 Fonte: http://paulodutrainfo.com.br/alguns-comandos-basicos-mongodb
 Fonte: https://www.luiztools.com.br/post/tutorial-mongodb-para-iniciantes-em-nosql/
 
