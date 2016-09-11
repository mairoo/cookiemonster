# 목표

Django 애플리케이션의 기본 뼈대를 제공한다. Two Scoops of Django 책을 참고로 작성하였다.

cookiecutter를 올바로 활용하려면 다소 많은 배경지식을 필요로 해서 간단한 템플릿을 만들고자 한다.

# cookiemonster 템플릿 구조

Two Scoops of Django 책은 3단계 구조를 제안한다.

```
<저장소_루트>
    <프로젝트_루트>
        <설정_루트>
```

그러나 굳이 저장소 루트와 프로젝트 루트 단계를 나눌 필요는 없을 것 같아 2단계 구조로 정의하고자 한다. 다만 다른 프로젝트와 구별할 수 있도록 프로젝트 이름의 최상위 디렉토리를 아래와 같이 두고자 한다.

```
<프로젝트_이름>/
    repo/
        config/
            settings/
                base.py
                local.py
                production.py
        manage.py
    venv/
    run/
        wsgi.sock
        gunicorn.sock
```

```프로젝트_이름```의 하위 디렉토리 3개의 의미는 다음과 같다.

* ```repo```: 저장소 루트 디렉토리이면서 동시에 프로젝트 루트가 된다.
* ```venv```: 종속성 분리를 제공하기 위한 독립된 가상환경 virtualenv 디렉토리이다.
* ```run```: WSGI 서버 배포시 소켓이 저장되는 디렉토리이다. ```manage.py runserver```로 서버를 구동한다면 불필요하다.

```repo``` 디렉토리 안에 ```config``` 디렉토리는 프로젝트 설정 파일이 존재한다. ```django_admin.py startapp``` 명령어로 프로젝트를 생성할 때 만들어지는 디렉토리이다.
 일반적으로 프로젝트 이름으로 만들지만 이미 최상위 디렉토리 이름을 다른 프로젝트와 구별할 수 있도록 프로젝트 이름으로 지었기 때문에 프로젝트 설정 디렉토리 이름은 ```config``` 이름으로 약속한다.

```repo```, ```venv```, ```run``` 디렉토리 모두 이름을 약속해서 다른 Django 프로젝트를 개발하더라도 쉽게 구조를 파악할 수 있도록 같은 이름으로 일관성을 유지한다.

# 프로젝트의 설정
  

# 프로젝트의 생성

```
django-admin.py startproject --template https://github.com/mairoo/cookiemonster/archive/master.zip repo
```

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
