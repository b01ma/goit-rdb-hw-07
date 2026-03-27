# goit-rdb-hw-07

Woolf University · Neoversity GoIT  
Relational Database · Homework #7

## Опис домашнього завдання

Для таблиці `orders` потрібно виконати 5 SQL-запитів на роботу з датою/часом та JSON.

> У запитах нижче використано MySQL-функції. Атрибут `date` взято в бектики як `` `date` ``, оскільки це службове слово.

---

## Завдання 1

**Умова:**
Для таблиці `orders` з атрибута `date` витягнути рік, місяць і день. Вивести 5 атрибутів: `id`, оригінальний `date`, рік, місяць, день.

**SQL-запит:**

```sql
SELECT
	id,
	`date`,
	YEAR(`date`)  AS order_year,
	MONTH(`date`) AS order_month,
	DAY(`date`)   AS order_day
FROM orders;
```

---

## Завдання 2

**Умова:**
Для таблиці `orders` додати 1 день до атрибута `date`. Вивести `id`, оригінальний `date` і результат додавання.

**SQL-запит:**

```sql
SELECT
	id,
	`date`,
	DATE_ADD(`date`, INTERVAL 1 DAY) AS date_plus_one_day
FROM orders;
```

---

## Завдання 3

**Умова:**
Для таблиці `orders` відобразити кількість секунд з початку відліку (Unix timestamp) для атрибута `date`. Вивести `id`, оригінальний `date` і результат функції.

**SQL-запит:**

```sql
SELECT
	id,
	`date`,
	UNIX_TIMESTAMP(`date`) AS seconds_since_epoch
FROM orders;
```

---

## Завдання 4

**Умова:**
Порахувати, скільки рядків у таблиці `orders` мають `date` у межах між `1996-07-10 00:00:00` та `1996-10-08 00:00:00`.

**SQL-запит:**

```sql
SELECT
	COUNT(*) AS total_rows
FROM orders
WHERE `date` BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```

---

## Завдання 5

**Умова:**
Для таблиці `orders` вивести `id`, `date` та JSON-об’єкт формату:

```json
{"id": <id>, "date": <date>}
```

**SQL-запит:**

```sql
SELECT
	id,
	`date`,
	JSON_OBJECT('id', id, 'date', `date`) AS order_json
FROM orders;
```

---

## Підсумок

У межах ДЗ використано такі функції MySQL:

- `YEAR()`, `MONTH()`, `DAY()` — виділення частин дати;
- `DATE_ADD(..., INTERVAL 1 DAY)` — додавання інтервалу часу;
- `UNIX_TIMESTAMP()` — перетворення дати у Unix timestamp;
- `BETWEEN` — фільтрація по діапазону дат;
- `JSON_OBJECT()` — формування JSON-об’єкта з полів рядка.
