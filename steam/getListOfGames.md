# Get a List of stream games via Chrome

Goto all games on your profile

eg. [my profile](https://steamcommunity.com/profiles/76561198208160528/games/?tab=all)

sort by name on the top right *optional

open chrome development tools (ctrl + shift + I) and paste the following into the console.


```javascript
var names = document.body.getElementsByClassName('gameListRowItemName');
var gamesList = '';
for (var i = 0; i < names.length; i++)
{
	//console.log(names[i].innerText);
	gamesList += names[i].innerText + '\n';
}
```