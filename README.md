Advanced To-Do App

A beginner-friendly Python project that demonstrates how to build an advanced command-line To-Do application using Python functions, file handling, loops, and task management features.

📌 Description

This program allows the user to:

Add tasks
View saved tasks
Delete tasks
Search tasks
Edit existing tasks
Exit the application

All tasks are stored permanently inside a file named task.txt.

The program also handles:

Missing task files
Empty task lists
Invalid task numbers
Case-insensitive searching

🧠 Concepts Used

Functions
File Handling
with open()
Read / Write / Append Modes
readlines() method
writelines() method
Lists
pop() method
enumerate() function
try-except
FileNotFoundError
while True loop
if-elif-else
String Methods
CRUD Operations (Create, Read, Update, Delete)

💻 Code

def add_task():
    task = input("Enter your task you wanna add:\n")

    with open("task.txt", "a") as file:
        file.write(task + "\n")

    print("Task saved")


def view_task():
    try:
        with open("task.txt", "r") as file:
            tasks = file.readlines()

        if len(tasks) == 0:
            print("No tasks found")
            return

        print("\nYour Tasks:")

        for i, task in enumerate(tasks, start=1):
            print(i, task.strip())

    except FileNotFoundError:
        print("No task file found")


def delete_task():
    try:
        with open("task.txt", "r") as file:
            tasks = file.readlines()

        if len(tasks) == 0:
            print("No tasks to delete")
            return

        print("\nTasks:")

        for i, task in enumerate(tasks, start=1):
            print(i, task.strip())

        delete_index = int(input("Enter the task number: ")) - 1

        if delete_index < 0 or delete_index >= len(tasks):
            print("Invalid task number")
            return

        tasks.pop(delete_index)

        with open("task.txt", "w") as file:
            file.writelines(tasks)

        print("Task deleted")

    except FileNotFoundError:
        print("Task file not found")


def search_task():
    found = False

    search = input("Enter what you want to search: ")

    try:
        with open("task.txt", "r") as file:
            tasks = file.readlines()

        print("Total tasks =", len(tasks))

        for i, task in enumerate(tasks, start=1):
            print(i, task.strip())

        print("\nSearch Results:")

        for task in tasks:
            if search.lower() in task.lower():
                print(task.strip())
                found = True

        if not found:
            print("Task not found")

    except FileNotFoundError:
        print("Task file not found")


def edit_file():
    with open("task.txt", "r") as file:
        tasks = file.readlines()

    for x, task in enumerate(tasks, start=1):
        print(x, task.strip())

    index = int(input("enter your task: ")) - 1

    new_task = input("Enter your new task: ")

    if 0 <= index < len(tasks):

        tasks[index] = new_task + "\n"

        with open("task.txt", "w") as file:
            for task in tasks:
                file.write(task)

        print("File updated")

    else:
        print("Invalid task number")


while True:

    print("\n===== TO DO LIST =====")
    print("1. Add task")
    print("2. View task")
    print("3. Delete task")
    print("4. Search task")
    print("5. Edit File")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_task()

    elif choice == "2":
        view_task()

    elif choice == "3":
        delete_task()

    elif choice == "4":
        search_task()

    elif choice == "5":
        edit_file()

    elif choice == "6":
        break

    else:
        print("Invalid choice")

▶️ Example Output

===== TO DO LIST =====
1. Add task
2. View task
3. Delete task
4. Search task
5. Edit File
6. Exit
Enter your choice: 1
Enter your task you wanna add:
Learn Python

Task saved
Enter your choice: 5
1 Learn Python

enter your task: 1
Enter your new task: Learn Advanced Python

File updated
