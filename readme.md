version: "3.9" # opsiyonel.

services:

    frontend:
        # container_name: frontend (default: keyName)
        image: docker-compose-frontend
        build: ./frontend
        ports:
            # dış/iç port numaraları
            - 5173:5173
            - 3000:5173
            - 80:5173
        restart: on-failure # hata anında tekrar çalıştır.
        depends_on:
            # önce aşağıdakileri çalıştır.
            - backend # aşağıda tanımlandı.

    backend:
        image: docker-compose-backend
        build: ./backend
        ports:
            - 8000:8000
        restart: on-failure

# --------------------------------
# $ docker compose up # compose çalıştır.
# $ docker compose up -d --build # compose daemon aç ve tekrar build et.
# $ docker compose down # compose kapat.
# $ docker compose down -v # compose tümünü kapat.

# MONGODB yi local veya cloud farketmeksizin web üzerinden kontrol etmek için kullanılır

# docker run -p 8081:8081 --rm -e ME_CONFIG_MONGODB_URL='mongodb://host.docker.internal:27017' mongo-express


