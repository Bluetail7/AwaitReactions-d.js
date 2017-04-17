AwaitReactions for Discord.js
Still in progress!!!

```
async function awaitReaction(index, emoji, time)
	{
		index.react(emoji)

		setTimeout(() => {
		var lookup = (index.reactions.find(y => y.emoji.toString() === emoji));
		if (lookup){return (lookup);} else {return (-1);}
		}, time)
	}
```
THIS DOESNT WORK

but this does
```
function createReaction(index, emoji_code)
	{return index.react(String.fromCharCode(emoji_code))}

function readReaction(index, emoji_string)
	{	//Use with SetTimeout and after create Reaction.
		var lookup = (index.reactions.find(y => y.emoji.toString() === emoji_string));
		if (lookup){return (lookup);} else {return (-1);}
	}

//EXAMPLE:
msg.channel.sendMessage("Simple test").then(x => {
	createReaction(x, 9876)
	setTimeout(() => {
		if (readReaction(x, 9876).count != -1)
			{msg.channel.sendMessage("I added a reaction")}
			else {msg.channel.sendMessage("Not even I reacted")}
	},5000)
})
```
