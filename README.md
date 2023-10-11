import java.util.ArrayList;
import java.util.Scanner;

class ToDoItem {
    private String description;
    private boolean isComplete;

    public ToDoItem(String description) {
        this.description = description;
        this.isComplete = false;
    }

    public String getDescription() {
        return description;
    }

    public boolean isComplete() {
        return isComplete;
    }

    public void markAsComplete() {
        isComplete = true;
    }

    @Override
    public String toString() {
        return "[" + (isComplete ? "X" : " ") + "] " + description;
    }
}

public class test {
    private ArrayList<ToDoItem> items;

    public test() {
        items = new ArrayList<>();
    }

    public void addItem(String description) {
        ToDoItem item = new ToDoItem(description);
        items.add(item);
    }

    public void markItemAsComplete(int index) {
        if (index >= 0 && index < items.size()) {
            items.get(index).markAsComplete();
        }
    }

    public void removeItem(int index) {
        if (index >= 0 && index < items.size()) {
            items.remove(index);
        }
    }

    public void displayItems() {
        System.out.println("To-Do List:");
        for (int i = 0; i < items.size(); i++) {
            System.out.println(i + ". " + items.get(i));
        }
    }

    public static void main(String[] args) {
        test toDoList = new test();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nOptions:");
            System.out.println("1. Add To-Do Item");
            System.out.println("2. Mark Item as Complete");
            System.out.println("3. Remove Item");
            System.out.println("4. Display To-Do List");
            System.out.println("5. Quit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline

            switch (choice) {
                case 1:
                    System.out.print("Enter a description: ");
                    String description = scanner.nextLine();
                    toDoList.addItem(description);
                    break;
                case 2:
                    System.out.print("Enter the item number to mark as complete: ");
                    int index = scanner.nextInt();
                    scanner.nextLine(); // Consume the newline
                    toDoList.markItemAsComplete(index);
                    break;
                case 3:
                    System.out.print("Enter the item number to remove: ");
                    int removeIndex = scanner.nextInt();
                    scanner.nextLine(); // Consume the newline
                    toDoList.removeItem(removeIndex);
                    break;
                case 4:
                    toDoList.displayItems();
                    break;
                case 5:
                    System.out.println("Goodbye!");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
