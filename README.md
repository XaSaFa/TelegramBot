# Telegram Bot

Un bot de Telegram és un compte similar al dels usuaris de Telegram però amb la diferència que només pot executar accions programades.

[Aquí teniu una explicació més exhaustiva del que és un bot de Telegram.](https://core.telegram.org/bots)

# Requeriments

Què necessitem per fer un bot de Telegram?

1. Telegram: Primer necessitem un compte de Telegram.
2. Python: Màquina amb un programa de Python executant-se.

# Telegram

## 1.- Crear el bot

Per crear un bot de telegram hem de buscar un compte anomenat BotFather y enviar-li el missatge "/newbot":

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/0ea27175-19f8-4d15-b3f4-458dc6212046)

BotFather ens preguntarà el nom del bot i el nom d'usuari del bot.

El nom del bot pot ser qualsevol, però el nom d'usuari ha de ser un nom únic dins de Telegram.

El Bot que creem d'exemple es diu **smxBot** i té com a no d'usuari **iaballesterBot**.

El BotFather ens donarà un codi especial per comunicar-nos amb Telegram des del nostre Bot, aquest codi només l'hem de conèixer nosaltres.

## 2.- Editar el bot

Amb la comanda /mybots BotFather ens deixa escollir el nostre bot i ens mostra un menú amb opcions d'edició:

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/5aea6b77-cebc-4118-a421-626555d5604a)

- **API TOKEN** ens mostra el Token del bot.
- **Edit Bot** ens deixa editar el nom del bot, la descripció, imatge del bot, etc...
- **Bot settings** ens deixa escollir opcions de personalització dels permisos del bot.
- **Payments** serveix per connectar el nostre bot amb pasarel·les de pagament.
- **Transfer Ownership** dona el bot a un altre compte de telegram.
- **Delete Bot** esborra el bot i ja no es pot fer servir més.

**Editar la descripció del bot:**

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/54612292-01a8-4fe5-9dba-f167f60f3fad)

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/65e697e3-7e25-4f00-8a74-b60c92182490)

**Afegir imatge d'avatar al bot:**

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/a621cfd4-7437-4cc8-8dc9-e77da9ea2164)

Si anem al bot de Telegram, ja existeix i té la descripció i la imatge que hem escollit, però no fa res.

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/f1013836-6d18-44b4-b052-9f11b0ad13ae)

## Python

Per a que el bot faci qualsevol cosa necessitem un programa de python executant-se, per això crearem un servidor que tingui el programa en execució.

Farem servir la [API de Telegram](https://core.telegram.org/bots/api).

Per simplificar les tasques utilitzarem la implementació de l'usuari [eternnoir](https://github.com/eternnoir/pyTelegramBotAPI).

El primer que necessitem és crear un programa de python, al qual anomenarem smxBot.py

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/17608064-f461-45df-8c10-4a811a4c474e)

### Funció dau de 6 cares:

La primera funcionalitat que tindrà el nostre bot serà llençar un dau de 6 cares, això ho aconseguim creant el següent programa

```
import telebot
import random

# connecto amb Telegram amb el TOKEN que ens ha donat BotFather
bot = telebot.TeleBot("TOKEN")

#anem a fer que si l'usuari escriu d6 el programa retorni un
#número aleatori de l'1 al 6 (com si fos una tirada de dau)

@bot.message_handler(commands=['d6'])
def dau_6_cares(message):
    chat_id = message.chat.id
    random.seed()
    r = random.randint(1,6)
    bot.send_message(chat_id,r)

# Faig que el script s'executi de forma infinita
bot.infinity_polling()
```

Després anem al bot i escrivim l'ordre "/d6":

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/172a2833-f085-4c00-85a4-5313c693cccc)


### Funció echo

Aquesta funció respòn a l'usuari amb el mateix text que envia:

```
#Aquesta funció fa eco, és a dir respòn a l'usuari amb el mateix missatge
@bot.message_handler(func=lambda m: True)
def echo(message):
    bot.reply_to(message, message.text)
```

![image](https://github.com/XaSaFa/TelegramBot/assets/110727546/b3f2d24f-295f-4d04-a06b-db71113234ef)
