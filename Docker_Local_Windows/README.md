
# Loyiha yaratishni boshlang! 

# 1. Loyiha uchun muhit yarating:

```rb
python -m venv venv
venv\Scripts\activate
```



# 2. requirements.txt faylini yarating va loyihaga kerakli paketlarni qo'shing:

__Django==4.1.3__  yoki 
```rb 
pip install django
```



# 3. Django loyiha yarating :

```rb
django-admin startproject myproject . 
```



# 4. Dockerfile fayl yarating:
```rb
FROM python:3.9-slim-buster
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
WORKDIR /code
COPY requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /code/
```
- FROM - Bu, bazov Python3.9 imajidan foydalaniladi.
- ENV - Python koddan bajargan bajt yoki kodni keshlashni qanday amalga oshirishni aniqlash uchun.
- WORKDIR - Ushbu imajda ishlash uchun kerakli direktoriyani aniqlash uchun.
- COPY - Loyiha fayllarini Docker imajiga ko'chirish.
- RUN - Loyiha kuyubxonalari bilan o'zaro amalga oshiriladigan buyruqlarni bajarish uchun.



# 5. docker-compose.yml faylini yarating:
```rb
version: "3.9"
services:
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
```



# 6. Docker ni ishga tushiring:

```rb 
docker-compose build
docker-compose up
```

- Bu kodlarni bajarish orqali, "Dockerfile" nomli fayl yordamida Docker-da oddiy Django loyihangizni ishga tushirishingiz mumkin. "docker-compose.yml" nomli fayl esa Docker konteynerlarini qurish va ishga tushurish uchun kerakli konfiguratsiyalarni o'z ichiga oladi

# "http://localhost:8000" manziliga kirib, brauzeringizda loyihangizni sinab ko'ring.

- Loyihaga yangilanish kiritishimiz uchun avval loyihani CTRL+C yordamida tuxtating.
    - __python manage.py migrate__
    - __python manage.py createsuperuser__
    
    
- Loyihani qayta ishga tushiring 
    - __docker-compose up__
    
    
 <hr>
 Mehnatimiz sizga foyda berayotgan bolsa GITHUB profilimizga obuna bo'ling va telegram kanalimizda reaksiyalarni qoldiring 👍
# *E'tiboringiz uchun rahmat* Savollaringiz bo'lsa [Telegram](https://t.me/foydamizteg_sin)
