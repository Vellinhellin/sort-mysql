











# Лабораторная работа: Ускорение сортировки и группировки в MySQL (ORDER BY / GROUP BY)

## Цель работы
Понять, когда MySQL выполняет `Using filesort` и `Using temporary`, и научиться проектировать индексы так, чтобы сортировка и группировка выполнялись за счёт порядка хранения данных.

## Ход работы
1. Создана база `sort_practice` и таблица `orders` (500 строк).
2. Продемонстрировано, что `ORDER BY amount` без индекса даёт `Using filesort`.
3. Создан индекс `idx_amount`, `filesort` исчез.
4. Показано влияние направления сортировки на использование индекса.
5. Продемонстрировано, что `GROUP BY status` без индекса даёт `Using temporary; Using filesort`.
6. Создан индекс `idx_status` (Loose Index Scan) — временная таблица исчезла.
7. Создан покрывающий индекс `idx_status_amount_cover` — получен `Using index`.
8. Создан дамп базы (`sort_dump.sql`).
9. Выгружен лог действий (`my_actions.log`).

## Скриншоты

### Создание БД и данных

![alt text](image.png)

### ORDER BY без индекса

![alt text](image-1.png)

### ORDER BY с индексом

![alt text](image-2.png)

### Направление сортировки

![alt text](image-3.png)

### GROUP BY без индекса

![alt text](image-4.png)

### GROUP BY с индексом

![alt text](image-5.png)

### Tight Index Scan

![alt text](image-6.png)

### Покрывающий индекс

![alt text](image-7.png)

### Файл дампа

![alt text](image-8.png)

### Файл лога

![alt text](image-9.png)

## Результаты
В папке проекта находятся:
- `sort_dump.sql` — дамп базы данных `sort_practice`.
- `my_actions.log` — отфильтрованный лог действий пользователя.