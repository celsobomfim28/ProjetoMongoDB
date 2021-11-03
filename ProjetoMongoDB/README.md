# Como importar a collection no Mongo DB?
 * Utilize o comando 
 ```shell
mongoimport --db <NOME_DO_SEU_DB> --collection <NOME_DA_COLLECTION> --file biblioteca.json
```

# Descrição do exercício
Você deve criar um banco de dados novo (database) e uma coleção com um nome pertinente, de acordo com os dados e tema que você escolher. Os seguintes comandos devem ser feitos e entregues:

Inserção de documentos
Atualização de documentos
Exclusão de documentos
Consulta com projeção
Consulta utilizando combinação entre os seletores
Consulta paginada e ordenada (utilizar ignorar , limitar e classificar )

* Criação do banco de dados:
```shell
use Biblioteca
```

* Criação da collection:  
```shell
db.createCollection('Consultas')
```

* Listar collections existentes
```shell
show collections
```

* Deleção a collection:  
```shell
db.Consultas.drop()
```

* Inserção de Documento:  
```shell
db.collection.insert({
        "_id" : ObjectId("61808fb2f73372ba1fd36192"),
        "nome" : "Epiphanio Dorea ",
        "cnpj" : "12365467787879/0001-76",
        "Tipo" : "Entidade Pública",
        "telefone" : "(79) 3221-12112",
		"Usuario" : [ 
        {
            "nome" : "Celso Bomfim",
            "cpf" : "0389373939393838",
            "telefone" : "(79) 99999-9999",
            "Livro" : [ 
                {
                    "titulo" : "Dom Casmurro",
                    "autor" : "Machado de Assis",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T10:00:20.000Z")
                }, 
                {
                    "titulo" : "Dona Flor e seus dois maridos",
                    "autor" : "Jorge Amado",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T10:00:20.000Z")
                }
            ]
        }, 
        {
            "nome" : "Enzo Matheus",
            "cpf" : "7893478598475798",
            "telefone" : "(79) 99999-9999",
            "Livro" : [ 
                {
                    "titulo" : "Porto dos Milagres",
                    "autor" : "Machado de Assis",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T10:00:20.000Z")
                }
            ]
        }, 
        {
            "nome" : "Alana Cintia",
            "cpf" : "0376786768768768",
            "telefone" : "(79) 99999-9999",
            "Livro" : [ 
                {
                    "titulo" : "Senhora",
                    "autor" : "Machado de Assis",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T10:00:20.000Z")
                }
            ]
        }
		]
		}
		{
        "_id" : ObjectId("61808fb2f73372ba1fd36193"),
        "nome" : "EAtheneu",
        "cnpj" : "123654565687879/0001-76",
        "Tipo" : "Entidade Pública",
        "telefone" : "(79) 3221-12112",
		"Usuario" : [ 
        {
            "nome" : "Adonis Profanus",
            "cpf" : "0389373939393838",
            "telefone" : "(79) 99999-9999",
             "Livro" : [ 
                {
                    "titulo" : "Porto dos Milagres",
                    "autor" : "Machado de Assis",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T11:00:20.000Z")
                }
            ]
        }
    ]
}
{
        "_id" : ObjectId("61808fb2f73372ba1fd36194"),
        "nome" : "Romero Brito",
        "cnpj" : "123654565437879/0001-76",
        "Tipo" : "Entidade Pública",
        "telefone" : "(79) 3221-12112",
    "Usuario" : [ 
        {
            "nome" : "Amadeus Mozart",
            "cpf" : "0389373939393838",
            "telefone" : "(79) 99999-9999",
             "Livro" : [ 
                {
                    "titulo" : "Porto dos Milagres",
                    "autor" : "Machado de Assis",
                    "dataHoraEmprestimo" : ISODate("2021-07-12T13:00:20.000Z")
                }
            ]
        }
    ]
}
)
```

* Atualização de Documento:  
```shell
		db.getCollection('Consultas').update(
		// query 
		{
        	_id: ObjectId("61808fb2f73372ba1fd36192")
    	},
    	// update 
    	{ $set:
        	{
            	"Usuario.0.nome": "Celso Ricardo Bomfim"
        	}
    	},
    	// options 
    	{
        	"multi" : false,  // update only one document 
        	"upsert" : false  // insert a new document, if no existing document match the query 
    	}
```

* Remoção de Documento:
```shell
db.getCollection('Consultas').remove({ 'nome' : 'EAtheneu' });
```

* Consulta de Documento com Projeção:
```shell
		db.getCollection('Consultas').find(
    	// query 
    	{
        	_id: ObjectId("61808fb2f73372ba1fd36192")
    	},
    	// update 
    	{ 
            "Usuario.nome": 1,
            "_id": 0
    	})
```

* Consulta utilizando combinação entre os seletores:

```shell
db.getCollection('Consultas').find(
{
    nome: 
    {
        $ne: "EAtheneu"
    }
 })

- Consulta paginada e ordenada (utilizar ignorar , limitar e classificar )

db.getCollection('Consultas').find({}).limit(1)

db.getCollection('Consultas').find().skip(2)

db.getCollection('Consultas').find().sort({"nome": 1})
```
