AwaitReactions for Discord.js
Still in progress!!!
LOOKUP returns the Message.Reactions Collection

```
function awaitReaction(index, emoji, time)
	{
		index.react(emoji)

		setTimeout(() => {
		var lookup = (index.reactions.find(y => y.emoji.toString() === emoji));
		if (lookup){msg.channel.sendMessage(lookup);} else {msg.channel.sendMessage(-1);}
		}, time)
	}
```
You are only able to use the data without return, otherwise it will skip the timeout.

this works if you want to return:
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
