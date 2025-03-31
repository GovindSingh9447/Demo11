http {
    upstream product_service {
        server localhost:8081;
    }

    upstream user_service {
        server localhost:8082;
    }

    upstream cart_service {
        server localhost:8083;
    }

    upstream order_service {
        server localhost:8084;
    }

    upstream inventory_service {
        server localhost:8085;
    }

    upstream chat_service {
      server localhost:8086;
    }

    server {
        listen 80;

        location /products/ {
            proxy_pass http://product_service/;
        }

        location /users/ {
            proxy_pass http://user_service/;
        }

        location /carts/ {
            proxy_pass http://cart_service/;
        }

        location /orders/ {
            proxy_pass http://order_service/;
        }

        location /inventory/ {
            proxy_pass http://inventory_service/;
        }

        location /chat/ {
          proxy_pass http://chat_service/;
        }

    }
}




































CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    image_url VARCHAR(255),
    category VARCHAR(100),
    stock INT
);









CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100)
);



CREATE TABLE cart_items (
    cart_item_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    product_id INT REFERENCES products(product_id),
    quantity INT NOT NULL
);


CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50)
);

CREATE TABLE order_items (
    order_item_id SERIAL PRIMARY KEY,
    order_id INT REFERENCES orders(order_id),
    product_id INT REFERENCES products(product_id),
    quantity INT NOT NULL,
    price DECIMAL(10,2)
);


CREATE TABLE inventory (
  product_id INT PRIMARY KEY REFERENCES products(product_id),
  stock_quantity INT NOT NULL
);





