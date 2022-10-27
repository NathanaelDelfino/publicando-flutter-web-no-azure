## publicando flutter web no azure

Um estudo de como subir uma aplicação web feita em flutter, como aplicação no azure websites

#### Ferramentas utilizadas

* Flutter 3.3.5
* NodeJs 16.18.0

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198142894-28e61214-0308-4de4-a174-f67f2a534c61.png">
</p>



<div align="center">
<h1><b>Coisas a se fazer no flutter</b></h1>
</div>

Com a aplicação em flutter criada o primeiro passo para a publicação é realizar o _build web_ da aplicação. Então na sua IDE ou via CMD (com a pasta do flutter setada) execute : 

```
Flutter build web
```

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198140778-cca342e2-149d-46ea-b012-9f1af7522ef3.png">
</p>
<p align="center">
_imagem de exemplo_
</p>

Apos gerar o comando o flutter ira criar uma pasta chamada **Web** dentro da pasta build **Build**

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198141617-6cd21899-5cc7-4729-b914-627ed5d6aee6.png">
</p>

Por em quanto vamos seguir em frente, mas vamos voltar a utilizar essa pasta em outro momento.


<div align="center">
<h1><b>Coisas a se fazer no NodeJS</b></h1>
</div>

Agora vamos para a criação no projeto em Node.Js que irá executar e exibir nosso projeto em Flutter nos serviços do Azure. 
(_obs: Até a criação desse tutorial, ainda não se é possível subir de maneira nativa ou direta as aplicações geradas no flutter web, para isso que iremos criar uma aplicação em nodejs._)

Com o nodejs instalado em nossa maquina vamos criar um projeto em Node que irá amazenar nossa aplicação (_obs: não se esqueça de apontar para uma pasta separada dos fontes do seu projeto em flutter, para não misturar os projetos_)

O primeiro comando a ser executado é executar o comando que irá o comando que irá criar o projeto em node:

```
npx express-generator ProjetoNodeDoProjetoQueIraRodarNossoAplicativoFlutter --view ejs
```

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198144421-a19eb34f-6888-444b-9321-e85ebd490c5f.png">
</p>

Na sequencia vamos mandar ele gerar todos os pacotes necessários para execução
```
cd ProjetoNodeDoProjetoQueIraRodarNossoAplicativoFlutter && npm install
```

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198145075-102aa8d4-0e86-4409-9e01-795c93fe17a8.png">
</p>

Para validar se o projeto foi criado e teve seus pacotes restaurado com sucesso, podemos executar o seguinte comando.
```
DEBUG=ProjetoNodeDoProjetoQueIraRodarNossoAplicativoFlutter:* npm start
```
_obs: Se você estiver dentro da pasta ProjetoNodeDoProjetoQueIraRodarNossoAplicativoFlutter, execute apenas npm start_

Se estiver tudo certo, ao carregar a url http://localhost:3000/ irá exibir a seguinte tela 

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198145789-432a35b2-a5f5-44f9-a065-0d34e8cda8bc.png">
</p>

Com o projeto em node criado, agora vamos criar uma pasta chamada "flutter-web" dentro da pasta do nosso projeto, em seguida vamos pegar os itens de dentro da pasta web criada pelo nosso build do projeto em flutter, na sequencia colar dentro da nossa pasta "flutter-web".

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198146485-14d82558-486f-479a-864f-99dc69233a59.png">
</p>
<p align="center">
<i>imagem de exemplo da pasta criada</i>
</p>

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198146684-bc1f46c7-c97d-4865-865e-b3358934c248.png">
</p>
<p align="center">
<i>imagem de exemplo dos arquivos copiados para pasta</i>
</p>

<div align="center">
<h1><b>Coisas a se fazer no Portal Azure</b></h1>
</div>

Para hospedar nossa aplicação no portal do azure vamos escolher o modelo de serviço como *Serviços de aplicativos*. 

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198321701-2c3f8927-9073-4e31-8fb6-f7ec3eff471f.png">
</p>

Na criação do nosso serviço de aplicativos, vamos definir nosso grupo de recursos (Um grupo de recursos é um conjunto de recursos que compartilham o mesmo ciclo de vida, permissões e políticas.), definir o nome da nossa aplicação, selecionar o nome da nossa aplicação 
