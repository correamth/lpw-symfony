## Atividade avaliativa de Linguagem de Programação para a WEB

# Passo a Passo para criação do seu primeiro CRUD com o Framework [Simfony](https://symfony.com/)

# Iniciando

Acessar o site -> Documentation -> Getting Started

[Chapter 1. Setup](https://symfony.com/doc/current/setup.html) o que você realmente precisa aqui:

1. Instalar o [composer](https://getcomposer.org/download/)
2. Verificar se o PHP da sua máquina(xampp) é 7.1+
3. Na linha de comando, vá até a htdocs e crie uma pasta
* mkdir simfony
* cd simfony
* composer create-project symfony/website-skeleton seu-projeto
7. cd seu-projeto
8. rode localmente com o comando:
* php bin/console server:run

# Pule para o Controller

[Chapter 4. Controllers](https://symfony.com/doc/current/index.html#gsc.tab=0) vá até o subtitulo Generating Controllers:

1. Gere um classe controller com o comando: 
* php bin/console make:controller BrandNewController

# Va para o Doctrine

1. Execute os comandos:
* composer require symfony/orm-pack
* composer require symfony/maker-bundle --dev
2. Procure seu arquivo .env no diretório do seu projeto e coloque a configuração do seu mysql localhost, assim:
```go
# .env

# customize this line!
DATABASE_URL=mysql://root:@127.0.0.1:3306/formulario
```
3. Execute:
* php bin/console doctrine:database:create
4. Crie a entidade:
* php bin/console make:entity




Vai pedir o seguinte:
```go
C:\xampp\htdocs\symfonytrabalho2\formulario>php bin/console make:entity

 Class name of the entity to create or update (e.g. GrumpyJellybean):
 > Produto

 created: src/Entity/Produto.php
 created: src/Repository/ProdutoRepository.php

 Entity generated! Now let's add some fields!
 You can always add more fields later manually or by re-running this command.

 New property name (press <return> to stop adding fields):
 > nome

 Field type (enter ? to see all types) [string]:
 > string

 Field length [255]:
 > 255

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Produto.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > preco

 Field type (enter ? to see all types) [string]:
 > integer

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Produto.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > descricao

 Field type (enter ? to see all types) [string]:
 > text

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Produto.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 >ENTER PARA CONCLUIR
```
5. Agora sincroniza com o Banco de dados com os comandos:
* php bin/console make:migration
* php bin/console doctrine:migrations:migrate
* y

# Voltando para o [Controller](https://symfony.com/doc/current/controller.html)

1. Enfim, faça o crud:
* php bin/console make:crud Produto
```go
C:\xampp\htdocs\symfonytrabalho2\formulario>php bin/console make:crud Produto

 created: src/Controller/ProdutoController.php
 created: src/Form/ProdutoType.php
 created: templates/produto/_delete_form.html.twig
 created: templates/produto/_form.html.twig
 created: templates/produto/edit.html.twig
 created: templates/produto/index.html.twig
 created: templates/produto/new.html.twig
 created: templates/produto/show.html.twig


  Success!


 Next: Check your new CRUD by going to /produto/
```
2. Rode o server:
* php bin/console server:run
3. Está pronto http://127.0.0.1:8000/produto/

# Para deixar mais bonito

1. Aproveite o twig, vá até seu-projeto/templates/produto/base.html.twig e coloque o cdn do bootstrap
* Todas as paginas que foram criadas automaticamente para o CRUD do seu produto, estão recebendo essa base.
![ss](https://raw.githubusercontent.com/correamth/lpw-simfony/master/symfony.png)

# Obrigado.


