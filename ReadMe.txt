Tutorial: https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/

Rename .env-rename to .env and env.db-rename

http://localhost:1337/ --> "Not Found The requested resource was not found on this server." because no page exists


Docker-compose commands
    Dev:
    $ docker-compose up -d --build
    $ docker-compose exec web python manage.py migrate --noinput
    $ docker-compose exec db psql --username=pg-admin --dbname=project
    $ docker volume inspect django-on-docker-template_postgres_data
    $ docker-compose down -v

    $ docker build -f ./app/Dockerfile -t project2:latest ./app
    $ docker-compose exec web python manage.py migrate --noinput
    $ docker run -p 8001:8000 -e "SECRET_KEY=please_change_me" -e "DEBUG=1" project2 python /usr/src/app/manage.py runserver 0.0.0.0:8000

    $ docker-compose up -d --build
    $ docker-compose exec web python manage.py startapp upload

    Prod:
    $ docker-compose -f docker-compose.prod.yml down -v
    $ docker-compose -f docker-compose.prod.yml up -d --build
    $ docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput
    $ docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear




