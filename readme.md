## Comandos de banco de dados

### Criar database
* Local para criar as tabelas do sistema
```
create database NOME_DATABASE;
```
### Executar o comando
```
Ctrl + Enter
```
### Selecionar database
```
use NOME_DATABASE;
```
<hr>

## Projeto site Ecommerce
* Tabela de usuários
* Tabela de produtos
* Tabela de carrinho de compras

### Criar tabela de usuários
```
create table usuarios(
    id int not null auto_autoincrement,
    nome varchar(120) not null,
    email varchar(120) not null,
    senha varchar(120) not null,
    primary key(id)
);
```
* id: identificador de cada registro
* not null: campo obrigatório, não pode ser nulo
* auto_autoincrement: soma +1 no último registro de id
* varchar(120): campo de texto com 120 caracteres

### Criar tabela de produtos
```
create table produtos(
    id int not null auto_autoincrement,
    modelo varchar(120),
    nome varchar(120) not null,
    valor float not null,
    primary key(id)
);
```

### Criar tabela de carrinho
```
create table carrinho(
    id int not null auto_autoincrement,
    id_usuario int not null,
    id_produto int not null,
    primary key(id),
    foreign key(id_usuarios) references usuarios(id),
    foreign key(id_produtos) references produtos(id)
);
```
* foreign key: chave estrangeira que recebe a referência de outra tabela
* references: atributo para definir a tabela e o campo estrangeiro

### Inserir usuários
```
insert into usuarios(nome, email, senha) values ('Renato Gaucho', 'teste@teste.com', 'secret');
```

### Inserir produtos
```
insert into produtos(modelo, nome, valor) values ('nike', 'camiseta', 129,99);
```

### Inserir carrinho
```
insert into carrinho(id_usuario, id_produto) values (43, 234);
insert into carrinho(id_usuario, id_produto) values (43, 120);
insert into carrinho(id_usuario, id_produto) values (43, 125);
insert into carrinho(id_usuario, id_produto) values (43, 6);
```

### Listar todas as colunas de usuários
```
select * from usuarios;
```

### Listar os nomes dos usuarios
```
select nome from usuarios;
```

### Listar os nomes e email dos usuarios
```
select nome, email from usuarios;
```

### Listar usuarios pelo id
```
select * from usuarios where id = 23;
```

### Verificar produtos no carrinho pelo id do usuário
```
select p.nome
from produto p, carrinho c
where c.id_usuario = 23 AND p.id = c.id_produtos;
```