# bot-discord-ia
import google.generativeai as genai

import discord

from discord.ext import commands
#la api_key va entre las comillas

genai.configure(api_key"")

intents = discord.Intents.default()

intents.message_content = True

bot = commands.Bot(command_prefix="!", intents=intents)

# Modelo Gemini

model = genai.GenerativeModel("gemini-1.5-flash")

# Generar respuesta

@bot.command()

async def gemini(ctx, *, pregunta: str):

    """Comando para preguntar a Gemini"""

    await ctx.send(" Pensando...")

    response = model.generate_content(pregunta)

    await ctx.send(response.text)

# Iniciar el bot
bot.run("el token va aquí")
