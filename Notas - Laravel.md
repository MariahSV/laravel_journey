# ESTUDOS DE LARAVEL

---
## DICIONÁRIO:
---
ACL: access control list; sistema de acessos de conteúdos com uso de usuário

Arquitetura MVC: padrão de arquitetura de software que melhora a conexão entre as camadas de dados, lógica de negócio e interação com usuário; sendo as 3 camadas: Model, Controller e View.

PSR: PHP Standards Recommendations
https://www.php-fig.org/psr/

LTS: long-term support, versão viável com mais manutenção

API: Application Programming Interface (Interface de Programação de Aplicação); mecanismos que permitem que dois componentes de software se comuniquem usando um conjunto de definições e protocolos; No contexto de APIs, a palavra Aplicação refere-se a qualquer software com uma função distinta. A interface pode ser pensada como um contrato de serviço entre duas aplicações. Esse contrato define como as duas se comunicam usando solicitações e respostas. A documentação de suas respectivas APIs contém informações sobre como os desenvolvedores devem estruturar essas solicitações e respostas.
<https://aws.amazon.com/pt/what-is/api/#:~:text=API%20stands%20for%20Application%20Programming,other%20using%20requests%20and%20responses.>

Artisan: assistente de comandos no console/prompt de comandos; auxilia em criar novos controllers, novos models, novas views; agiliza processo de trabalho

Rotas, routes = páginas, urls "complementares", ex: index.html/complemento
app > http > routes

Migrate: migrações ou tabelas de dados criadas com php

---
## REQUISITOS:
---
- PHP
- Composer para o PHP
- sempre averiguar compatibilidade entre linguagem (no caso PHP) e framework (no caso laravel), bem como respectivas versões com LTS (nem tão velhas, nem tão novas, e ainda recebendo atualização)

---
## CONFERINDO VERSÕES:
---
- [ php -v ] no prompt de comando: versão do PHP
- [ php artisan -V ] no prompt de comando: versão do laravel

---
## INSTALAÇÃO:
---
- pode seguir o tutorial nas documentações
-- via composer: pró, vai mais rápido; contra, pode ser que o próprio composer esteja desatualizado, exige mais informações para configurar o ambiente.
-- via composer, mas definindo versão do laravel; método recomendado.

---
## INSTALANDO / CRIANDO NOVO PROJETO
---
- Criar diretório e/ou acessar pasta desejada via CMD (prompt de comando)
- instalar laravel via composer como indicado na documentação da versão escolhida
- inicializar servidor php [comando abaixo]


- .env é o arquivo de configurações do sistema do projeto e deve ficar somente na máquina, sendo ignorado pelo git. Em projetos de servidor não local, configurações extras devem ser feitas nos arquivos da pasta CONFIG.
- Usuário sempre associado a uma ou mais Funções, sendo que cada função tem uma lista de permissões específicas
- principal diretório a ser usado: pasta APP
- root, js e css: em PUBLIC

---
## COMANDOS
---
- cls >> limpa prompt de comando no Windows
- php artisan >> lista todos os comandos do artisan
- php artisan help comando >> explica como funciona o comando escrito
- php artisan serve >> inicia servidor php do projeto e informa a porta do mesmo. Digitando o portal no browser verifica-se se está tudo ok.
- Ctrl+C ou fechando o prompt >> encerra servidor php artisan
- php artisan key:generate >> com o server DESLIGADO, gera uma chave de acesso/segurança para o projeto no arquivo .env [APP_KEY=...]
-- principais no futuro do curso: make:auth, make:command, make:controller, make:event, make:mail, make:middleware, make:migration, make:model, migrate:.., route:.., view

- Route::get (param1, param2) >> exige 2 parâmetros: o caminho da ação (param1) e uma função com retorno de conteúdo (param2), ou um controle (param2). EXEMPLO:
----- Route::get('/', function () {return view('welcome');}); >> use o comando/objeto Routes, use o subcomando/método Get na pasta raiz (/) e faça: retorne da pasta View a blade Welcome.
----- Route::get ('/contato/{id}', function ($id) {return "Contato id=$id"; return 'Contato id='.$id; }); >> puxa a variável presente na rota definida como param1 e através da função, imprime na tela como determinado.
----- EXERCÍCIO: no arquivo routes/web.php >> Route::get ('/contato/{id?}', function ($id = null) {return "Contato id=$id"; return 'Contato id='.$id; }); >> [id?]=verificação de conteúdo; [$id = null]=definição de valor default como nulo no caso;
--- outros métodos possíveis: post, put (edita, dá update em registros), delete;
----- EXERCÍCIO: no arquivo routes/web.php >> Route::post ('/contato', function () { dd($_POST); return "Contato id=$id"; return "Contato POST"; }); >> [dd($_POST);]=método laravel que funciona como [var_dump($_POST);] mais elegante, mais comando Exit ||| no arquivo welcome.blade.php >> inserção de >> 
<div>
	<h2>Teste com Rotas:</h2>
	<form action="/contato" method="post">
		{{ carf_field() }} <!--OBRIGATÓRIO-->
		<input type="text" name="nome" placeholder="Nome / POST">
		<button>Enviar</button>
	</form>
</div> ||| resultado: ao enviar o formulário, direciona para uma página com o texto definido nas rotas [var_dump em forma de dd].
----- EXERCÍCIO: no arquivo routes/web.php >> Route::put ('/contato', function () {  return "Contato id=$id"; return "Contato PUT"; }); ||| no arquivo welcome.blade.php >> inserção de >> <form action="/contato" method="post">
		{{ carf_field() }} <!--OBRIGATÓRIO-->
		<input type="hidden" name="_method" value="put">
		<input type="text" name="nome" placeholder="Nome / PUT">
		<button>Enviar</button>
	</form> ||| resultado: ao enviar o formulário, direciona para uma página com o texto definido nas rotas [Contato PUT]

---
## OBSERVAÇÕES
---
- Há arquivos específicos para funções que afetem APIs, comandos de console e as páginas web.
- localhost:8000/contato >> endereço ou rota ou comando para acessar página Contato; para tal é necessário que exista o arquivo-Blade "contato.blade.php" e respectivo conteúdo, e uma rota para imprimir este arquivo no browser. 
- o laravel possui um sistema de segurança para inputs, que sempre devem possuir um gerador de token: {{ carf_field() }} ; que pela documentação do laravel, serve como uma "sigla" para as chaves do php [<?php php>] e comando Echo >> se usar inspecionar na tela deve encontrar a seguinte linha [<input type="hidden" name="_token" value="..token com letras e números..">]
- usando o artisan: obrigatório estar dentro do diretório raiz do projeto, onde fica o arquivo do artisan, para usar o console de comandos, ex: [c:\pastas..\estudos_laravel\projeto1]


---
CONTINUAR AQUI >> aula 6/26
<https://www.udemy.com/course/introducao-ao-laravel-53/learn/lecture/6718262#notes>