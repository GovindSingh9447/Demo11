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
