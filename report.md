# Отчет по проекту
###### Позволю себе писать на русском.
## О проекте
Language: Python

Libs: torch, torchvision, telebot, flask, vedis

Deployed on: Heroku

Этот бот - это итоговый проект для осеннего семестра 2021 года в Deep Learning School.
## Обо мне
Меня зовут: Георгий Якушев

Telegram: @MrDarkTesla

E-mail: yakushev.ga@phystech.edu
## Аннотация
Написанный мной бот переносит стиль с одной картинки на другую.
Использованы предобеденные слои VGG19 для извлечения "признаков стиля".
Бот запущен через heroku. Выходное изображение имеет формат 256x256, что связано с некоторыми техническими ограничениями.
## Подробное описание модели
У VGG19 используются слои: 0, 5, 10, 19, 28.

В качестве функции потерь выступают функции оценивающие
"близость" с содержанием и со стилем:
Среднеквадратичное отклонение для содержания и матрица грамма
для каждого использованного слоя стиля. Эти функции связаны некоторым коэффициентом. (style / content = 100)

Обучаю 50 эпох Адамом.
###### Эта часть проекта была реализована первой и заняла меньше всего времени, поскольку алгоритм не сложный 
## Реализация функционала бота
Простейшие функции были реализованы с помощью библиотеки telebot.
###### Это было мое первое знакомство с телеграм ботами, но я быстро с этим разобрался
Далее для хранения данных о состоянии пользователя была выбрана библиотека vedis (NoSQL).
###### Я касался SQL всего пару раз так что не был уверен что быстро разберусь в том, что там и как происходит. Этот вопрос остается открытым, и я надеюсь в ближайшем будущем с ним разобраться.
Позже были добавлены красивые реплики, оформлены команды и т.д. В общем бот стал красивым.

## Сказ о деплое на heroku
###### Как можно догадаться я по заголовку эта часть отняла у меня больше всего времени, сил и нервов.
Я очень долго тупил и пытался понять как это работает, какая там файловая система и почему я не могу сохранять файлы так,
как я это делаю локально. Также непреодолимой оказалась задача запихнуть в 500мб все что нужно. 
Как написано в README.md, бот иногда может падать из-за того что он всегда использует примерно 700-800мб из положенных 500.
Сначала я пытался пофиксить эту проблему, но заметил что бот и так работает, так что я решил не трогать.
Единственное, что меня смущает - это вечные сообщения о превышении выделенной памяти в логах heroku и периодические краши.

Сказки всегда заканчиваются хорошо, так и здесь. Вроде все работает...

Я не проверял многопоточность, это, я подозреваю, требуют примерно таких же усилий, но главное - памяти, которой, итак, мало.
К тому же заканчивается время.
## Итог
Строго говоря это мой первый большой самостоятельный **завершенный** (до состояния, когда этим может пользоваться кто-то кроме меня) проект.
Так что я планирую его довести до ума так или иначе. Любая критика приветствуется на ровне с пожеланиями и предложениями. Но и без этого бот вроде кое-как функционирует. 