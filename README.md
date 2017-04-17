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
