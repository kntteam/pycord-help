***JSON DATABASE***

***GUILD CONFIG EXAMPLE***

**• CREATE FILE "db.json"**

**CONTENT:**

```json
{}
```

**• IMPORTS AND BOT DEFINE**

```py
import discord
from discord.ext import commands
import json

bot = commands.Bot(command_prefix='!')

@bot.event
async def on_ready():
  print('Bot is Ready!')
```

**• FUNCTION -> TRIGGER WHEN BOT WAS INVITED TO SERVER**

```py
@bot.event
async def on_guild_join(guild: discord.Guild):  # define function -> trigger when bot was invited to guild
  try:
    lang = 'ru'  # standart lang = russian
    prefix = '!'  # standart prefix = !
    mod_comms = 1  # mod_comms default status is enabled
    standart_config = [lang, prefix, mod_comms]  # define list with standart config
    with open('db.json', 'r') as f:  # open db.json for (r)ead
      database = json.load(f)  # open this file like json as database
    database[str(guild.id)] = standart_config  # idk
    with open('db.json', 'w') as f:  # open db.json for (w)rite
      json.dump(database, f, indent=4)  # dumping that list
  except:
    print('error with on guild join trigger')
```

**• FUNCTION -> TRIGGER WHEN BOT WAS KICKED FROM SERVER**

```py
@bot.event
async def on_guild_remove(guild: discord.Guild):
  try:
    with open('db.json', 'r') as f:
      database = json.load(f)
    database.pop[str(guild.id)]
    with open('db.json', 'w') as f:
      json.dump(database, f, indent=4)
  except:
    print('error with on guild remove trigger')
```

⚠️ ***ВОЗМОЖНЫ ОШИБКИ*** ⚠️
**В СЛУЧАЕ ВОЗНИКНОВЕНИЯ ОШИБОК РЕШАЙТЕ ИХ САМИ. ОШИБКИ ПОЯВЛЯЮТСЯ В КОНСОЛИ.**

```
original = https://github.com/kntteam/pycord-help
```