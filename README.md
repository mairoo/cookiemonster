# 목표

Django 애플리케이션의 기본 뼈대를 제공한다. Two Scoops of Django 책을 참고로 작성하였다.

# cookiemonster 템플릿 구조

# 프로젝트의 생성

# 명령어 정리

본 프로젝트의 구조를 위한 아래와 같이 정리할 수 있다.

```
pyvenv venv
source venv/bin/activate
pip install Django
mkdir run
sudo chown $(whoami):www-data run
mkdir repo
cd repo
django-admin.py startproject conf .
```
