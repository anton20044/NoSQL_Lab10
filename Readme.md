Лабораторная работа №10 по курсу NoSQL.

Задание:
	- Выбор туроператоров:
		Выберите 4-5 популярных туроператоров, таких как TUI, Tez Tour, Coral Travel, Pegas Touristik и Anex Tour.
	- Создание нод для туроператоров:
		Представьте каждого туроператора в виде ноды в Neo4j.
	- Выбор направлений:
		Выберите 10-15 направлений, в которые данные операторы предоставляют путевки. 		Каждое направление должно быть представлено в виде связки нод: 				страна - конкретное место.
	- Создание связей между странами и местами:
	- Создайте связи между нодами стран и конкретных мест.
	- Добавление городов с транспортной инфраструктурой:
	- Добавьте ноды для ближайших к туристическим локациям городов, в которых есть аэропорты или вокзалы.
	- Создание маршрутов между городами:
		Создайте связи между городами, охарактеризовав каждый маршрут видом транспорта (поезд, автобус и т.д.).
	- Запрос для поиска маршрутов по наземному транспорту:
		Напишите запрос, который выводил бы направления (со всеми промежуточными точками), доступные только наземным 		транспортом.
	- Составление плана запроса:
		Составьте план запроса из пункта 7, используя команду EXPLAIN.
	- Добавление индексов для оптимизации:
		Добавьте индексы для оптимизации запроса.
	- Проверка плана запроса:
		Проверьте план запроса еще раз, чтобы убедиться, что индексы позволили оптимизировать запрос, используя команду PROFILE.

Решение:
1) Создал туроператоров:
create (:Toperator {name: 'TUI'})
create (:Toperator {name: 'Tez Tour'})
create (:Toperator {name: 'Coral Travel'})
create (:Toperator {name: 'Pegas Touristik'})
create (:Toperator {name: 'Anex Tour'})

2) Создал страны:
create (:Country {name: 'ОАЭ'})
create (:Country {name: 'Великобритания'})
create (:Country {name: 'Мексика'})
create (:Country {name: 'Индонезия'})
create (:Country {name: 'Греция'})
create (:Country {name: 'Италия'})
create (:Country {name: 'Турция'})
create (:Country {name: 'Франция'})
create (:Country {name: 'Египет'})
create (:Country {name: 'Испания'})
create (:Country {name: 'Марокко'})
create (:Country {name: 'Канарские острова'})
create (:Country {name: 'Индия'})
create (:Country {name: 'Сингапур'})
create (:Country {name: 'Перу'})
create (:Country {name: 'Тайланд'})
create (:Country {name: 'Катар'})
create (:Country {name: 'Бразилия'})

3) Создал места:
create (:Place {name: 'Дубай'})
create (:Place {name: 'Лондон'})
create (:Place {name: 'Канкун'})
create (:Place {name: 'Бали'})
create (:Place {name: 'Крит'})
create (:Place {name: 'Рим'})
create (:Place {name: 'Кабо-Сан-Лукас'})
create (:Place {name: 'Стамбул'})
create (:Place {name: 'Париж'})
create (:Place {name: 'Хургада'})
create (:Place {name: 'Барселона'})
create (:Place {name: 'Марракеш'})
create (:Place {name: 'Тенерифе'})
create (:Place {name: 'Корсика'})
create (:Place {name: 'Нью-Дели'})
create (:Place {name: 'Сингапур'})
create (:Place {name: 'Эдинбург'})
create (:Place {name: 'Флоренция'})
create (:Place {name: 'Джайпур'})
create (:Place {name: 'Куско'})
create (:Place {name: 'Бангкок'})
create (:Place {name: 'Доха'})
create (:Place {name: 'Пхукет'})
create (:Place {name: 'Рио-де-Жанейро'})

4) Создал связи оператор-место
match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Дубай'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Лондон'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Париж'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Джайпур'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Пхукет'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Марракеш'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Барселона'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Хургада'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'TUI'})
match (subj:Place {name: 'Бали'})
create (main) -[:Путевка]-> (subj);


match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Дубай'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Париж'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Крит'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Рим'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Кабо-Сан-Лукас'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Эдинбург'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Барселона'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Хургада'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Бали'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Tez Tour'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Путевка]-> (subj);


match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Бали'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Эдинбург'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Рим'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Крит'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Стамбул'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Париж'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Нью-Дели'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Coral Travel'})
match (subj:Place {name: 'Корсика'})
create (main) -[:Путевка]-> (subj);



match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Дубай'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Корсика'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Рио-де-Жанейро'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Куско'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Доха'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Крит'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Рим'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Pegas Touristik'})
match (subj:Place {name: 'Стамбул'})
create (main) -[:Путевка]-> (subj);



match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Дубай'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Доха'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Корсика'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Рим'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Бали'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Канкун'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Бангкок'})
create (main) -[:Путевка]-> (subj);

match (main:Toperator {name: 'Anex Tour'})
match (subj:Place {name: 'Нью-Дели'})
create (main) -[:Путевка]-> (subj);


5) Создал связи страна-место:
match (main:Country {name: 'ОАЭ'})
match (subj:Place {name: 'Дубай'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Великобритания'})
match (subj:Place {name: 'Лондон'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Великобритания'})
match (subj:Place {name: 'Эдинбург'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Мексика'})
match (subj:Place {name: 'Канкун'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Индонезия'})
match (subj:Place {name: 'Бали'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Греция'})
match (subj:Place {name: 'Крит'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Италия'})
match (subj:Place {name: 'Рим'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Турция'})
match (subj:Place {name: 'Стамбул'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Мексика'})
match (subj:Place {name: 'Кабо-Сан-Лукас'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Франция'})
match (subj:Place {name: 'Париж'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Египет'})
match (subj:Place {name: 'Хургада'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Испания'})
match (subj:Place {name: 'Барселона'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Марокко'})
match (subj:Place {name: 'Марракеш'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Франция'})
match (subj:Place {name: 'Корсика'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Канарские острова'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Сингапур'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Индия'})
match (subj:Place {name: 'Нью-Дели'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Индия'})
match (subj:Place {name: 'Джайпур'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Италия'})
match (subj:Place {name: 'Флоренция'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Перу'})
match (subj:Place {name: 'Куско'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Тайланд'})
match (subj:Place {name: 'Бангкок'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Катар'})
match (subj:Place {name: 'Доха'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Тайланд'})
match (subj:Place {name: 'Пхукет'})
create (main) -[:Туристическое_место]-> (subj);

match (main:Country {name: 'Бразилия'})
match (subj:Place {name: 'Рио-де-Жанейро'})
create (main) -[:Туристическое_место]-> (subj);


5) Добавляем ближайшие города с аэропортами и вокзалами. Устанавливаем связь с туристическим местом

create (:City {name: 'Сингапур'});
match (main:City {name: 'Сингапур'})
match (subj:Place {name: 'Сингапур'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Джайпур'});
match (main:City {name: 'Джайпур'})
match (subj:Place {name: 'Джайпур'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Флоренция'});
match (main:City {name: 'Флоренция'})
match (subj:Place {name: 'Флоренция'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Корсика'});
match (main:City {name: 'Корсика'})
match (subj:Place {name: 'Корсика'})
create (main) -[:Поезд]-> (subj);

create (:City {name: 'Барселона'});
match (main:City {name: 'Барселона'})
match (subj:Place {name: 'Барселона'})
create (main) -[:Поезд]-> (subj);

create (:City {name: 'Рио-де-Жанейро'});
match (main:City {name: 'Рио-де-Жанейро'})
match (subj:Place {name: 'Рио-де-Жанейро'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Доха'});
match (main:City {name: 'Доха'})
match (subj:Place {name: 'Доха'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Куско'});
match (main:City {name: 'Куско'})
match (subj:Place {name: 'Куско'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Хургада'});
match (main:City {name: 'Хургада'})
match (subj:Place {name: 'Хургада'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Кабо-Сан-Лукас'});
match (main:City {name: 'Кабо-Сан-Лукас'})
match (subj:Place {name: 'Кабо-Сан-Лукас'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Стамбул'});
match (main:City {name: 'Стамбул'})
match (subj:Place {name: 'Стамбул'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Крит'});
match (main:City {name: 'Крит'})
match (subj:Place {name: 'Крит'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Бали'});
match (main:City {name: 'Бали'})
match (subj:Place {name: 'Бали'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Париж'});
match (main:City {name: 'Париж'})
match (subj:Place {name: 'Париж'})
create (main) -[:Поезд]-> (subj);

create (:City {name: 'Париж'});
match (main:City {name: 'Париж'})
match (subj:Place {name: 'Париж'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Тенерифе'});
match (main:City {name: 'Тенерифе'})
match (subj:Place {name: 'Тенерифе'})
create (main) -[:Самолет]-> (subj);

create (:City {name: 'Барселона'});
match (main:City {name: 'Барселона'})
match (subj:Place {name: 'Барселона'})
create (main) -[:Самолет]-> (subj);


6) Выбираем маршруты где есть поезд
match (p1:Toperator) -[]- (p3:Place)  -[r:Поезд]- (p2:City) return p1, p3,  p2

7) Проведя анализ плана запроса, решил построить индекс 

create index on for (n:Place) on (n.name)

8) Повторил запрос. За счет индекса уменьшилось количество поднимаемых записей. Как и в большинстве СУБД индекс привел к уменьшению количества читаемых данных и как следствие более быстрому выполнению запроса.











