# Saiket_To-Do-List-Project

#  To-Do List Application

A simple command-line To-Do List app built with Python.

## 🚀 Features

- Add new tasks
- View current tasks
- Mark tasks as completed



## ✅ 1. `Task` Class

```python
class Task:
    def __init__(self, description):
        self.description = description
        self.completed = False
```

###  Explanation:

* `Task` represents a single to-do item.
* When a new task is created, it stores:

  * `description` (what the task is about)
  * `completed` status (initially set to `False`, meaning not done)

---

```python
    def mark_completed(self):
        self.completed = True
```

* This method is called to **mark a task as completed**.
* It just sets `completed` to `True`.

---

```python
    def __str__(self):
        status = "✓" if self.completed else "✗"
        return f"[{status}] {self.description}"
```

* This method is called **automatically when the object is printed**.
* It returns a string like:

  * `[✗] Do homework` (if not completed)
  * `[✓] Do homework` (if completed)

---

## ✅ 2. `ToDoList` Class

```python
class ToDoList:
    def __init__(self):
        self.tasks = []
```

* `ToDoList` is a manager class that holds **all the tasks** in a list called `self.tasks`.

---

```python
    def add_task(self, description):
        task = Task(description)
        self.tasks.append(task)
        print("Task added!")
```

* This method:

  1. Creates a new `Task` object
  2. Adds it to the list of tasks
  3. Prints confirmation

---

```python
    def view_tasks(self):
        if not self.tasks:
            print("No tasks found.")
            return
        print("\nYour Tasks:")
        for i, task in enumerate(self.tasks, 1):
            print(f"{i}. {task}")
```

* Shows the current task list.
* Uses `enumerate(..., 1)` to number tasks starting from 1.
* If the list is empty, it tells the user.

---

```python
    def complete_task(self, task_number):
        if 0 < task_number <= len(self.tasks):
            self.tasks[task_number - 1].mark_completed()
            print("Task marked as completed.")
        else:
            print("Invalid task number.")
```

* Marks a specific task as completed.
* The user gives a number (like `2`), and it converts it to list index (`1`).
* Checks if the number is valid.

---

## ✅ 3. `main()` Function

```python
def main():
    todo_list = ToDoList()
```

* This function runs the app.
* It first creates a `ToDoList` object to manage all tasks.

---

```python
    while True:
        print("\n--- To-Do List Application ---")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Complete Task")
        print("4. Exit")
```

* This is a **menu loop**.
* Runs repeatedly until the user chooses to exit.

---

```python
        choice = input("Enter your choice (1-4): ")
```

* Asks the user what they want to do.

---

```python
        if choice == '1':
            description = input("Enter task description: ")
            todo_list.add_task(description)
```


---

```python
        elif choice == '2':
            todo_list.view_tasks()
```

* Option `2` displays all tasks.

---

```python
        elif choice == '3':
            try:
                task_number = int(input("Enter task number to mark as completed: "))
                todo_list.complete_task(task_number)
            except ValueError:
                print("Please enter a valid number.")
```

* Option `3` lets the user mark a task as completed.


```python
        elif choice == '4':
            print("Goodbye!")
            break
```

* Option `4` ends the program with a goodbye message.

---

```python
        else:
            print("Invalid choice. Try again.")
```


##  4. Run the Program

```python
if __name__ == "__main__":
    main()
```





## 📌 Summary

| Part                        | Purpose                                    |
| --------------------------- | ------------------------------------------ |
| `Task` class                | Represents a single to-do item             |
| `ToDoList` class            | Manages all tasks (add, view, complete)    |
| `main()`                    | Displays menu and handles user interaction |
| `if __name__ == "__main__"` | Starts the app                             |



