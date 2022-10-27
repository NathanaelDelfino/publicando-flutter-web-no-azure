## publicando flutter web no azure

Um estudo de como subir uma aplicação web feita em flutter, como aplicação no azure websites

#### Ferramentas utilizadas

* Flutter 3.3.5
* NodeJs 16.18.0
* Fillezila 

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

Agora temos de abrir o nosso projeto (Eu utilzei o VS Code), somente para alterar a pasta public para pasta que contem os arquivos do nosso projeto em flutter

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198334269-19797541-2cf1-4746-9e68-7db52a5238d8.png">
</br><i>Parte do código que deve ter seu nome trocado</i>
</p>

Note que não foi mexido em nada além do nome da pasta.

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198334577-006ef012-711a-400f-8729-0e9a8bbf92bd.png">
</br><i>Parte do código que deve ter seu nome trocado</i>
</p>

Caso queira garantir que está tudo certo, bastar executar no terminal o comando:
```
npm start
```
e carregar no seu navegador http://localhost:3000/#/ , onde irá lhe carregar a pagina o consolle do seu terminal ira ficar como na imagem a baixo

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198335452-8177e06d-db8f-49ff-b378-78e888751ea0.png">
</br><i>Tudo funcionando</i>
</p>


<div align="center">
<h1><b>Coisas a se fazer no Portal Azure</b></h1>
</div>

Para hospedar nossa aplicação no portal do azure vamos escolher o modelo de serviço como *Serviços de aplicativos*. 

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198321701-2c3f8927-9073-4e31-8fb6-f7ec3eff471f.png">
</p>

Na criação do nosso serviço de aplicativos, vamos definir nosso grupo de recursos (Um grupo de recursos é um conjunto de recursos que compartilham o mesmo ciclo de vida, permissões e políticas.), definir o nome da nossa aplicação, selecionar o nome da nossa aplicação, podemos deixar a publicação como código mesmo e selecionamos o serviço Node que irá executar nossa aplicação Web.

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198328149-f03c6a24-2138-4873-9664-2acef07083d6.png">
</p>
<p align="center">
<i>exemplo das configurações utilizadas</i>
</p>

Com as configurações definidas, podemos ir direto em *Revisar + Criar*, e podemos ir direto em criar na sequencia. 
Ao clicar em criar irá nos ser exibido a seguinte mensagem

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198329383-d8c4960f-0f88-4b1d-952e-9e8e71f3c435.png">
</br><i>criando o serviço</i>
</p>


Com o serviço criado, ao clicar no link vamos ter a seguinte o retorno
<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198331205-57829c5b-cd77-4671-80f5-db3767735a1b.png">
</br><i>Serviço hospedado rodando</i>
</p>

Agora podemos ir em Centro de implantação, para pegar os dados necessários para subir no aplicativo.

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198330747-30838644-a6b1-4213-a426-6e61d8ffce66.png">
</br><i>Centro de implantação</i>
</p>

No centro de implantação vamos ter três opções Settings, Logs e FTPS Credentials. A opção que vamos utilizar é a *FTPS credentials*, nela irá conter os dados necessários para que possamos subir os arquivos de nossa aplicação.

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198332049-7829c016-bb63-4d39-bfac-d0468352e6df.png">
</br><i>FTPS credentials</i>
</p>

No meu caso eu configurei o Filezilla como ferramenta para subir os arquivos para o site

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198332628-dde8d987-d1ac-4727-b708-48bf522843f2.png">
</br><i>Configuração realizada no FileZilla</i>
</p>

O próximo passo é basicamente pegar a pasta que configuramos o projeto em node, e subir para o FTPS no azure
<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198333331-8bc27b3f-0694-4853-989a-c7ea887626d0.png">
</br><i>arquivos do projeto</i>
</p>


 Após subir nossos arquivos podemos apagar o arquivo *hostingstart.html* que é um arquivo que o azure sobe quando criando a nosso serviço de aplicação
<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198337265-e0da40e0-33ab-4e9d-af83-d7f9fa601b64.png">
</br><i>apagar o arquivo hostingstart.html</i>
</p>

Agora só é necessiario que reiniciemos nosso serviço de aplicação no portal do azure, para isso basta ir na *OPÇÃO GERAL* e clicar em reiniciar na sequencia. 
<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198338600-ee490790-ae23-4478-94e3-2c6abb955db5.png">
</br><i>Reiniciando aplicação</i>
</p>


Se tudo estiver certo agora podemos acessar no aplicação flutter rodando, por meio do endereço que definimos ao criar o serviço, no meu caso https://flutter-web-no-azure.azurewebsites.net , e é isso.

Its all Folks! ✌️
