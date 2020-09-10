# Telegram bot for fun
 Простой бот в телеграмм созданный по образу и подобию @vsratoslavbot реализованный на Python 3.*<br>
 [Ссылка](https://github.com/ATWp/Telegram_fun_bot.git) на репозиторий с ботом, если вы вдруг нашли его не на GitHub<br>
 
## Бот умеет:
 1. Создавать случайную подпись на картинке полученной от пользователя шрифтом *Lobster*;
 2. Репостить картинку в канал, указанный в настройках, если пользователь этого захочет.

## Краткая архитектура бота
Все настройки хранятся в файле с переменными окружения .env. Проверьте, чтобы он был в наличии.<br>
Фразы, которые бот будет рисовать на картинке записаны в папку *data* файл *phrases.txt*.<br>
Main файл для запуска бота *app.py*<br>
Необходимые библиотеки и их версии для запуска, указаны в *requirements.txt*. <br>
Чтобы установить их, используйте терминал и команду<br>
```
pip install -r requirements.txt
```

## Инструкция по установке и запуску на Linux Server
1. Получите доступ к серверу на который вы хотите установить бота

2. Создайте папку
```
mkdir telegram_bot_for_fun
```

3. Переместитесь в нее
```
cd telegram_bot_for_fun
```

4. Получите права доступа **Root** к серверу 
```
sudo su
```

5. Выполните установку Docker, если у вас нет его на сервере
```
sh docker_install.sh
```

6. Скорее всего, вы были перемещены в начальный каталог сервера. Вернитесь в созданную в пункте
**2** папку
```
cd telegram_bot_for_fun
```
7. Скачайте репозиторий бота из GitHub с помощью команды
```
git clone https://github.com/ATWp/Telegram_fun_bot.git
```


8. Перед запуском бота убедитесь, что он еще не запущен!
```
docker ps -a 
```
	В колонке **STATUS**, все значения должны быть **Exited**!!!

9. Запустим бота
```
docker-compose up --build
```

10. Возможно бот не запустился из-за отсутствия файла .env
Для того, чтобы его создать, используйте команду:
```
nano .env
```
Скопируйте в файл настройки бота:
```
TOKEN = 
DATA_PHRASES_PATH = data/phrases.txt
FOLDER_PICTURES = pictures_user/
CHANNEL_PUBLIC = 
RESOURCE_FONT = resoures/Lobster.ttf
```
Заполните пустые поля значениями.<br>
**TOKEN** - это user token, ваш доступ к боту, которое вы получаете от @BotFather.<br>
**CHANNEL_PUBLIC_ID** - это название канала в телеграмме, куда бот будет отправлять трансформированные картинки.<br>

*Сохраните файл* - **Ctr+X**<br>
*Выберите* **Yes**<br>
*Нажмите* **Enter**<br>
*Попробуйте снова запустить бота*<br>
```
docker-compose up --build
```

11. *Все запустилось?* Поздравляю, **Вы Великолепны!!!** :)


## Как улучшить бота и его код?
1. Написать unit test
Основа уже есть в папке *unit_test* и модуле *unit_test_app.py*
2. Добавить фразы в базу данных
3. Добавить сохранение запросов пользователя в БД с именами загруженных картинок
4. Сохранять картинки в папку для каждого пользователя
5. Сделать модуль по парсингу фраз с сайтов
6. Расширить функционал
7. и т.д.