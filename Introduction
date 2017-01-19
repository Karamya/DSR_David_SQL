select count (*) from film;

-- List all film titles with their actor's names

select first_name, last_name, title 
from film_actor, film, actor 
where film_actor.film_id = film.film_id and actor.actor_id = film_actor.actor_id;

-- Titles of all films that are not in the inventory

select title 
from film left join inventory on film.film_id = inventory.film_id 
where inventory.film_id is null;

-- The titles of all films returned on 2005-05-27
select title 
from film, inventory, rental
where to_char(rental.return_date, 'YYYY-MM-DD') = '2005-05-27' and rental.inventory_id = inventory.inventory_id and inventory.film_id = film.film_id;

-- cast(rental.return_date as DATE)) = '2005-05-27'


-- Customers ranked by how much they have spent

select first_name, last_name, sum(amount)
from customer, payment
where payment.customer_id = customer.customer_id
group by payment.customer_id, customer.first_name, customer.last_name
order by sum(payment.amount) desc;


-- customers who have spent more than 200

select first_name, last_name, sum(amount)
from customer, payment
where payment.customer_id = customer.customer_id
group by customer.first_name, customer.last_name
having sum(payment.amount) > 200
order by sum(payment.amount) desc;

-- stores with more than 200 customers

select store_id, count(customer_id)
from customer
group by  store_id
having count(customer_id)>200;

-- The number of rentals from each category

select name, count(rental_id)
from category, film_category, inventory, rental
where rental.inventory_id = inventory.inventory_id
and inventory.film_id = film_category.film_id
and film_category.category_id = category.category_id
group by category.name
order by count(rental_id) desc;



select name, count(rental_id)
from category
	join film_category using (category_id)
    join inventory using (film_id)
    join rental using (inventory_id)
group by category.name
order by count(rental_id) desc;


























