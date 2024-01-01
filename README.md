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

