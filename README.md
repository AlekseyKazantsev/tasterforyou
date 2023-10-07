Привет🙌, меня зовут Алексей.

Я начинающий QA-инженер с горящими глазами. Ищу удаленную работу!

Обо мне:

Я прохожу обучуние и осваиваю профессию инженера по тестированию на платформе SkyPro. Особый интерес проявляю к тестированию API и работе с SQL. Я активно посещаю онлайн-курсы, читаю профессиональные книги и форумы, где могу учиться у опытных профессионалов, постоянно общаюсь и коллегами по курсу, а так же с кураторами. Также ищу разные возможности и участвую в профессиональных конференциях и встречах, чтобы делиться знаниями. Всё это помогает мне развиваться в области тестирования и достигать высоких результатов в обучении и освоении новой профессии.

Связаться со мной:
https://t.me/alekseykazantsev

Инструменты:

:white_check_mark: функциональное тестирование;

:white_check_mark: тестирование API;

:white_check_mark: SQL.

____

Проект тестирования функциональной возможность добавления, редактирования и удаления личного события в личном кабинете учителя Skyeng.

Раздел 1. Функциональное тестирование
На тестирование нового элемента - “Личные события” потрачено 85 минут. 
Применены следующие виды тестироватия:

- Smoke тест
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/1.jpeg)




- Функциональное тестирование
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/2.jpeg)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/3.jpeg)






- Приемочное тестирование
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/4.jpeg)




- Регрессионное тестрирование (старый функционал)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/5.jpeg)




По результатам тестирования найдено 4 бага, все баги с низким приоритетом (P3) - Low, серьезность S4 - незначительная. 
Все баги заведены в баг-трекинговую систему Jira. Три бага связаны с визуальным отражением в календаре уроков и личных событий в момент, 
когда они совпадают по времени, согласно требованию урок всегда должен отображаться выше личных событий. Один баг связан с полем “Описание“,
согласно документации проекта поле не имеет ограничение по количеству символов, в проекте реализовано ограничение в 500 символов.
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/6.jpeg)






Работа по тестированию проводилась ПК VivobookAsus_Laptop X1502ZA, ОС Windows 11 Домашняя для одного языка Версия 22H2, 
Браузер Microsoft Edge Версия 111.0.1661.62 (Официальная сборка) (64-разрядная версия).



Раздел 2. Тестирование API
При тестировании функционала “Личные события” через API проведены следующие мероприятия:
- Созданы функциональные тест-кейсы, на основе которых определены методы для тестирования API
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/7.jpeg)


- Создана Postman-коллекция (ссылка) и проведен тест-ран. При запуске колеекции ошибок не выявлено;
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/8.jpeg)


- Дополнительно написан тест-кейс “Повторное удаление личного события“, данный тест-кейс нельзя проверить через UI через один клиент (браузер). Также API позволяет при редактировании личного события устанавливать любую дату нового события как в прошлом так и в будущем, в отличие от UI (диапазон дат, редактируемого личного события, равен понедельнику недели в котором находится редактируемое личное событие плюс 3 месяца)
- Выявлен баг отображения времени урока, созданного через API на UI. При последовательном прогоне запросов в Postman (создание, редактирование) часовой пояс указанный в теле запроса на 1 час больше чем часовой пояс который фиксируется в UI. Связано с тем, что тестовая версия личного кабинета не учитывает часовой пояс пользователя, по умолчанию стоит часовой пояс МСК +3, а в Postman используются данные из инструментов разработчика пользователя (часовой пояс пользователя).
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/9.jpeg)
![Screenshot](https://github.com/AlekseyKazantsev/testerforyou/blob/main/10.jpeg)






Заключение. 

Раздел 1. Найденые баги являются низкими по приоритету, так как не влияют на новую функциональность, и можно исправить в последнюю очередь. Основные операции с “Личными событиями“: добавление, удаление, редактирование, совмещение личного события и урока работают согласно документации к проекту. Так же было проведено регресс-тестирование старого функционала перенос и отмена “Урока”, данные функции работают без замечаний.

Раздел 2. Благодаря тестированию API появилась возможность протестировать более широкий диапазон переноса дат события, особенно это касаестся даты в прошлом. Так же мы убедились в том, что при первом удалении личного события оно гарантировано удаляется из системы, что подтверждает запрос на повторное удаление личного события. Выявили баг несоответствия часового пояса польвателя с данными в личном кабинете.

Вывод: 
- новый функционал (личные события) системы готов к выпуску;
- остальной функционал (уроки - перенос, отмена) системы работает в прежнем режиме;
- проведенное тестирование API, подтверждает ранее сделанные выводы о работе функционала “Личные собития“, функционал работает согласно документации к проекту;
- необходимо к следующему релизу рассмотреть возможность изменения технологии корректировки даты в UI (выбор не из выпадающего списка, а через календарь);
- автоматический учет часового пояса пользователя на основании данных из ОС

____

Проект SQL

Проект: база данных.

Описание: используя готовую базу данных, были написаны запросы различной сложности для вывода информации по заданным критериям. В дополнение к готовой базе данных были созданы таблицы с данными для последующей работы с ними.

Цель: научиться работать с БД и писать запросы на получение информации по заданным условиям.

Инструменты:

:white_check_mark: DBeaver


1. Составьте запрос, который выведет имя вида с наименьшим id. 

select type_id, species_name

rom species

order by type_id asc

limit 1

2. Составьте запрос, который выведет имя вида с количеством представителей более 1800. 
select species_name
from species
where species_amount > 1800

3. Составьте запрос, который выведет имя вида, начинающегося на «п» и относящегося к типу с type_id = 5. 
select species_name
from species
where species_name like 'п%' and type_id = 5

4. Составьте запрос, который выведет имя вида, заканчивающегося на «са» или количество представителей которого равно 5. 
select species_name, species_amount
from species
where species_name like '%са' or species_amount = 5

5. Составьте запрос, который выведет имя вида, появившегося на учете в 2023 году. 
select species_name
from species
where extract (year from date_start) = 2023

6. Составьте запрос, который выведет названия отсутствующего (status = absent) вида, расположенного вместе с place_id = 3. 
select species.species_name, places.place_id
from species
join species_in_places on species.species_id = species_in_places.species_id
join places on species_in_places.place_id = places.place_id
where species.species_status = 'absent' and places.place_id = 3

7. Составьте запрос, который выведет название вида, расположенного в доме и появившегося в мае, а также и количество представителей вида. 
select species.species_name, places.place_name, species.species_amount
from species
join species_in_places on species.species_id = species_in_places.species_id
join places on species_in_places.place_id = places.place_id
where place_name = 'дом' and extract(month from species.date_start) = 5

8. Составьте запрос, который выведет название вида, состоящего из двух слов (содержит пробел). 
select species_name
from species
where species_name like '% %'

9. Составьте запрос, который выведет имя вида, появившегося с малышом в один день. 
select species_name, date_start
from species
where date_start in(
	select date_start
	from species
	where species_name = 'малыш')

10. Составьте запрос, который выведет название вида, расположенного в здании с наибольшей площадью. 
select species.species_name, places.place_name, place_size
from species
join species_in_places on species.species_id = species_in_places.species_id
join places on species_in_places.place_id = places.place_id
where place_name in ('сарай', 'дом')
order by place_size desc
limit 1

11. Составьте запрос/запросы, которые найдут название вида, относящегося к 5-й по численности группе проживающей дома. 
select species.species_name, places.place_name, species.species_amount
from species
join species_in_places on species.species_id = species_in_places.species_id
join places on species_in_places.place_id = places.place_id
where places.place_name = 'дом'
group by species.species_name, places.place_name, species.species_amount
order by species.species_amount desc
limit 1 offset 4

12. Составьте запрос, который выведет сказочный вид (статус fairy), нерасположенный ни в одном месте.
select species_name, species_status
from species
where species_status = 'fairy' and species_id not in (
select distinct species_id
from species_in_places
)








