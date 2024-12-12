# Python_Day_18
#To-Do List Application

#Define the Main Functions
# Initialize an empty list to store tasks
tasks = []

# Function to add a task
def add_task(task):
    tasks.append(task)
    print(f"Task '{task}' added.")

# Function to view all tasks
def view_tasks():
    print("\nTo-Do List:")
    for index, task in enumerate(tasks, start=1):
        print(f"{index}. {task}")

# Function to remove a task by its number
def remove_task(task_number):
    try:
        task = tasks.pop(task_number - 1)
        print(f"Task '{task}' removed.")
    except IndexError:
        print("Invalid task number.")








        ### Save and Load Tasks from a File
# Function to save tasks to a file
def save_tasks(filename):
    with open(filename, 'w') as file:
        for task in tasks:
            file.write(task + '\n')
    print(f"Tasks saved to {filename}.")

# Function to load tasks from a file
def load_tasks(filename):
    try:
        with open(filename, 'r') as file:
            for line in file:
                tasks.append(line.strip())
        print(f"Tasks loaded from {filename}.")
    except FileNotFoundError:
        print(f"{filename} not found.")







        #Main Menu
def main():
    filename = 'tasks.txt'
    load_tasks(filename)

    while True:
        print("\nMenu:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Remove Task")
        print("4. Save and Exit")

        choice = input("Choose an option: ")

        if choice == '1':
            task = input("Enter the task: ")
            add_task(task)
        elif choice == '2':
            view_tasks()
        elif choice == '3':
            task_number = int(input("Enter the task number to remove: "))
            remove_task(task_number)
        elif choice == '4':
            save_tasks(filename)
            break
        else:
            print("Invalid option. Please choose again.")

if __name__ == "__main__":
    main()
