# для сборки образа и запуска контейнера
docker-compose -f docker-compose.prod.yml up -d --build  
docker-compose -f docker-compose.prod.yml exec web python manage.py migrate --noinput  
docker-compose -f docker-compose.prod.yml exec web python manage.py collectstatic --no-input --clear  

 
# для создания суперпользователя
docker-compose -f docker-compose.prod.yml exec web python manage.py createsuperuser  


# для остановки контейнера
sudo docker-compose down  
