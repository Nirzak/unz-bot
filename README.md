<div align="center">

# Unarchiver Bot

## A Telegram bot to extract various types of archives

<img src="https://telegra.ph/file/d4ba24682e030fc58613f.jpg" alt="Unzip logo" width="200" height="200">

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black) [![DeepSource](https://app.deepsource.com/gh/EDM115/unzip-bot.svg/?label=active+issues&show_trend=true&token=17SfwVx77dbrFlixtGdQsQNh)](https://app.deepsource.com/gh/EDM115/unzip-bot/?ref=repository-badge)

[![Unzip-Bot Analytics](https://repobeats.axiom.co/api/embed/5c857b55b42dd8235388093858b74341f6c679ac.svg)](https://github.com/EDM115/unzip-bot/pulse)

</div>

## Features 👀

- Extract all format of archives like `rar`, `zip`, `tar`, `7z`, `tar.xz`, …
- Supports password protected archives
- Extract archives from direct links
- Broadcast messages to users
- Ban/Unban users from using your bot
- Send logs in a private channel/group
- Can run only one extract per user at a time
- Fast to answer and process tasks
- Thumbnail can be set
- Problems can be directly reported
- Can send a message to a specific user
- Get infos about users
- Can rename files
- Able to process splitted archives (`.001`)
- And some other features 🔥 Dive into the code to find them 🤭


## Config vars 📖

- `APP_ID` - Your APP ID. Get it from [my.telegram.org](my.telegram.org)
- `API_HASH` - Your API_HASH. Get it from [my.telegram.org](my.telegram.org)
- `BOT_OWNER` - Your Telegram Account ID. Get it from [@MissRose_bot](https://t.me/MissRose_bot) (Start the bot and send `/info` command).
- `BOT_TOKEN` - Bot Token of Your Telegram Bot. Get it from [@BotFather](https://t.me/BotFather)
- `MONGODB_URL` - Your MongoDB URL ([**tutorial here**](./CreateMongoDB.md))
- `LOGS_CHANNEL` - Make a private channel and get its ID (search on Google if you don't know how to do). Using a group works as well, just add [`Rose`](https://t.me/MissRose_bot?startgroup=startbot), then send `/id` (In both cases, **make sure to add your bot to the channel/group as an admin !**)

## Commands ✍️

Copy-paste those to BotFather when he asks you for them

```
commands - Get commands list
mode - Upload as Doc 📄 / Media 📺
addthumb - Add custom thumbnail
delthumb - Remove your thumbnail
stats - Know if bot is overused
clean - Cancel on-going process
help - In case you need 😭
```

## Deploy 🚧

Deploying is easy 🥰 You can deploy this bot in Heroku or in a VPS ♥️  
**Star 🌟 Fork 🍴 and Deploy 📤**

> ⚠️ Note :
> We are using arch linux. But why 🤔
> 
> Because arch's p7zip package is the only maintained version of the [original p7zip](http://p7zip.sourceforge.net/) package with some additional features

---

#### The lazy way

[![Deploy me 🥺](https://www.herokucdn.com/deploy/button.svg)](https://www.heroku.com/deploy?template=https://github.com/Nirzak/unz-bot)  
(if you're in a fork, make sure to replace the template URL with your repo's one)

---

#### The easy way

+ Install [Docker](https://www.docker.com/) then restart your computer

```bash
git clone https://github.com/Nirzak/unz-bot.git
cd unzip-bot
nano .env
docker build -t edm115/unzip-bot .
```

+ Open Docker Desktop, go on the Images tab, click on the Run button
+ On Optional settings, fill the env variables

---

#### The legacy way

```bash
git clone https://github.com/Nirzak/unz-bot.git
cd unzip-bot
pip3 install -r requirements.txt
```

+ Install required dependencies  
  Arch Linux : `sudo pacman -S p7zip`  
  Ubuntu/Debian : `sudo apt-get install p7zip-full p7zip-rar`
+ Edit `.env` with your own values

```bash
chmod +x start.sh && ./start.sh
```

---

**DONE 🥳 enjoy the bot !** Be sure to follow me on [Github](https://github.com/EDM115) and Star 🌟 this repo to show some support 🥺

## How to Build after changes ?

#### Trust GitHub Actions

+ Add new Actions secrets to the repo :
  + `DOCKER_USERNAME` : all in lowercase
  + `DOCKER_TOKEN` : one with all rights, here : https://hub.docker.com/settings/security
+ Go in Actions tab, 2 workflows are here for ya :
  + `Build Docker Image` : Check if it builds without errors
  + `Publish Docker Image` : Rebuild && publish

#### Do it manually

+ Go in the repo's folder

```bash
docker build --no-cache -t Nirzak/unz-bot .
docker run -d -v downloaded-volume:/app/Downloaded -v thumbnails-volume:/app/Thumbnails --env-file ./.env --network host --name unzip-bot-container edm115/unzip-bot
docker start unzip-bot-container
# if you want to check something
docker exec -it unzip-bot-container sh
docker logs unzip-bot-container
# once you're done
docker stop unzip-bot-container
```

+ If you wanna publish :

```bash
docker tag edm115/unzip-bot Nirzak/unz-bot:latest
```

*(replace `Nirzak` with your docker hub username, `unz-bot` with the repo's name and `latest` whith whatever you want)*

```bash
docker login
```

*login and don't mind the errors*

```bash
docker push edm115/unzip-bot:latest
```
