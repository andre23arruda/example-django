# Comecando um projeto

Crie uma pasta para manter seu código e acessando essa pasta em um terminal, crie um ambiente virtual com o seguinte comando:

```python
python3 -m venv ./venv
```

Ative seu ambiente virtual com o seguinte comando em Windows:

```python
source venv/bin/activate
```

Instale o Django nesse ambiente virtualizado:

```python
pip install django
```

Crie um projeto chamado setup utilizando o Django admin, para manter toda configuração de nossa aplicação:

```python
django-admin startproject setup .
```

Na pasta setup, altere no arquivo [settings.py](http://settings.py/) o idioma e o horário que usaremos na aplicação, incluindo as seguintes linhas de código:

```python
LANGUAGE_CODE = 'pt-br'
TIME_ZONE = 'America/Sao_Paulo'
```

Para finalizar a configuração do ambiente, vamos configurar um diretório para manter os arquivos HTML incluindo a seguinte linha de código em TEMPLATES(não esqueça de criar a pasta template):

```python
'DIRS': [os.path.join(BASE_DIR, 'templates')],
```

Rodar o servidor:

```python
python manage.py runserver
```

Vai aparecer a tela com o foguetinho no navegador

Criar um App:

```python
python manage.py startapp nome_app
```

A pasta nome_app vai ser criada no ambiente

Registrar o App no projeto em settings.py:

```python
INSTALLED_APPS = [
    'nome_app',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

Criar a url para o App em [urls.py](http://urls.py) do projeto:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('nome_app.urls'))
]
```

Criar [urls.py](http://urls.py) dentro da pasta do App e colocar:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name = 'index')
]
```

Agora, em [views.py](http://views.py) dentro da pasta do App colocar:

```python
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```

E agora, dentro de templates, criar um arquivo index.html:

```html
<h1>Ola, mundo</h1>
```

## Pronto para comecar :)