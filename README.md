---Criação de tabelas no MySQL

create table tb_marcas (
	id bigint auto_increment,
    nome varchar (20) not null,
    ativo boolean,
    primary key(id)
)

--"foreign key" define a chave estrangeira, estando dentro dos parenteses a coluna e por fim fazendo referência outra tabela, colocando o nome da coluna entre parenteses

create table tb_produtos (
	id bigint auto_increment,
    nome varchar (30) not null,
    preco decimal,
    marca_id bigint not null,
    primary key (id),
    foreign key (marca_id) references tb_marcas (id)
)


--Exclusão de tabelas no MySQL
drop table tb_marcas

--Exclusão coluna na tabela no MySQL
delete from tb_marcas where id = 3

--Atualização de coluna na tabela no MySQL
update tb_produtos set preco = 79.80 where id = 3

--Inserção de dados nas tabelas no MySQL

insert into tb_marcas (nome, ativo) values ("Nike", true);
insert into tb_marcas (nome, ativo) values ("H&M", true);
insert into tb_marcas (nome, ativo) values ("Zara", true);
insert into tb_marcas (nome, ativo) values ("Louis Vuitton", true);
insert into tb_marcas (nome, ativo) values ("Adidas", true);
insert into tb_marcas (nome, ativo) values ("Uniqlo", true);
insert into tb_marcas (nome, ativo) values ("Hermes", true);
insert into tb_marcas (nome, ativo) values ("Rolex", true);
insert into tb_marcas (nome, ativo) values ("Gucci", true);
insert into tb_marcas (nome, ativo) values ("Cartier", true);
insert into tb_marcas (nome, ativo) values ("Polo", true);
insert into tb_marcas (nome, ativo) values ("Armany", true);

--Visualização de tabela completa no MySQL

select * from tb_marcas

--Visualização de coluna na tabela do MySQL

select * from tb_produtos where marca_id =5

select * from tb_produtos where marca_id =5 and nome like '%cal%'

--Alteração coluna que já existe no MySQL

--Determina o preço possui seis digitos antes da virgula e dois depois

alter table tb_produtos modify column preco decimal (6,2)

--  INNER JOINS --

select * from tb_produtos
	inner join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id

--Seleciona nome da coluna sendo necessario fornecer o nome do atributo de todas as tabelas--

select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	inner join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id


-- Pesquisar apenas produtos de uma marca

select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	inner join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id
    where tb_marcas.nome = 'adidas'


-- Pesquisar apenas produtos de uma marca abaixo de 60 reis 

select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	inner join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id
    where tb_marcas.nome = 'adidas'
    and tb_produtos.preco < 60

-- Pesquisar apenas meias e camisas --

select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	inner join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id
    where tb_produtos.nome = 'meias'
    or tb_produtos.nome = 'camisas'

-- Prioriza tabela da esquerda
select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	left join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id

-- Prioriza tabela da direita
select tb_produtos.nome, tb_produtos.preco, tb_marcas.nome from tb_produtos
	right join tb_marcas
    on tb_marcas.id = tb_produtos.marca_id


