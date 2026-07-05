# Домашнее задание к занятию "`Расширенные возможности SQL`" - `Габрусев Михаил`  // я так и не смог приложить нормально скриншоты, добавил их в общую ветку репозитория..



### Задание 1

```
SELECT 
    CONCAT(s.first_name, ' ', s.last_name) AS staff_name,
    c.city AS city,
    COUNT(cu.customer_id) AS customer_count
FROM staff s
JOIN store st ON s.store_id = st.store_id
JOIN address a ON st.address_id = a.address_id
JOIN city c ON a.city_id = c.city_id
JOIN customer cu ON cu.store_id = st.store_id
GROUP BY s.staff_id, s.first_name, s.last_name, c.city
HAVING COUNT(cu.customer_id) > 300;
```


---

### Задание 2

```
SELECT COUNT(*) AS films_count
FROM film
WHERE length > (SELECT AVG(length) FROM film);
```



---

### Задание 3


```
SELECT 
    DATE_FORMAT(p.payment_date, '%Y-%m') AS month,
    SUM(p.amount) AS total_amount
FROM payment p
GROUP BY DATE_FORMAT(p.payment_date, '%Y-%m')
ORDER BY total_amount DESC
LIMIT 1;
```


### Задание 4


```
SELECT 
    CONCAT(s.first_name, ' ', s.last_name) AS staff_name,
    COUNT(p.payment_id) AS sales_count,
    CASE 
        WHEN COUNT(p.payment_id) >= 8000 THEN 'Да'
        ELSE 'Нет'
    END AS Премия
FROM staff s
LEFT JOIN payment p ON s.staff_id = p.staff_id
GROUP BY s.staff_id, s.first_name, s.last_name;
```




### Задание 5

```
SELECT f.film_id, f.title
FROM film f
LEFT JOIN inventory i ON f.film_id = i.film_id
LEFT JOIN rental r ON i.inventory_id = r.inventory_id
WHERE r.rental_id IS NULL
GROUP BY f.film_id, f.title;
```
```
Результат задачи 5:
1	ACADEMY DINOSAUR
14	ALICE FANTASIA
33	APOLLO TEEN
36	ARGONAUTS TOWN
38	ARK RIDGEMONT
41	ARSENIC INDEPENDENCE
87	BOONDOCK BALLROOM
108	BUTCH PANTHER
128	CATCH AMISTAD
144	CHINATOWN GLADIATOR
148	CHOCOLATE DUCK
171	COMMANDMENTS EXPRESS
192	CROSSING DIVORCE
195	CROWDS TELEMARK
198	CRYSTAL BREAKING
217	DAZED PUNK
221	DELIVERANCE MULHOLLAND
318	FIREHOUSE VIETNAM
325	FLOATS GARDEN
332	FRANKENSTEIN STRANGER
359	GLADIATOR WESTWARD
386	GUMP DATE
404	HATE HANDICAP
419	HOCUS FRIDA
495	KENTUCKIAN GIANT
497	KILL BROTHERHOOD
607	MUPPET MILE
642	ORDER BETRAYED
669	PEARL DESTINY
671	PERDITION FARGO
701	PSYCHO SHRUNK
712	RAIDERS ANTITRUST
713	RAINBOW SHOCK
742	ROOF CHAMPION
801	SISTER FREDDY
802	SKY MIRACLE
860	SUICIDES SILENCE
874	TADPOLE PARK
909	TREASURE COMMAND
943	VILLAIN DESPERATE
950	VOLUME HOUSE
954	WAKE JAWS
955	WALLS ARTIST
```
