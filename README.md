Russian! ("bad" English version later, after main part of development ends)

Простая идея проекта:
Обеспечить работу андроид смартфона как сканера штрихкода. Наподобии Honeywell 1202g.
Проект состоит из 2х частей:

Первая - Приложение на андроид (вот это)
Основная часть работает на основе технологии ZXing, распознавая штрихкод. 
Затем при помощи Retrofit передает штрихкод выбранному в настройках приложения сокету

Вторая - Серверная часть на Java, с последующей конвертацией в службу Windows
https://github.com/Sapiens-bru/WifiBarcodeServer
Состоит из стандартного com.sun.HttpServer и обращения к классу java.awt.Robot

Результатом работы 2х приложений является эмуляция поведения сканера штрихкодов.

*Смартфон получает изображение содержащее штрихкод на камеру 

*ZXing находит на этом изображении штрихкод и превращает его в строку символов

*Retrofit отправляет строку символов на выделенный адрес

*HttpServer получает запрос содержащий строку символов

*Внутренняя логика приложения-сервера переводит строку символов в коды понятные роботу

*Robot последовательно вбивает клавиатурные коды, эмулируя тем самым событие клавиатуры.

