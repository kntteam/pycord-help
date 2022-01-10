***TRANSLATE BDFD CODE TO PYTHON || ORIGINAL CODE BY @Prokro_TV#8469 (Prokro_TV)***

**• IMPORTS**

```py
import discord
from discord.ext import commands
import datetime
```

**• DEFINE MOSCOW TIME**

```py
offset = datetime.timezone(datetime.timedelta(hours=3))  # MOSCOW TIME
```

**• DEFINE BOT**

```py
bot = commands.Bot(command_prefix='!')

@bot.event
async def on_ready():
  print('Bot is Ready!')
```

**• DEFINE BOT MENTION TRIGGER FUNCTION**

```py
@bot.event
async def on_message(message: discord.Message):  # event -> trigger on message
    if bot.user.mentioned_in(message):  # Checking bot mention
        e = discord.Embed(  # Define embed
            description=f'Текст'  # Define text in embed
        )
        e.set_footer(text=f'{message.author.name}#{str(message.author.discriminator)} отправил сообщение в {datetime.datetime.now(offset).strftime("%H:%M:%S")}')  # Define footer
        await message.channel.send(embed=e)  # sending embed
```