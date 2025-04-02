# Product Service (Port 8081)

# Get all products
curl http://localhost:8081/products

# Get product by ID
curl http://localhost:8081/products/1

# Create product
curl -X POST -H "Content-Type: application/json" -d '{
  "name": "Example Product",
  "description": "This is an example product.",
  "price": 29.99
}' http://localhost:8081/products

# Update product
curl -X PUT -H "Content-Type: application/json" -d '{
  "name": "Updated Product",
  "description": "This is an updated product.",
  "price": 39.99
}' http://localhost:8081/products/1

# Delete product
curl -X DELETE http://localhost:8081/products/1

# Search products
curl http://localhost:8081/products/search?query=Example

# User Service (Port 8082)

# Get all users
curl http://localhost:8082/users

# Get user by ID
curl http://localhost:8082/users/1

# Create user (register)
curl -X POST -H "Content-Type: application/json" -d '{
  "username": "exampleuser",
  "password": "password123"
}' http://localhost:8082/users/register

# Update user
curl -X PUT -H "Content-Type: application/json" -d '{
  "username": "updateduser",
  "password": "newpassword"
}' http://localhost:8082/users/1

# Delete user
curl -X DELETE http://localhost:8082/users/1

# Authenticate user (get JWT)
curl -X POST -H "Content-Type: application/json" -d '{
  "username": "exampleuser",
  "password": "password123"
}' http://localhost:8082/users/authenticate

# Cart Service (Port 8083)

# Get cart for user
curl http://localhost:8083/carts/1

# Add item to cart
curl -X POST -H "Content-Type: application/json" -d '{
  "productId": 1,
  "quantity": 2
}' http://localhost:8083/carts/1/items

# Remove item from cart
curl -X DELETE http://localhost:8083/carts/1/items/1

# Update item quantity
curl -X PUT http://localhost:8083/carts/1/items/1?quantity=3

# Clear cart
curl -X DELETE http://localhost:8083/carts/1/clear

# Order Service (Port 8084)

# Create order
curl -X POST -H "Content-Type: application/json" -d '[1, 2, 3]' http://localhost:8084/orders/1

# Get order by ID
curl http://localhost:8084/orders/1

# Get orders by user
curl http://localhost:8084/orders/user/1

# Update order status
curl -X PUT http://localhost:8084/orders/1/status/SHIPPED

# Inventory Service (Port 8085)

# Get product stock
curl http://localhost:8085/inventory/1

# Create product stock
curl -X POST -H "Content-Type: application/json" -d '{
  "productId": 1,
  "stock": 100
}' http://localhost:8085/inventory

# Update product stock
curl -X PUT -H "Content-Type: application/json" -d '{
  "productId": 1,
  "stock": 150
}' http://localhost:8085/inventory/1

# Decrease product stock
curl -X PUT http://localhost:8085/inventory/1/decrease/10
