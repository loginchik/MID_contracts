# Сбор данных

Наборы данных - см. [data](data).

## Контракты государственных закупок МИД

Данные собраны с помощью API сайта [clearspending.ru](clearspending.ru). 

В select-запросе содержалось два аргумента: 
* фильтрация: ИНН заказчика = 7704206201, то есть ИНН главного подразделения МИД РФ;
* сортировка: по дате подписания, от новейших к старейшим. 

Сначала был произведён тестовый запрос, по данным из которого определены интересующие ключи и значения, затем с помощью цикла собраны данные обо всех контрактах, удовлетворяющих условиям фильтрации, за всё время. 

Подробное описание структуры json есть в блокноте [contracts_api](contracts_api.ipynb).

Для удобства дальнейшего анализа: 
- переименованы колонки в соответствии с ключами в json-response;
- дополнена колонка prodQuantity там, где достаточно данных;
- преобразованы типы данных в колонках с датами;
- данные о поставщиках разбиты на три колонки: название компании, инн компании, тип компании; 
- ссылки на контракты выделены в отдельный датасет. 

Произведённые манипуляции есть в блокноте [contracts_api](contracts_api.ipynb).

## ИНН компаний-резидентов Иннополиса

С сайта [sezinnopolis.ru](https://sezinnopolis.ru) путем скрейпинга были собраны все ссылки на страницы компаний-резидентов Иннополиса. Затем с каждой страницы компании взята ссылка на название компании и её официальный сайт. 

Затем для каждой компании вручную подобраны ИНН с помощью [egrul.nalog.ru](https://egrul.nalog.ru/index.html). Результаты собранных данных сохранены в датасет. 

Произведённые манипуляции есть в блокноте [innopolis_inn](innopolis_inn.ipynb).