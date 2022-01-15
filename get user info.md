> ### Get user info

**• IMPORTS**

```py
import discord
from discord.ext import commands
```

**• DEFINE BOT**
```py
bot = commands.Bot(command_prefix='!', intents=discord.Intents.all())

@bot.event
async def on_ready():
	print('Bot is Ready!')
```

**• DEFINE FUNCTION WITH COMMAND**

```py
@commands.slash_command(description='Get user info', guild_ids=[READ BOTTOM])
@commands.guild_only()
async def user(ctx: commands.Context, user: discord.Member = None)
	if user is None:  # The user wants to know information about themselves
		member = ctx.author
	else:
		member = user
	if member.bot is True:
		botStatus = "Yes"
	else:
		botStatus = "No"
	e = discord.Embed(
	title='Information about user',
	color=0xFFFFFF,
	description=member.mention
	)
	e.add_field(name='Tag:', value=f'*{str(member.name)}#{str(member.discriminator)}*', inline=False)
	e.add_field(name='ID:', value=str(member.id), inline=False)
	e.add_field(name='Top Role:', value=member.top_role.mention, inline=False)
	e.add_field(name='Color:', value=str(member.color), inline=False)
	e.add_field(name='Register date', value=member.created_at.strftime("%d.%m.%Y | %H:%M"), inline=False)
	await ctx.respond(embed=e, ephemeral=True)
```

**• RUNNING BOT**

```py
bot.run(token)
```

**• PS**
> **`In the event of errors, deal with them yourself. Errors are written in the console.`**
