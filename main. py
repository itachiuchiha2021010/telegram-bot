import telebot
import requests
import json

BOT_TOKEN = "8507553949:AAHJeT8Hq65Trj5lFyeCRwizXSphjdZhD9A"
OPENAI_API_KEY = "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"

bot = telebot.TeleBot(BOT_TOKEN)

def ask_openai(question):
    url = "https://api.openai.com/v1/responses"
    headers = {
        "Content-Type": "application/json",
        "Authorization": f"Bearer {OPENAI_API_KEY}"
    }

    data = {
        "model": "gpt-4.1-mini",
        "input": question
    }

    response = requests.post(url, headers=headers, json=data)

    try:
        return response.json()["output_text"]
    except:
        return "⚠️ Error: Something went wrong..."

@bot.message_handler(commands=['start'])
def start(message):
    bot.reply_to(message, "Hello! Bot is now active 🔥")

@bot.message_handler(func=lambda m: True)
def chat(message):
    reply = ask_openai(message.text)
    bot.reply_to(message, reply)

print("Bot running...")
bot.infinity_polling()
