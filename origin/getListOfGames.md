# Get a List of origin games via Chrome

Log in to origin web page via chome browser

eg. [Goto your game library](https://www.origin.com/gbr/en-us/game-library)

open chrome development tools (ctrl + shift + I) and paste the following into the console.


```javascript
var gamesList = '';

var names = document.body.getElementsByClassName('origin-telemetry-gametile')

for (var i = 0; i < names.length; i++)
{
	var rawName = names[i].getAttribute('data-telemetry-ocdpath');
	var arrName = rawName.split("/");
	if(arrName[2] == "originqa-04")
		arrName[2] = "command-and-conquer"

	gamesList += arrName[2] + '\n';
}

console.log(gamesList);

```