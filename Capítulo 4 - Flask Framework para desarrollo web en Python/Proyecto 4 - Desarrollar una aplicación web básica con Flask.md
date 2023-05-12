# Desarrollar una aplicación web básica con Flask

Ahora que hemos cubierto los conceptos clave de Flask, es hora de aplicarlos en un proyecto. Para este proyecto, vamos a crear una aplicación web básica de lista de tareas (To-Do List) utilizando Flask.

La estructura de archivos de la aplicación será la siguiente:

```
app/
  ├── static/
  │   ├── css/
  │   │   └── main.css
  ├── templates/
  │   ├── base.html
  │   ├── index.html
  │   ├── login.html
  │   ├── register.html
  ├── app.py
  ├── forms.py
  ├── tasks.py
  └── users.py
```

1. Comienza creando las plantillas `base.html`, `index.html`, `login.html` y `register.html` en la carpeta `templates`.

2. A continuación, crea el archivo `app.py` y configura tu aplicación Flask con las rutas y vistas necesarias.

3. Crea el archivo `forms.py` para definir los formularios de registro e inicio de sesión utilizando Flask-WTF y WTForms.

4. Implementa la funcionalidad de autenticación y autorización utilizando Flask-Login. Para ello, crea el archivo `users.py` con la clase de usuario y la función `load_user`.

5. Implementa la funcionalidad de la lista de tareas utilizando una estructura de datos básica en el archivo `tasks.py`.

6. Por último, agrega estilos CSS en el archivo `main.css` dentro de la carpeta `static/css`.

Al finalizar este proyecto, tendrás una aplicación web básica de lista de tareas utilizando Flask que permite a los usuarios registrarse, iniciar sesión, agregar tareas y marcarlas como completadas. Este proyecto te ayudará a consolidar tus conocimientos sobre Flask y te preparará para explorar técnicas y herramientas más avanzadas en el futuro.