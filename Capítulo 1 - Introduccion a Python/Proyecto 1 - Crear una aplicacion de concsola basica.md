# Proyecto 1: Crear una aplicación de consola básica - Lista de tareas

En este proyecto, aplicaremos los conceptos aprendidos en el Capítulo 1 para crear una aplicación de consola básica que permita a los usuarios gestionar una lista de tareas. La aplicación permitirá a los usuarios agregar, eliminar y ver tareas en la lista. A lo largo del proyecto, utilizaremos variables, tipos de datos, operadores, estructuras de control, funciones y manejo de excepciones.

1. Definir una función para mostrar el menú de opciones:

```python
def display_menu():
    print("1. Agregar tarea")
    print("2. Eliminar tarea")
    print("3. Ver lista de tareas")
    print("4. Salir")
```

2. Definir una función para agregar tareas a la lista:

```python
def add_task(task_list):
    task = input("Ingrese la descripción de la tarea: ")
    task_list.append(task)
    print("Tarea agregada.")
```

3. Definir una función para eliminar tareas de la lista:

```python
def remove_task(task_list):
    try:
        task_index = int(input("Ingrese el índice de la tarea a eliminar: "))
        del task_list[task_index]
        print("Tarea eliminada.")
    except IndexError:
        print("Índice de tarea inválido.")
    except ValueError:
        print("Entrada inválida. Por favor, ingrese un número.")
```

4. Definir una función para mostrar la lista de tareas:

```python
def view_tasks(task_list):
    if len(task_list) == 0:
        print("No hay tareas en la lista.")
    else:
        for index, task in enumerate(task_list):
            print(f"{index}. {task}")
```

5. Implementar el bucle principal de la aplicación:

```python
def main():
    task_list = []

    while True:
        display_menu()

        try:
            choice = int(input("Ingrese su opción: "))

            if choice == 1:
                add_task(task_list)
            elif choice == 2:
                remove_task(task_list)
            elif choice == 3:
                view_tasks(task_list)
            elif choice == 4:
                break
            else:
                print("Opción inválida. Por favor, ingrese un número entre 1 y 4.")
        except ValueError:
            print("Entrada inválida. Por favor, ingrese un número.")

        print()

if __name__ == "__main__":
    main()
```

Con esta aplicación básica de lista de tareas, hemos aplicado y reforzado los conceptos aprendidos en el Capítulo 1. A medida que avanzamos en la capacitación y aprendamos sobre el desarrollo web y otros conceptos avanzados, podremos expandir y mejorar esta aplicación.