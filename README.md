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

 
 ### <REALIZANDO COMANDOS DO MONGODB NO TERMINAL CMD>
 
 - Para iniciar o serviço do mongo, abra p terminal CMD e digite:
 
> mongod
 
 
 
 

 
 

#### *Autora: Tereza Oliveira*
