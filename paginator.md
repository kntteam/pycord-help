> ***PAGINATOR ON PYCORD***

**• IMPORTS**
```py
import discord
from discord.ext import commands, pages
```
**• DEFINE BOT**
```py
bot = commands.Bot(command_prefix='!')

@bot.event
async def on_ready():
	print('Bot is Ready!')
```
**• MAKE A SLASH COMMAND ONLY FOR OUR SERVER (read the bottom later)**
```py
@bot.slash_command(guild_ids=[int(server_id)])
@commands.guild_only()
async def paginator(ctx: discord.ApplicationContext):
	e1 = discord.Embed(
        title='Первый эмбед',
        color=0x66CCCC,
        description=f'Это первый эмбед'
    )
    e1.set_footer(text='Made by KNTeam <3')
    e2 = discord.Embed(
        title='Второй эмбед',
        color=0x66CCCC,
        description=f'Это второй эмбед'
    )
    e2.set_footer(text='Made by KNTeam <3')
    e3 = discord.Embed(
        title='Третий эмбед',
        color=0x66CCCC,
        description=f'Это третий эмбед'
    )
    e3.set_footer(text='Made by KNTeam <3')
    embeds = [e1, e2, e3]

    page = pages.Paginator(pages=embeds, show_indicator=True, show_disabled=False)
    await page.respond(ctx.interaction, ephemeral=True)
```
**• START UR BOT**
```py
bot.run('token')
```
**NOW CHECK THIS COMMAND ON YOUR SERVER**
```discord
/paginator
```
**MORE INFORMATION [CLICK HERE](https://docs.pycord.dev/en/master/ext/pages/index.html#)**

`Для того, чтобы сделать команду общедоступной - уберите "guild_ids=[...]" из обозначения функции нашей команды.`
`Учтите, что кэширование слеш команд длится около часа`