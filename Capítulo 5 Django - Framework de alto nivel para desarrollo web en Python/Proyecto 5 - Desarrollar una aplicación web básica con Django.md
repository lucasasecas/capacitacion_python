# Desarrollar una aplicación web básica con Django

En este proyecto, vamos a desarrollar una aplicación de lista de tareas pendientes (To-Do List) utilizando Django. La aplicación permitirá a los usuarios crear, leer, actualizar y eliminar tareas. Al igual que con el proyecto Flask, la aplicación se actualizará en cada capítulo para incorporar los conceptos aprendidos.

A continuación, se presenta la estructura de archivos y directorios:

```
todolist_django/
├── manage.py
├── requirements.txt
├── todolist/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── static/
└── tasks/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── migrations/
    │   └── __init__.py
    ├── models.py
    ├── templates/
    │   ├── tasks/
    │   │   ├── base.html
    │   │   ├── index.html
    │   │   ├── detail.html
    │   │   ├── create.html
    │   │   └── update.html
    ├── tests.py
    ├── urls.py
    └── views.py
```

1. Crear un nuevo proyecto Django y una aplicación llamada `tasks`:
   ```
   django-admin startproject todolist_django
   cd todolist_django
   python manage.py startapp tasks
   ```

2. Instalar Django y agregarlo a `requirements.txt`:
   ```
   pip install django
   echo "django" > requirements.txt
   ```

3. Crear el modelo `Task` en `tasks/models.py`:
   ```python
   from django.db import models

   class Task(models.Model):
       title = models.CharField(max_length=200)
       description = models.TextField()
       completed = models.BooleanField(default=False)
       created_at = models.DateTimeField(auto_now_add=True)
       updated_at = models.DateTimeField(auto_now=True)

       def __str__(self):
           return self.title
   ```

4. Crear las vistas para manejar las tareas en `tasks/views.py`:
   ```python
   from django.shortcuts import render, get_object_or_404, redirect
   from .models import Task

   def task_list(request):
       tasks = Task.objects.all()
       return render(request, 'tasks/index.html', {'tasks': tasks})

   def task_detail(request, task_id):
       task = get_object_or_404(Task, id=task_id)
       return render(request, 'tasks/detail.html', {'task': task})

   def task_create(request):
       # Lógica para crear una nueva tarea aquí

   def task_update(request, task_id):
       # Lógica para actualizar una tarea existente aquí

   def task_delete(request, task_id):
       # Lógica para eliminar una tarea aquí
   ```

5. Crear las plantillas en `tasks/templates/tasks/`:
   - `base.html`: Plantilla base con la estructura HTML principal.
   - `index.html`: Plantilla para mostrar la lista de tareas.
   - `detail.html`: Plantilla para mostrar los detalles de una tarea.
   - `create.html`: Plantilla para crear una nueva tarea.
   - `update.html`: Plantilla para actualizar una tarea existente.

6. Configurar las rutas en `tasks/urls.py`:
   ```python
   from django.urls import path
   from . import views

   urlpatterns = [
       path('', views.task_list, name='task_list'),
       path('task/<int:task_id>/', views.task_detail, name='task_detail'),
       path('task/create/', views.task_create, name='task_create'),
       path('task/<int:task_id>/update/', views.task_update, name='task_update'),
       path('task/<int:task_id>/delete/', views.task_delete, name='task_delete'),
   ]
   ```

7. Agregar la aplicación `tasks` al archivo `todolist/settings.py` en la lista `INSTALLED_APPS`:
   ```python
   INSTALLED_APPS = [
       # ...
       'tasks',
   ]
   ```

8. Incluir las rutas de la aplicación `tasks` en `todolist/urls.py`:
   ```python
   from django.contrib import admin
   from django.urls import path, include

   urlpatterns = [
       path('admin/', admin.site.urls),
       path('', include('tasks.urls')),
   ]
   ```

9. Ejecutar las migraciones y crear la base de datos:
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

10. Iniciar el servidor de desarrollo local y probar la aplicación:
    ```
    python manage.py runserver
    ```

Con estos pasos, has creado una aplicación de lista de tareas pendientes utilizando Django. La aplicación permite a los usuarios agregar, modificar y eliminar tareas. Puedes utilizar tags en GitHub para marcar diferentes versiones del proyecto, como "Cap1", "Cap4", etc. A medida que avanzas en los capítulos, puedes actualizar el proyecto para reflejar los conceptos aprendidos.