import telebot
from telebot import types


TOKEN = "7809373895:AAFw9j5souz-B_VkGvaM3BN51TNKDSxwzoU"  
bot = telebot.TeleBot(TOKEN) 


# # Обработчик сообщений (будет отвечать тем же текстом)
# @bot.message_handler(func=lambda message: True)
# def echo_message(message):
#     bot.reply_to(message, message.text)  # Отправляем обратно тот же текст




@bot.message_handler(commands=['start'])
def start_message(message):
    bot.send_message(message.chat.id, "Привет! Я твой бот. Задай мне вопрос.")


@bot.message_handler(commands=['fuck'])
def start_message(message):
    bot.send_message(message.chat.id, "Fuck y stupid corel!!!")

@bot.message_handler(commands=['трындец'])
def start_message(message):
    bot.send_message(message.chat.id, "апупеть!")


    
@bot.message_handler(commands=['menu'])
def show_menu(message):

    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)

    btn1 = types.KeyboardButton("Привет")
    btn2 = types.KeyboardButton("Как дела?")
    btn3 = types.KeyboardButton("WTF")
    btn4 = types.KeyboardButton("calc")

    markup.add(btn1, btn2, btn3,btn4)    


    bot.send_message(message.chat.id, "Выбери действие:", reply_markup=markup)

@bot.message_handler(func=lambda message: message.text == "Привет")
def hello_response(message):    
    bot.send_message(message.chat.id, "Привет! Меня зовут Опенгеймер!") 


@bot.message_handler(func=lambda message: message.text == "Как дела?")
def hello_response(message):    
    bot.send_message(message.chat.id, "Дела хорошо!") 

@bot.message_handler(func=lambda message: message.text == "WTF")
def hello_response(message):    
    bot.send_message(message.chat.id, "FTW") 







@bot.message_handler(func=lambda message: message.text.lower() == "calc")
def calculator_start(message):
    bot.send_message(message.chat.id, "Введите операцию (+, -, *, /):")
    bot.register_next_step_handler(message, get_operation)

def get_operation(message):
    operation = message.text
    if operation not in ['+', '-', '*', '/']:
        bot.send_message(message.chat.id, "Некорректная операция! Попробуйте снова.")
        return
    bot.send_message(message.chat.id, "Введите первое число:")
    bot.register_next_step_handler(message, get_first_number, operation)

def get_first_number(message, operation):
    try:
        num1 = float(message.text)
    except ValueError:
        bot.send_message(message.chat.id, "Это не число! Попробуйте снова.")
        return
    bot.send_message(message.chat.id, "Введите второе число:")
    bot.register_next_step_handler(message, get_second_number, operation, num1)

def get_second_number(message, operation, num1):
    try:
        num2 = float(message.text)
    except ValueError:
        bot.send_message(message.chat.id, "Это не число! Попробуйте снова.")
        return
    result = None
    if operation == '+':
        result = num1 + num2
    elif operation == '-':
        result = num1 - num2
    elif operation == '*':
        result = num1 * num2
    elif operation == '/':
        if num2 == 0:
            bot.send_message(message.chat.id, "Деление на ноль невозможно!")
            return
        result = num1 / num2
    bot.send_message(message.chat.id, f"Результат: {result}")



bot.polling(none_stop=True)  # Запускаем бота в бесконечном цикле
