# Proyecto 2: Crear una aplicación de consola orientada a objetos

En este proyecto, continuaremos con la aplicación de lista de tareas pendientes del Proyecto 1, pero aplicaremos los conceptos de programación orientada a objetos aprendidos en el Capítulo 2. La estructura de archivos del proyecto será la siguiente:

```
todo_app/
├── main.py
├── todo.py
└── task.py
```

1. Crea un archivo llamado `task.py`. Este archivo contendrá la clase `Task`, que representa una tarea individual en nuestra aplicación:

```python
# task.py

class Task:
    def __init__(self, description, completed=False):
        self.description = description
        self.completed = completed

    def complete(self):
        self.completed = True

    def __str__(self):
        return f"{self.description} ({'Completed' if self.completed else 'Not Completed'})"
```

2. Crea un archivo llamado `todo.py`. Este archivo contendrá la clase `Todo`, que representará la lista de tareas pendientes y gestionará las tareas:

```python
# todo.py

from task import Task

class Todo:
    def __init__(self):
        self.tasks = []

    def add_task(self, description):
        task = Task(description)
        self.tasks.append(task)

    def complete_task(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index].complete()
        else:
            print("Índice de tarea no válido")

    def display_tasks(self):
        for index, task in enumerate(self.tasks):
            print(f"{index + 1}. {task}")
```

3. Modifica el archivo `main.py` para utilizar las clases `Todo` y `Task` en nuestra aplicación:

```python
# main.py

from todo import Todo

def main():
    todo_list = Todo()

    while True:
        print("\nMenu:")
        print("1. Añadir tarea")
        print("2. Completar tarea")
        print("3. Mostrar tareas")
        print("4. Salir")

        choice = input("Seleccione una opción: ")

        if choice == "1":
            description = input("Ingrese la descripción de la tarea: ")
            todo_list.add_task(description)

        elif choice == "2":
            index = int(input("Ingrese el número de la tarea a completar: ")) - 1
            todo_list.complete_task(index)

        elif choice == "3":
            todo_list.display_tasks()

        elif choice == "4":
            break

        else:
            print("Opción no válida, por favor intente de nuevo.")

if __name__ == "__main__":
    main()
```

Ahora, nuestra aplicación de lista de tareas pendientes utiliza clases y objetos para representar y gestionar las tareas. Ejecuta `main.py` para probar la aplicación y ver cómo funciona con la nueva estructura orientada a objetos.