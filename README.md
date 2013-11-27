Plataphorma
===========

Meteor pet project created to teach my students the following Meteor functionality: 

* Collection's publish/subscribe 
* Deps.autorun 
* Meteor.methods/call 
* Integration of non-Meteor code in compatibility folder (HTML5 games Alien Invasion and Froot Wars)
* Usage of allow to control client access to collections

![ScreenShot](/screenshot.png)


Plataphorma offers the possibility to run 2 different HTML5 games: Alien Invasion and Froot Wars. 

On the right side of the screen the best players of each game are shown, updated in real time each time a signed in player finishes a game. If no game is selected, the best players overall are shown.

On the left side of the screen a chatroom for the current game is available. Only signed in users can post messages. If no game is selected a general chatroom is shown.

The original code of the two HTML5 games integrated in this project is available here:
* Alien Invasion: https://github.com/cykod/AlienInvasion
* Froot Wars: http://www.wrox.com/WileyCDA/WroxTitle/Professional-HTML5-Mobile-Game-Development.productCd-1118301323,descCd-DOWNLOAD.html

Bootstrap style (file bootstrap.min.css) provided by http://bootswatch.com


Running the project
-------------------

A live version of this code is running here: http://plataphorma.meteor.com

To run the project locally, clone the repo and run ```meteor``` inside it. You can see in .meteor/packages that this Meteor project uses these packages:
* ```meteor remove autopublish```
* ```meteor remove insecure```
* ```meteor add bootstrap```
* ```meteor add accounts-ui```
* ```meteor add accounts-password```

* ``` 1) Click en botón del juego:
			- En el momento que hacemos click en cualquier botón de juego vemos que esto es controlado en client.js por
			  "Template.choose_game.events" donde vemos que dependiendo de la pestaña que seleccionemos se oculta o se enseñan 
			  contenedores. LINEA: 112-130
			  Es decir que cuando queramos sacar AlienInvasion tendremos que ocultar #gamecontainer y mostrar #container.
		      Cuando queramos sacar FroottWars tendremos que ocultar #container y mostrar #gamecontainer. Y cuando queramos
			  ocultar los dos juegos se ocultarán tanto #gamecontainer como #container.

* ``` 2) Se escribe mensaje chat sin estar autenticado:
			- Si escribimos un mensaje sin estar autenticado vemos que no nos deja porque necesitamos estarlo para poder 
			  escribir mensajes. Esto lo vamos a ver en "Template.input.events" donde si pasamos el filtro "if (Meteor.userId())"
			  donde esto es nuestro identificador de usuario, nos dejará insertarlo en la lista "Messages.insert", sino nos 
			  mostrará el mensaje de error "#login-error". 

3) Se escribe mensaje chat estando autenticado:
			- Si escribimos un mensaje sin estar autenticado vemos que ahora, a diferencia de antes, si nos deja escribir, y esto 
			  es debido a que ahora cuando nos pregunta por nuestro identificador ("if (Meteor.userId())") vamos a ser capaces de 
			  mostrarselo y por antes se insertara en la lista de Messages ("Messages.insert").

4) Se termina partida con puntuación alta sin estar autenticado:
			- Cuando jugamos a cualquiera de los juegos vamos a tener unas líneas de código, en las que le envio la información
			  a server.js. Esta llamada la vamos a efectuar entre las líneas 103 a 118 del fichero game.js y las recibiremos en 
			  el lado del servidor en las líneas 46 a 47 donde solamente vamos a procesarlas si tenemos el correspondiente ID que
			  nos identifique ("if (this.userId)").

5) Se termina partida estando autenticado:	
			- Ahora, al contrario que antes vamos a tener lo mismo pero esta vez cuando enviemos la puntuación si va a añadirse a
			  la lista de puntuaciones dado que esta vez si vamos a darle un identificador.

6) ¿Qué sale en consola cuando te autenticas (sign in)?
			- En la consola sale un current user que es un identificador aleatorio.

7) ¿Qué sale en consola cuando sales (sign out)?
			- Cuando haces sign out el current user nos lo pone a "null".
	
