import telebot
from telebot import types
import random
from flask import Flask
import threading

# 🔑 Токен и ID админа
TOKEN = "ТОКЕН"
ADMIN_ID = 12345678
bot = telebot.TeleBot(TOKEN)

app = Flask("")

@app.route("/")
def home():
    return "✅ Bot is running!"

def run():
    app.run(host="0.0.0.0", port=8080)

def keep_alive():
    t = threading.Thread(target=run)
    t.start()

# --- твой код бота ниже ---

print("✅ Bot is running. Send /start to your bot.")

keep_alive()
bot.polling(none_stop=True, interval=0, timeout=20)
