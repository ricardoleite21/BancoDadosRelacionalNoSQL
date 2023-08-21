# BancoDadosRelacionalNoSQL

Desafio de Implementação de Banco de Dados – DIO

Neste desafio, desenvolvi uma aplicação que utiliza tanto um banco de dados relacional quanto um banco de dados NoSQL para armazenar informações de clientes e contas. O objetivo foi explorar e aplicar conceitos de banco de dados usando SQLAlchemy para o banco de dados relacional e Pymongo para o banco de dados NoSQL.

Parte 1 - Banco de Dados Relacional (SQLite) com SQLAlchemy

Na primeira parte do desafio, utilizei o SQLAlchemy para criar um banco de dados relacional com um esquema que inclui tabelas para clientes e contas. As principais etapas incluíram:

	Definição das classes de modelo para representar as tabelas do banco de dados.
	Configuração de uma conexão com o SQLite.
	Criação do banco de dados e das tabelas.
	Inserção de dados de clientes e contas para possibilitar a manipulação das informações.
	Execução de métodos de recuperação de dados usando SQLAlchemy.

Parte 2 - Banco de Dados NoSQL (MongoDB) com Pymongo

Na segunda parte do desafio, criei um banco de dados NoSQL utilizando o MongoDB para fornecer uma visão agregada do modelo relacional. As operações realizadas incluíram:

	Conexão ao MongoDB Atlas e criação de um banco de dados.
	Definição de uma coleção chamada "bank" para armazenar os documentos de clientes.
	Inserção de documentos com a estrutura especificada, onde informações de clientes e contas estão contidas dentro de documentos de acordo com o cliente.
	Escrita de instruções para recuperar informações com base em pares de chave e valor, semelhante ao que foi demonstrado em aula.

Este desafio me permitiu explorar e aplicar conceitos de banco de dados relacionais e NoSQL, bem como praticar o uso de ferramentas como SQLAlchemy e Pymongo. O projeto final está disponível neste repositório do GitHub para referência e pode ser utilizado como parte do meu portfólio técnico.

