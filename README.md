# Домашнее задание к занятию "`«SQL.Часть 2»`" - `Бызгаев Александр`

---

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### Решение:

```
SELECT CONCAT(staff.first_name, ' ', staff.last_name) AS employee_name, city.city AS store_city,
COUNT(customer.customer_id) AS customer_count FROM store JOIN staff ON store.manager_staff_id = staff.staff_id JOIN address ON store.address_id = address.address_id
JOIN city ON address.city_id = city.city_id JOIN customer ON store.store_id = customer.store_id GROUP BY store.store_id HAVING customer_count > 300;
```

![image](https://github.com/Byzgaev-I/SQL.Part-2/blob/main/2-1.png)

---

### Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

### Решение:

```
SELECT COUNT(*) AS film_count FROM film WHERE length > (SELECT AVG(length) FROM film);
```

![image](https://github.com/Byzgaev-I/SQL.Part-2/blob/main/2-2.png)


---

### Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей, и добавьте информацию по количеству аренд за этот месяц.

### Решение:

```
SELECT DATE_FORMAT(payment_date, '%Y-%m') AS payment_month, COUNT(rental_id) AS rental_count, SUM(amount) AS total_amount FROM payment GROUP BY payment_month ORDER BY total_amount DESC LIMIT 1;
```

![image](https://github.com/Byzgaev-I/SQL.Part-2/blob/main/2-3.png)
