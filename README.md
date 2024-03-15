# project4
#include<bits/stdc++.h>
using namespace std;

struct Task {
    string description;
    bool completed;

    Task(const string& desc) : description(desc), completed(false) {}
};

class TodoList {
private:
    vector<Task> tasks;

public:
    void addTask(const string& desc) {
        tasks.push_back(Task(desc));
    }

    void viewTasks() {
        cout << "Tasks:" << endl;
        for (size_t i = 0; i < tasks.size(); ++i) {
            cout << i + 1 << ". " << tasks[i].description << " - "
                 << (tasks[i].completed ? "Completed" : "Pending") << endl;
        }
    }

    void markTaskCompleted(size_t index) {
        if (index >= 0 && index < tasks.size()) {
            tasks[index].completed = true;
            cout << "Task marked as completed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }

    void removeTask(size_t index) {
        if (index >= 0 && index < tasks.size()) {
            tasks.erase(tasks.begin() + index);
            cout << "Task removed." << endl;
        } else {
            cout << "Invalid task index." << endl;
        }
    }
};

int main() {
    TodoList todoList;
    char choice;

    do {
        cout << "\nOptions:" << endl;
        cout << "1. Add Task" << endl;
        cout << "2. View Tasks" << endl;
        cout << "3. Mark Task as Completed" << endl;
        cout << "4. Remove Task" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case '1': {
                string task;
                cout << "Enter task description: ";
                cin.ignore();
                getline(cin, task);
                todoList.addTask(task);
                break;
            }
            case '2':
                todoList.viewTasks();
                break;
            case '3': {
                size_t index;
                cout << "Enter index of task to mark as completed: ";
                cin >> index;
                todoList.markTaskCompleted(index - 1);
                break;
            }
            case '4': {
                size_t index;
                cout << "Enter index of task to remove: ";
                cin >> index;
                todoList.removeTask(index - 1);
                break;
            }
            case '5':
                cout << "Exiting..." << endl;
                break;
            default:
                cout << "Invalid choice. Please enter a number between 1 and 5." << endl;
        }
    } while (choice != '5');

    return 0;
}
