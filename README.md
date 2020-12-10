# yagCCs
This repository is meant for all the custom commands I've been making over time. Most of which are meant for VtM play by post servers, but they can be adapted to work with whatever you need for your custom commands.  
  
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
  
Have fun tinkering!  
