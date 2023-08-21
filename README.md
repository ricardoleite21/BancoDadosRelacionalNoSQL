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

Segue abaixo os códigos utilizados de uma aplicação que utiliza tanto um banco de dados relacional quanto um banco de dados NoSQL para armazenar informações de clientes e contas, tendo como objetivo explorar e aplicar conceitos de banco de dados usando SQLAlchemy para o banco de dados relacional e Pymongo para o banco de dados NoSQL.

pip install sqlalchemy

!pip install pymongo

from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.declarative import declarative_base

# Crie uma conexão com o banco de dados SQLite (ou outro banco de dados suportado)
engine = create_engine('sqlite:///banco_de_dados.db')

# Crie uma instância de sessão para interagir com o banco de dados
Session = sessionmaker(bind=engine)
session = Session()

# Crie uma classe base para definir os modelos de dados
Base = declarative_base()

# Defina as classes que representam as tabelas do banco de dados
class Cliente(Base):
    __tablename__ = 'clientes'
    
    id = Column(Integer, primary_key=True)
    nome = Column(String)
    email = Column(String)

class Conta(Base):
    __tablename__ = 'contas'
    
    id = Column(Integer, primary_key=True)
    numero = Column(String)
    saldo = Column(Integer)
    cliente_id = Column(Integer)

# Crie as tabelas no banco de dados
Base.metadata.create_all(engine)

# Inserir dados de exemplo
cliente1 = Cliente(nome='João', email='joao@email.com')
cliente2 = Cliente(nome='Maria', email='maria@email.com')

conta1 = Conta(numero='12345', saldo=1000, cliente_id=1)
conta2 = Conta(numero='54321', saldo=500, cliente_id=2)

session.add_all([cliente1, cliente2, conta1, conta2])
session.commit()

# Recuperar dados
clientes = session.query(Cliente).all()
contas = session.query(Conta).all()

for cliente in clientes:
    print(f"Cliente: {cliente.nome}, Email: {cliente.email}")

for conta in contas:
    print(f"Conta: {conta.numero}, Saldo: {conta.saldo}")

import pymongo

# Substitua <USERNAME> e <PASSWORD> pelas suas credenciais do MongoDB Atlas
USERNAME = "user_name"
PASSWORD = "my_password"

# Conecte-se ao cluster do MongoDB no MongoDB Atlas
client = pymongo.MongoClient(f"mongodb+srv://user_name}:{ikOpaCup70Gxpf3n}@cluster.mongodb.net/test?retryWrites=true&w=majority")

# Crie um banco de dados no MongoDB
db = client["banco_no_sql"]

# Crie uma coleção chamada "bank" para armazenar os documentos de clientes
collection = db["bank"]

# Insira documentos com a estrutura mencionada
cliente1 = {
    "nome": "João",
    "email": "joao@email.com",
    "contas": [
        {
            "numero": "12345",
            "saldo": 1000
        },
        {
            "numero": "54321",
            "saldo": 500
        }
    ]
}

cliente2 = {
    "nome": "Maria",
    "email": "maria@email.com",
    "contas": [
        {
            "numero": "67890",
            "saldo": 1500
        }
    ]
}

collection.insert_one(cliente1)
collection.insert_one(cliente2)

# Recuperar informações com base nos pares de chave e valor
# Exemplo: Recuperar informações do cliente com nome "João"
resultado = collection.find_one({"nome": "João"})
print("Informações do cliente:")
print(resultado)

# Exemplo: Recuperar todas as contas com saldo maior que 1000
contas_acima_de_1000 = collection.find({"contas.saldo": {"$gt": 1000}})
print("\nContas com saldo acima de 1000:")
for conta in contas_acima_de_1000:
    print(conta)

    
pip install sqlalchemy
