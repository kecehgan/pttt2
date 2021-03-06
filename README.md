# Telegram Airdrop/Bounty Bot in Node.JS, using Telegraf.js

## What is this repository about?
This repository lets you run and configure a Telegram bot, easily, in order to interact with user input, manage data with a referral system built in!

This bot lets you store users data, generate a referral link and calculate the number of referrals.

## How to create the bot

### Step 1: create a 'user bot' and connect it with Node.js
- Open Telegram application on your computer/web;
- Contact BotFather through Telegram here: https://telegram.me/BotFather. This bot will be used to create your bot;
- As image suggests, follow those steps:
![image](http://i.imgur.com/POZq2tq.png)
- BotFather will provide you an API key. This API key is used to make requests to Telegram API in order to listen messages from your bot user, make bot answer accordingly and much more. Save it for next step.

### Step 2: configure your Node.js application
- Create config.js in the repository root with this content. Replace API_TOKEN with the API key you got from BotFather and replace the "your database connection string" with the correct connection string for your mongodb:
```javascript
module.exports = {telegraf_token:'API_TOKEN',
database:'Your database connection string',};
```

- Install dependencies:
```
npm install
```
This will install all dependencies in `package.json` so just `telegraf` in order to use Telegram API.

Done! Your bot is now configured.

## Run the bot
- Start your application:
```
npm start
```
If it prints:
```
connected to mongodb
```
...congratulations! Now bot will do what you want.

![image](https://i.imgur.com/P7CtZ7r.png)

## Secure your API key
In .gitignore:
```
config.js
```
API key will not be published inside your GitHub repository.
I have separated configuration logic from application logic in order to secure this key, but in a production environment it might not be enough.

Secure your API key as much as possible.
If your key gets stolen --- Bad things could happen with your bot.

If you're working on this repository with someone else, I suggest to NOT publish config.js but to share your configuration file privately with your collaborators OR let them build their own 'bot-users' with their own API keys.

# Documentation
I have personally commented my own code in order to make things as much clear as possible.


For example, listening a command:
```javascript
// Command example, pretty easy. Each callback passes as parameter the context.
// Context data includes message info, timestamp, etc; check the official documentation or print ctx.
bot.command('start', (ctx) => ctx.reply('Bot started.'));
```

Hear a word in a sentence:
```javascript
// Hears, instead of command, check if the given word or regexp is CONTAINED in user input.
bot.hears('ymca', (ctx) => ctx.reply("*sing* It's fun to stay at the Y.M.C.A.!"));
```

You can also use regexp, for example this one checks case-insensitive version of the word:
```javascript
bot.hears(/torino/i, (ctx) => ctx.reply("Someone said Torino!?"));
```

## Tip jar
```
0xd6c7B10Bb1132464d8B1e64fCDd97e576063D4a2
```



For more informations, check Telegraf API: https://github.com/telegraf/telegraf.
For inline support results, check: https://core.telegram.org/bots/api#inlinequeryresult.
