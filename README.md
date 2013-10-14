##  Summary

Geobot is a Java-based IRC bot based on the
[PIRC](http://www.jibble.org/pircbot.php) framework designed Twitch.


For more information about the Ackbot implementation, please see
[Ackbot](http://bashtech.net/wiki/Ackbot).

##  Features

  * Link filtering w/ permitted domains
  * Highly configurable caps filtering
  * Custom info triggers
  * Topic / Status commands 
  * Viewers and bitrate commands
  * Poll and random number giveaways 

##  Issues/Feature Requests

PM [george](http://www.twitch.tv/message/compose?to=george) on Twitch

##  Commands

###  Note about prefixes

This documentation uses the default command prefix of `!`. This can be changed on the channel level using: `!set prefix`.

###  General Channel

  * `!topic [new topic]` - All/Mods - Displays and sets the topic. If no topic is set, Twitch channel title will be returned 
  * `!viewers` - All - Displays the number of viewers 
  * `!bitrate` - All - The current broadcast bitrate 
  * `!uptime` - All - Stream starting time and length of time streamed 
  * `!music` - All - Displays what you are currently listening to on Last.fm 
  * `!steam` - All - Display Steam profile, current game and server 
  * `!bothelp` - All - Displays link bot help documents 
  * `!commercial` - Owner - Runs a 30 second commercial. You must contact the bot maintainer to follow your channel with the bot's account and add the bot as a channel editor first. This command is also supported in !repeat.
  * `!game [new game - optional]` - All/Owner - Displays the current Twitch game. Optional - specify a new game to set. (Bot must be channel editor to update)
  * `!status [new status - optional]` - All/Owner - Displays the current Twitch status. Optional - specify a new status to set. (Bot must be channel editor to update)
  * `!followme` - Owner -  Forces the bot to follow your channel. Necessary for !game and !status updates or commercials.


### Fun 

  * `!throw [object]` - All - Throws object 

###  Moderation and Modes - Mods 


  * `+m` - Slow mode on 
  * `-m` - Slow mode off 
  * `+f` - Followers only mode on 
  * `-f` - Followers only mode off 
  * `+s` - Subscribers only mode off 
  * `-s` - Subscribers only mode off 
  * `+b [user]` - Bans a user 
  * `-b [user]` - Unbans a user 
  * `+k [user]` - Timeouts a user 
  * `+p [user]` - Purges a user 

  * `!clear` - Clears chat 
  * `!modchan` - Toggle command access between mod only and everyone 

###  Custom, Custom Repeat, Custom Scheduled, AutoReplies

  * `!command add [name] [text]` - Ops - Creates an info command (!name) 
  * `!command delete [name]` - Ops - Removes info command (!name) 
  
  
  * `!repeat add [name] [delay in seconds] [message difference - optional]`
  * `!repeat delete [name]`
  * `!repeat on/off [name]`
  * `!repeat list`

The repeat command will repeat a custom trigger every X amount of seconds passed. Message difference allows you to prevent spamming an inactive channel. It requires Y amount of messages have passed in the channel since the last iteration of the message. The default is 1 so at least one message will need to have been sent in the channel in order for the repeat to trigger.

  * `!schedule add [name] [pattern] [message difference - optional]`
  * `!schedule delete [name]`
  * `!schedule on/off [name]`
  * `!schedule list`

Schedule is similar to repeat but is designed to repeat at specific times such as 5pm, hourly (on the hour), semihourly (on 0:30), etc. `pattern` accepts: hourly, semihourly, and [crontab syntax**](http://i.imgur.com/j4t8CcM.png).

Examples:

 * `!schedule add youtube hourly 0` - This will repeat the !youtube command every hour on the hour.
 * `!schedule add ip *_*_*_*_* 0` - This will repeat the !ip command every minute.
 * `!schedule add texture *_5_*_*_* 0` - This will repeat the !texture at 5am every day.

\*\* **Replace the spaces in crontab syntax with _**

 * `!autoreply list` - Ops - Lists current autoreplies
 * `!autoreply add [*patten*] [response]` - Ops - Adds an autoreply triggered by \*pattern\* with the desired response. Use * to denote wildcards and _ to denote spaces in the pattern.
 * `!autoreply remove [number]` - Ops - Removes the autoreply with that index number. Do !autoreply list for those values.

###  Settings

  * `!links on/off` - Owner - Toggles link filtering on and off 
  * `!permit [name]` - Mods - Permits name to post 1 link 
  * `!pd add/delete/list` - Owner - Configures permanently permitted domains 
  
  
  * `!caps on/off` - Owner - Toggle cap filtering on and off 

Filtered messages must match all three of the below settings:

  * `!caps percent [int (0-100)]` - >= this percentage of caps per line 
  * `!caps mincaps [int]` - >= this number of caps per line 
  * `!caps minchars [int]` - total characters per line must be >= this 
  * `!caps status` - Displays the current values 
  
  
  * `!banphrase on/off` - Turns filter on/off
  * `!banphrase list` - Lists filtered words
  * `!banphrase add [word string]` - Adds string to filter - Accepts direct regular expressions (Prefix with REGEX:)
  * `!banphrase delete [word string]` - Removes string from filter

  * `!symbols on/off` - Turns symbols filter on/off. Covers ASCII symbols, unicode classes for box drawings, block elements and geometric shapes also select other spammed characters.
  Filtered messages must match both of the below settings:

  * `!symbols percent [int (0-100)]` - >= percentage of symbols
  * `!symbols min [int]` - >= number of symbols per line
  * `!caps status` - Displays the current values

  * `!emotes on/off` - Owner - Toggle emote spam filtering on and off 
  * `!emotes max [int]` - Max number of emotes allowed 

  * `!set [option] on/off` - Owner 
    * `topic` - Enables the !topic command 
    * `filters` - Global toggle for cap and link filters 
    * `throw` - Enables the !throw command 
    * `signedkicks` - Enables announcing cap and link kicks 
    * `lastfm [username/off]` - Sets username to use with !music command
    * `maxlength [num of chars]` - Maximum allowed message length
    * `steam [ID]` - Sets your Steam ID. Must be in [SteamID64](http://steamidconverter.com/) format and profile must be public 
    * `mode [(0/owner),(1/mod),(2,everyone),(-1, "Admin mode")]` - Sets the minimum access to use any bot commands. Options are either owner, mod, everyone, or "Admin mode". Specifying no argument will display current setting. Also see !modchan 
    * `commerciallength [30/60/90/120/150/180]` - Lenth of commercials to run with
    * `filterme` - Toggle /me block filter
    * `enablewarnings [on/off]` - Enabled a lesser timeout for first offensive of a filter (10 second timeout)
    * `timeoutduration [seconds]` - Sets the duration for filter offenses (after warning if enabled)
    * `tweet [String w/ replacements]` - Format for Click to tweet message.
    * `prefix [character` - Sets the command prefix. Default is "!"
  
  
  * `!regular add/delete/list [name]` - Owner - Adds a "regular". Regulars don't need permission to post links 
  * `!mod add/delete/list [name]` - Owner - Adds a "moderator". Moderators have access to all the bot commands the same way mods/ops do. Sometimes the bot does not recognize peoples op status do to issues with their IRC implementation so this is a way to explicitly add them. Channel owner automatically gets this status 
  * `!owner add/delete/list [name]` - Owner - Gives a user owner permissions on a channel 

###  Poll, Giveaway, Raffle

  * `!poll create [vote options]` - Ops - Creates a new poll with specified options. (ex "!poll create pie cake") 
  * `!poll start/stop` - Ops - Starts or stops the poll 
  * `!poll results` - Ops - Displays poll results
  * `!vote [option]` - All - Votes in the poll.
  
  
  * `!giveaway create max-number [duration]` - Ops - Creates a number-selection based giveaway with numbers from 1 - max. Duration is an optional value in seconds after which the giveaway will stop. Specifying a duration will auto-start the giveaway and stop will not need to be executed 
  * `!giveaway start/stop` - Ops - Starts or stops the giveaway entry 
  * `!giveaway results` - Ops - Displays winner(s) 
  * `!ga` - Alias for !giveaway
  
  
  * `!raffle` - Enters sender in the raffle. 
  * `!raffle enable/disable` - Enables entries in the raffle. 
  * `!raffle reset` - Clears entries. 
  * `!raffle count` - Displays number of entries. 
  * `!raffle winner` - Picks a winner. 


### Bot General

  * `!join` - Request bot to join your channel 
  * `!rejoin` - Force bot to attempt to rejoin your channel 
  * `!leave` - Owner - Removes the bot from channel 

###  Admin

Admin nicks are defined in global.properties. Twitch Admins and Staff also have access.

  * `!bm-join [#channelname]` - Joins channelname  
  * `!bm-leave [#channelname]` - Leaves channelname   
  * `!bm-rejoin` - Rejoin all channels   
  * `!bm-reconnect` - Disconnects all bots and allows them to "auto-reconnect" 
  * `!bm-global [message]` - Sends a message to all channel the bot is in
  * `!bm-loadglobalfilter` - Reload the global spam filter

### String Replacement

Adding dynamic data to bot message is also supported via string substitutions. The following substitutions are available:

  * `(_GAME_)` : Twitch game
  * `(_STATUS_)` : Twitch status
  * `(_VIEWERS_)` : Viewer count
  * `(_CHATTERS_)` : Number of users in chat
  * `(_STEAM_PROFILE_)` : Link to Steam profile (Steam account must be configured)
  * `(_STEAM_GAME_)` : Steam game (Steam account must be configured)
  * `(_STEAM\_SERVER_)` : Server you are playing on with a compatible (ie SteamWorks) game (Steam account must be configured)
  * `(_STEAM_STORE_)` : Link to Steam store for the game you are playing (Steam account must be configured)
  * `(_SONG_)` : Scrobbled Last.fm track name and artist (Last.fm account must be configured)
  * `(_BOT_HELP_)` : Bot's help message. See bothelpMessage in global.properties.
  * `(_TWEET_URL_)` : Click to tweet URL See !set tweet.

  Example:
  `!command add info I am (\_PROFILE\_) and I'm playing (\_STEAM\_GAME\_) on (\_STEAM\_SERVER\_) listening to (\_SONG\_)`

  Output:
  `I am http://bit.ly/321nds and I'm playing FTL: Faster Than Light on (none) listening to Wings of Destiny by David Saulesco`