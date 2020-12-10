# yagCCs
This repository is meant for all the custom commands I've been making over time. Most of which are meant for VtM play by post servers, but they can be adapted to work with whatever you need for your custom commands.\n
\n
# InitPositions
This command is to initialize the messages that the poitions command will edit. pick a channel where the messages will be tracked, and use `-initPositions`
\n
# Position
When you want to add a character to the tracker, you do: `-Position {Sect} {Position} {"Character Name"} {@mentionUser} {Clan/Seat}`\n
When you want to remove a character from the tracker, you do `-Position {Sect} {Position} {Clan/Seat}`\n
**Sect can be:** Anarch, Sabbat or Camarilla\n
**Position can be:** Any of the positions listed with (Status #) behind its name in the channel. \n
**Character name:** Make sure to put them between "quote marks" because of spaces and such.\n
**@mentionUser** this is rather obvious I recon\n
**Clan/Seat** this one seems a little odd, but it's neccecary. When adding Primogen or ClanWhip, add the Clan name (copy them from the list if need be) The current only one with a space in its name is the Banu Haqim, I replaced the space with a `-` instead\n
Any of the other positions that can have more than 1 character in it, you can add one of the following "firstSeat, secondSeat, or thirdSeat"
\n
It looks like a lot, but we're almost there.\n
Lastly I have to note, Upper case letters, and their placement are **very** important. firstSeat has the S in uppercase, but not the f from first. **important**
all Clans and Sects and Positions have their first letter in upper case. again **important**\n
\n
\n
Here's an example\n
`-Position Camarilla Prince "Some Name" @userMention`\n
`-Position Camarilla Primogen "Some Name" @userMention Malkavian`\n
`-Position Anarch Cameleon "Some Name" @mentionUser firstSeat`\n
\n
Removing a character goes almost the same way\n
`-Position Camarilla Prince`\n
`-Position Primogen Malkavian`\n
`-Position Anarch Cameleon firstSeat`\n
\n
# InitTracker
This command initializes the character tracker by clan and sect. All of the clans/sects should have their own roles to mention. run -initTracker once in the chosen channel. From now on, that message will be edited, store the messageID in addCharacter together with channelID\n
\n
# addCharacter
Add or remove, the command is the same.\n
`-addCharacter {Clan} {Sect} {number}`\n
{Clan} is each of the roles mentioned in the message, but **don't** mention the roles in the command. Type them out with `-` instead of spaces.\n
{Sect} is the same as clans, but now for the sects.\n
{number} can be positive, negative. Positive adds to the tracker, negative removes from the tracker.\n
\n
Note: In the bottom of the code for the tracker, where it says "editMessage ####### ####### $msg" , change the first ##### value into channelID and the second ### value into messageID of the message you just made with initTracker\n
\n
examples:\n
add: `-addCharacter Malkavian Camarilla 1`\n
remove: `-addCharacter Malkavian Camarilla -1`\n
\n
Have fun tinkering!
