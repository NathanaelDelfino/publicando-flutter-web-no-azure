## publicando flutter web no azure

Um estudo de como subir uma aplicação web feita em flutter, como aplicação no azure websites

#### Ferramentas utilizadas

* Flutter 3.3.5
* NodeJs 16.18.0

<p align="center">
<img  src="https://user-images.githubusercontent.com/7662248/198142894-28e61214-0308-4de4-a174-f67f2a534c61.png">
</p>

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

Agora vamos para a criação no projeto em Node.Js que irá executar e exibir nosso projeto em Flutter nos serviços do Azure. 
(_obs: Até a criação desse tutorial, ainda não se é possível subir de maneira nativa ou direta as aplicações geradas no flutter web, para isso que iremos criar uma aplicação em nodejs._)

