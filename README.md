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
function createReaction(index, emoji_string)
	{return index.react(emoji_string)}

function readReaction(index, emoji_string)
	{	//Use with SetTimeout and after create Reaction.
		var lookup = (index.reactions.find(y => y.emoji.toString() === emoji_string));
		if (lookup){return (lookup);} else {return (-1);}
	}

//EXAMPLE 1, test:
msg.channel.sendMessage("Simple test").then(x => {
	createReaction(x, String.fromCharCode(9876))
	setTimeout(() => {
		var test =readReaction(x, String.fromCharCode(9876)).count //.count belongs to message.reactions' Collection
		if (test > 1){msg.channel.sendMessage(test + " people  added a reaction!")}
		else
		if (test === 1){msg.channel.sendMessage("I added a reaction")}
			else {msg.channel.sendMessage("Nobody reacted")}
	},5000)
})

//EXAMPLE 2, giveaway:
msg.channel.sendMessage("@all Giveaway").then(x => {
    createReaction(x, String.fromCharCode(55356,57217))
    setTimeout(() => {
        var test =readReaction(x, String.fromCharCode(55356,57217)).users //.users belongs to message.reactions' Collection
        if (test.size > 1){msg.channel.sendMessage(test.random().username + " won the giveaway!!")}
        else
        if (test.size === 1){msg.channel.sendMessage("I won the giveaway")}
            else {msg.channel.sendMessage("Nobody wanted it")}
    },5000)
})
```
