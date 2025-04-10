# Домашнее задание к занятию "Индексы" - Петр Фумелли

### Задание 1

![alt text](https://github.com/PeterFumelli/SQL.1/blob/main/img/1.png)

### Задание 2

```sql
EXPLAIN ANALYZE
SELECT DISTINCT
  CONCAT(c.last_name, ' ', c.first_name) AS customer_name,
  SUM(p.amount) OVER (PARTITION BY c.customer_id, f.title) AS total_payment
FROM payment p
JOIN rental r ON p.payment_date = r.rental_date
JOIN customer c ON r.customer_id = c.customer_id
JOIN inventory i ON i.inventory_id = r.inventory_id
JOIN film f ON f.film_id = i.film_id
WHERE p.payment_date >= '2005-07-30' AND p.payment_date < '2005-07-31';

```