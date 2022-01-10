> ***CUSTOM PREFIX SYSTEM ON PYCORD BY MYSQL***
**• IMPORTS**
```py
import discord
from discord.ext import commands
import mysql.connector
```
**• DB CONNECT**
```py
try:
  db_conn = mysql.connector.connect(
    host='localhost',
    user='admin',
    password='123',
    database='admin_bot',
    port=int(3306)
  )

  cursor = db_conn.cursor()
except:
  print('mysql error!')
  exit()
```
**• DEFINE GET PREFIX**
```py
def get_prefix(client, message):
  cursor.execute("select prefix from prefixes where guildid = %s", [message.guild.id])
  result = cursor.fetchall()[0][0]
  return str(result)
```
**• DEFINE BOT**
```py
bot = commands.Bot(command_prefix=(get_prefix))

@bot.event
async def on_ready():  # startup
  print('Bot is Ready!')
```
**• COMMAND CHANGE PREFIX**
```py
@bot.command()
@commands.has_permissions(administrator=True)
async def change_prefix(ctx: commands.Context, prefix):
    cursor.execute("update prefixes set prefix = %s where guildid = %s", [prefix, ctx.guild.id])
    db_conn.commit()
    await ctx.reply(f'Success!\nNow prefix is - **`{prefix}`**')

@bot.command()
async def ping(ctx: commands.Context):
  await ctx.reply(f'Ping is {str(round(bot.latency * 1000))}ms')
```
**• RUNNING BOT**
```py
bot.run('token')
```