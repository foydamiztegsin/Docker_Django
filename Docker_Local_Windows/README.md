
# Loyiha yaratishni boshlang! 

# 1. Loyiha uchun muhit yarating:

__python -m venv venv__
__venv\Scripts\activate__



# 2. requirements.txt faylini yarating va loyihaga kerakli paketlarni qo'shing:

__Django==4.1.3__  yoki __pip install django__



# 3. Django loyiha yarating :

__django-admin startproject myproject .__



# 4. Dockerfile fayl yarating:
'''rb
FROM python:3.9-slim-buster
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
WORKDIR /code
COPY requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /code/
'''
- FROM - Bu, bazov Python3.9 imajidan foydalaniladi.
- ENV - Python koddan bajargan bajt yoki kodni keshlashni qanday amalga oshirishni aniqlash uchun.
- WORKDIR - Ushbu imajda ishlash uchun kerakli direktoriyani aniqlash uchun.
- COPY - Loyiha fayllarini Docker imajiga ko'chirish.
- RUN - Loyiha kuyubxonalari bilan o'zaro amalga oshiriladigan buyruqlarni bajarish uchun.



# 5. docker-compose.yml faylini yarating:

version: "3.9"
services:
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"




# 6. Docker ni ishga tushiring:

__docker-compose build__
__docker-compose up__

- Bu kodlarni bajarish orqali, "Dockerfile" nomli fayl yordamida Docker-da oddiy Django loyihangizni ishga tushirishingiz mumkin. "docker-compose.yml" nomli fayl esa Docker konteynerlarini qurish va ishga tushurish uchun kerakli konfiguratsiyalarni o'z ichiga oladi

# "http://localhost:8000" manziliga kirib, brauzeringizda loyihangizni sinab ko'ring.

- Loyihaga yangilanish kiritishimiz uchun avval loyihani CTRL+C yordamida tuxtating.
    - __python manage.py migrate__
    - __python manage.py createsuperuser__
    
- Loyihani qayta ishga tushiring 
    - __docker-compose up__
