
# FundaBot



Tired of looking for houses? Always responding just a bit too late? Hiring an intern to check funda for you is too expensive? Well look no further! This is a puppeteer based discord bot that checks Funda (a Dutch housing website) for you 4x a day and pings the user when it finds something new. 





## Features

- Individual user profiles and search parameters
- Searches 4x a day (adjustable via Cron schedule)
- Pings you specifically the moment it finds something in a discord channel of your choice
- Also sends a random €2.000.000+ house every morning to let you know the bot didn't die and to make you hate the current market even more 
- That's it. What else should it do, buy the house for you?


## Installation

There are two ways to run the bot. The first is to use it as a discord bot that pings you when it finds something. If you want to do this, go down to the section titled ''set up discord bot''. You can also use the scraper without a discord bot and write something yourself to notify you (like an email). In that case, go through checkFunda.js and remove anything that has to do with sending things in discord channels. 

### Set up as discord bot
First clone the github repo and save it somewhere on a PC with node.js installed. Go to the folder and run npm install to set up the dependencies. 

`npm install` 


Secondly, go to the discord [developer portal](https://discord.com/developers) and set up your own discord bot: 
- Click "new application" and give it a name (any name will do)
- In the menu on the left, go from 'General Information' to 'Bot' and give the bot a name (again, any name will do)
- Click 'reset token' and make sure you **COPY** the bot token that it gives you. You will need this token to make sure the script can use the bot
- Optionally add a funny icon to the bot that replaces the 'Funda' text in the Funda logo with some profanity of your choice

After this is done you can open checkFunda.js with your IDE or text editor of choice and add the bot token into the 'discordBotToken' variable as a string. Additionally, invite the bot to a discord server that you have privileges in (or make a new one) and make sure it has the correct rights to send messages in the channel you want it to ping users in.

In principle the bot is now ready to operate, but it still needs to know who to look for and what to look for. You can set up multiple users and profiles if you want to. For each user you will need to know their discord user ID and the channel ID in which you want them to be pinged. We'll figure out those IDs now. 

In Discord, go to User settings --> advanced and enable 'developer mode'. Once you have done this you can right click on any user and copy their user ID. You can also right click on channels and copy the channel ID. 

Finally we need the bot to know what you're looking for. To do this, go to funda.nl and set up a search with all the filters that are relevant for you. You can include anything you like. Price ranges, areas to search, whether or not to have a bathtub, energy labels etc. Once you are happy with your filter copy the URL from your browser, go back into checkFunda.js and make a new user record in 'peopleAndSearchRequests' using this format: 

    "your name": {
        "searchURL": "https://www.funda.nl/zoeken/koop?selected_area=%5B%22elst-ge",
        "userID": "YOUR-USER-ID",
        "channelID": "YOUR-CHANNEL-ID"
    }
The bot uses your search URL parameters to check funda for you. Start the bot by running checkFunda.cmd (on windows) or by running node checkFunda.js. 





## Authors

- [Jordie Eskes](https://www.github.com/skuderos)

