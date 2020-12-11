# yagCCs
This repository is meant for all the custom commands I've been making over time. Most of which are meant for VtM play by post servers, but they can be adapted to work with whatever you need for your custom commands.  
The bot these commands are used with is yagpdb, a moderation bot.
  
# Commands:  
## InitPositions
This command is to initialize the messages that the poitions command will edit. pick a channel where the messages will be tracked, and use `-initPositions`  
  
## Position  
When you want to add a character to the tracker, you do: `-Position {Sect} {Position} {"Character Name"} {@mentionUser} {Clan/Seat}`  
When you want to remove a character from the tracker, you do `-Position {Sect} {Position} {Clan/Seat}`  
**Sect can be:** Anarch, Sabbat or Camarilla  
**Position can be:** Any of the positions listed with (Status #) behind its name in the channel.   
**Character name:** Make sure to put them between "quote marks" because of spaces and such.  
**@mentionUser** this is rather obvious I recon  
**Clan/Seat** this one seems a little odd, but it's neccecary. When adding Primogen or ClanWhip, add the Clan name (copy them from the list if need be) The current only one with a space in its name is the Banu Haqim, I replaced the space with a `-` instead  
Any of the other positions that can have more than 1 character in it, you can add one of the following "firstSeat, secondSeat, or thirdSeat"  
  
It looks like a lot, but we're almost there.  
Lastly I have to note, Upper case letters, and their placement are **very** important. firstSeat has the S in uppercase, but not the f from first. **important**
all Clans and Sects and Positions have their first letter in upper case. again **important**  
  
  
Here's an example  
`-Position Camarilla Prince "Some Name" @userMention`  
`-Position Camarilla Primogen "Some Name" @userMention Malkavian`  
`-Position Anarch Cameleon "Some Name" @mentionUser firstSeat`  
  
Removing a character goes almost the same way  
`-Position Camarilla Prince`  
`-Position Primogen Malkavian`  
`-Position Anarch Cameleon firstSeat`  
  
## InitTracker  
This command initializes the character tracker by clan and sect. All of the clans/sects should have their own roles to mention. run -initTracker once in the chosen channel. From now on, that message will be edited, store the messageID in addCharacter together with channelID  
  
## addCharacter  
Add or remove, the command is the same.  
`-addCharacter {Clan} {Sect} {number}`  
{Clan} is each of the roles mentioned in the message, but **don't** mention the roles in the command. Type them out with `-` instead of spaces.  
{Sect} is the same as clans, but now for the sects.  
{number} can be positive, negative. Positive adds to the tracker, negative removes from the tracker.  
  
Note: In the bottom of the code for the tracker, where it says "editMessage ####### ####### $msg" , change the first ##### value into channelID and the second ### value into messageID of the message you just made with initTracker  
  
examples:  
add: `-addCharacter Malkavian Camarilla 1`  
remove: `-addCharacter Malkavian Camarilla -1`  
  
## Reset Commands  
  
### Create damages (Not required, but adds damage numbers to reset message)  
  
Any channel you wish to use this command in. It's a simple but required command to have your reset message display properly.  
If people breach, or do other masquerade damages, or if the SI has gotten attention of your city in some way. This command allows you to track the damage done.  
`dmg "Damage Type" #` is the command.   
`#` can be positive or negative numbers, to increase or reduce the damage.  
**"Damage Type"** is simply one of the two **"Masquerade Damage"** or **"SI Attention"** (make sure to use the capital letters where I just wrote them in the examples)  
  
Before the first use, use this snippet of code instead first, so that the db items are set.  
```go
{{ $damages := sdict "Masquerade Damage" 0 "SI Attention" 0 }}  
{{ dbSet 0 "damages" $damages }}  
```  
  
### Exp messager 
  
This is a relatively easy command, it starts with a trigger which I have set to `-exp` and the arguments follow in groups of 2, repeated untill the message limit has been reached.  
"Character Name" within quotation marks, and an exp value as second argument.   
So as example:  
`-exp "Character One" 2 "Character Two" 4 "Character Three" 3 "Character Four" 1 .....` etc.  
  
### list Channels (Required for Reset command - per IC Channel to display) 
  
`chnlList` this command adds channels to the list that the "reset" command uses to send a reset message in all the IC channels.  
This one can be used in the following ways:  
`-chnlList show` this makes the bot show you **all** the channels it currently has listed for those messages  
`-chnlList #somechannel` this adds that channel to the list. Make sure it's a mentioned channel  
`-chnlList #somechannel {del | delete | remove }` any one of the three words on the end will do, this deletes the channel from the list.  
  
### Weather Randomiser  (Not required, but adds damage numbers to reset message)
  
`-weather {season}` give any season as argument to this command, and it will randomise a weather pattern given by some hardcoded weather phenomena. Wind with speed, temperature, clouds or sun. the works. Can use some editing, but it works like a charm for now.  
  
### Reset Command  
  
This command will message in all channels from the "List Channels" command, and in the announcement channel that Reset has happened.  
In the Announcement channel it will display a general message with damage numbers ("Damage command") and custom additional messaging. In the commented parts it the code itself describes what parts of the message you can or can't edit.
it's usage is simple. `-Reset` in whatever channel you like. After using this command, I personally use the weather command too. But I'm thinking for later updates that I make this command run the weather command for you.
