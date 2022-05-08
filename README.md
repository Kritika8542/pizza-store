# pizza-store
springboot REST based pizza store application

# Changes made by 2021MT93200@wilp.bits-pilani.ac.in
View the available pizzas
Ability to order  Pizzas
Customize the Pizza

# add more details here
# Changes made by 2021MT93200@wilp.bits-pilani.ac.in
Making changes to the order
Cancel the order
Expected Delivery Time


# changes from @BITS-2021MT93275 
# Example commands to test with Curl
* List all restaurants: `curl -v -H "Content-Type: application/json" -X GET http://localhost:8080/rest/restaurants`
* Add a new restaurant:
  * `curl -v -H "Content-Type: application/json" -X POST -u "admin:admin" -d '{"name":"Amarillo","city":"Tampere","address":"Hatanpäänvaltatie 1","email":"pizza@amarillo.fi","phone":"0207 716 328","open_at":"11:00:00","close_at":"22:00:00"}' http://localhost:8080/rest/restaurant`
  * `curl -v -H "Content-Type: application/json" -X POST -u "admin:admin" -d '{"name":"Rax","city":"Tampere","address":"Hatanpäänvaltatie 1","email":"pizza@rax.fi","phone":"0207 716 328","open_at":"11:00:00","close_at":"22:00:00"}' http://localhost:8080/rest/restaurant` 
  * (without authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X POST -d '{"name":"Amarillo","city":"Tampere","address":"Hatanpäänvaltatie 1","email":"pizza@amarillo.fi","phone":"0207 716 328","open_at":"11:00:00","close_at":"22:00:00"}' http://localhost:8080/rest/restaurant` 

# changes from @BITS-2021MT93275 
* Get specific restaurant (by id with all pizza details listed i.e. list all pizzas with a specific restaurant): `curl -v -H "Content-Type:application/json" -X GET http://localhost:8080/rest/restaurant/full/1`

* Update restaurant details (identified by id): 
  * `curl -v -H "Content-Type: application/json" -X PUT -u "admin:admin" -d '{"name":"Updated","city":"Kuopio","address":"Hatanpäänvaltatie 1","email":"pizza_kuopio@amarillo.fi","phone":"0210 716 328","open_at":"12:00:00","close_at":"23:00:00"}' http://localhost:8080/rest/restaurant/1`
  * (with wrong authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X PUT -u "admin:admi" -d 
  * '{"name":"Updated","city":"Kuopio","address":"Hatanpäänvaltatie 1","email":"pizza_kuopio@amarillo.fi","phone":"0210 716 328","open_at":"12:00:00","close_at":"23:00:00"}' http://localhost:8080/rest/restaurant/1`

# changes from @BITS-2021MT93275 
* Delete specific restaurant (identified by id)
  * `curl -v -H "Content-Type: application/json" -X DELETE -u "admin:admin" http://localhost:8080/rest/restaurant/1`
  * (without authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X DELETE http://localhost:8080/rest/restaurant/2`

* List all pizzas of specific restaurant: `curl -v -H "Content-Type: application/json" -X GET http://localhost:8080/rest/pizzas?restaurant_id=1`
 Add new pizza to specific restaurant: 
  * `curl -v -H "Content-Type: application/json" -X POST -u "admin:admin" -d '{"name":"California", "size":"L", "key_ingredients":"fetajuusto", "price":10, "restaurant_id":2}' http://localhost:8080/rest/pizza`
  * (with wrong authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X POST -u "admi:admin" -d '{"name":"California II", "size":"L", "key_ingredients":"fetajuusto", "price":10, "restaurant_id":2}' http://localhost:8080/rest/pizza`
* Get specific pizza details: `curl -v -H "Content-Type: application/json" -X GET http://localhost:8080/rest/pizza/1`
* Update pizza details (by pizza id)
  * `curl -v -H "Content-Type: application/json" -X PUT -u "admin:admin" -d '{"name":"Updated", "size":"L", "key_ingredients":"fetajuusto", "price":10, "restaurant_id":2}' http://localhost:8080/rest/pizza/1`
  * (without authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X PUT -d '{"name":"Updated", "size":"L", "key_ingredients":"fetajuusto", "price":10, "restaurant_id":2}' http://localhost:8080/rest/pizza/1`
* Delete specific pizza 
  * `curl -v -H "Content-Type: application/json" -X DELETE -u "admin:admin" http://localhost:8080/rest/pizza/1`
  * (with wrong authentication, thus expected to fail) `curl -v -H "Content-Type: application/json" -X DELETE -u "d:d" http://localhost:8080/rest/restaurant/2`
* List all pizzas of Web store: `curl -v -H "Content-Type: application/json" -X GET http://localhost:8080/rest/pizzas`
* Basic search by pizza name (should return all pizzas whose name contains search term): `curl -v -H "Content-Type: application/json" -X GET http://localhost:8080/rest/pizzas?name=PIZZA`
