***TRANSLATE BDFD CODE TO PYTHON || ORIGINAL CODE BY @Ffanyi × ∆  clown🃏#3726***

**• IMPORTS**
```py
import discord
from discord.ext import commands
import random
```
**• DEFINE BOT**
```py
bot = commands.Bot(command_prefix='!')

@bot.event
async def on_ready():
  print('OK')
```
**• HUG COMMAND ERROR HANDLER (optional)**
```py
@bot.event
async def on_command_error(ctx: commands.Context, error):
    if isinstance(error, commands.MemberNotFound):
        e = discord.Embed(
            title='Ошибка!',
            color=0xFFFFFF,
            description=f'Пользователь не найден!'
        )
        await ctx.reply(embed=e)
```

**• HUG COMMAND FUNCTION DEFINE**

```py
@bot.command()
@commands.guild_only()
async def hugging(ctx: commands.Context, args: discord.Member):
    hugged: discord.Member = args  # define args as hugged
    if hugged.mentioned_in(ctx.message):  # checking (idk why)
        e = discord.Embed(  # Define Embed
            color=0xFFFFFF,  # Define embed color
            description=f'**В обнимку {ctx.author.mention} обнял {hugged.mention}**'  # define embed description
        )
        pictures = [  # define pictures
            'https://cdn.weeb.sh/images/Sk-xxs3C-.gif',
            'https://cdn.weeb.sh/images/ryjJFdmvb.gif',
            'https://cdn.weeb.sh/images/HJ7lY_QwW.gif',
            'https://cdn.weeb.sh/images/rkx1dJ25z.gif',
            'https://cdn.weeb.sh/images/rJ_slRYFZ.gif',
            'https://cdn.weeb.sh/images/rkIK_u7Pb.gif',
            'https://cdn.weeb.sh/images/r1kC_dQPW.gif',
            'https://cdn.weeb.sh/images/Hyec_OmDW.gif',
            'https://cdn.weeb.sh/images/HytoudXwW.gif',
            'https://cdn.weeb.sh/images/Hk0yFumwW.gif'
        ]
        try:  # trying attach the image to embed
            e.set_image(url=random.choice(pictures))
        except:  # if image attaching is failed
            e.set_footer(text='Ошибка при прикреплении фото')
        await ctx.send(embed=e)  # sending the embed
```

**• Bot Running**

```py
bot.run('token')
```
