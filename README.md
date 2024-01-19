# Oops-task
1.  Create a class Person with properties (name and age) with following features. a. Default age of person should be 18;
b. A person object can be initialized with name and age;
c. Method to display name and age of person

public class Person {
    private String name;
    private int age;

    // Default constructor with age set to 18
    public Person() {
        this.age = 18;
    }

    // Parameterized constructor to initialize name and age
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Method to display name and age of the person
    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }

    // Getter and setter methods for name
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // Getter and setter methods for age
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public static void main(String[] args) {
        // Create a person object using the default constructor
        Person defaultPerson = new Person();
        defaultPerson.displayInfo();

        // Create a person object with a name and age using the parameterized constructor
        Person namedPerson = new Person("Joe", 25);
        namedPerson.displayInfo();
    }
}

2. Create class Product (pid, price, quantity) with parameterized constructor. Create a main function in different class (say XYZ) and perform following task: a. Accept five product information from user and store in an array
b. Find Pid of the product with the highest price.
c. Create method (with array of product's object as argument) in XYZ class to calculate and return the total amount spent on all products. (amount spent on
single product-price of product * quantity of product

import java.util.Scanner;

class Product {
    private int pid;
    private double price;
    private int quantity;

    // Parameterized constructor
    public Product(int pid, double price, int quantity) {
        this.pid = pid;
        this.price = price;
        this.quantity = quantity;
    }

    // Getter method for pid
    public int getPid() {
        return pid;
    }

    // Getter method for price
    public double getPrice() {
        return price;
    }

    // Getter method for quantity
    public int getQuantity() {
        return quantity;
    }
}

public class XYZ {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Accept five product information from the user and store in an array
        Product[] products = new Product[5];

        for (int i = 0; i < 5; i++) {
            System.out.println("Enter details for product " + (i + 1));
            System.out.print("Enter product ID: ");
            int pid = scanner.nextInt();

            System.out.print("Enter product price: ");
            double price = scanner.nextDouble();

            System.out.print("Enter product quantity: ");
            int quantity = scanner.nextInt();

            products[i] = new Product(pid, price, quantity);
        }

        // Find Pid of the product with the highest price
        int highestPricePid = findHighestPricePid(products);
        System.out.println("Product with the highest price has PID: " + highestPricePid);

        // Calculate and return the total amount spent on all products
        double totalAmountSpent = calculateTotalAmountSpent(products);
        System.out.println("Total amount spent on all products: $" + totalAmountSpent);

        // Close the scanner to prevent resource leaks
        scanner.close();
    }

    // Method to find Pid of the product with the highest price
    private static int findHighestPricePid(Product[] products) {
        int highestPricePid = -1;
        double maxPrice = Double.MIN_VALUE;

        for (Product product : products) {
            if (product.getPrice() > maxPrice) {
                maxPrice = product.getPrice();
                highestPricePid = product.getPid();
            }
        }

        return highestPricePid;
    }

    // Method to calculate and return the total amount spent on all products
    private static double calculateTotalAmountSpent(Product[] products) {
        double totalAmountSpent = 0.0;

        for (Product product : products) {
            totalAmountSpent += product.getPrice() * product.getQuantity();
        }

        return totalAmountSpent;
    }
}

3) Create Class Account with data member As Balance. Create two constructors (no argument, and two arguments) and perform following task
a. method to deposit the amount to the account.
b. method to withdraw the amount from the account.
c.
method to display the Balance

import java.util.Scanner;

public class Account {
    private double balance;

    // Constructor with no arguments (default balance is set to 0.0)
    public Account() {
        this.balance = 0.0;
    }

    // Constructor with two arguments to set the initial balance
    public Account(double initialBalance) {
        this.balance = initialBalance;
    }

    // Method to deposit the amount to the account
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Amount deposited successfully. New balance: $" + balance);
        } else {
            System.out.println("Invalid deposit amount. Please enter a positive amount.");
        }
    }

    // Method to withdraw the amount from the account
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Amount withdrawn successfully. New balance: $" + balance);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient funds.");
        }
    }

    // Method to display the balance
    public void displayBalance() {
        System.out.println("Current balance: $" + balance);
    }

    public static void main(String[] args) {
        // Creating an account with the default constructor
        Account defaultAccount = new Account();
        defaultAccount.displayBalance();

        // Creating an account with the constructor that takes initial balance as an argument
        Account customAccount = new Account(1000.0);
        customAccount.displayBalance();

        // Depositing and withdrawing from the accounts
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the deposit amount for default account: ");
        double depositAmount = scanner.nextDouble();
        defaultAccount.deposit(depositAmount);

        System.out.print("Enter the withdrawal amount for custom account: ");
        double withdrawalAmount = scanner.nextDouble();
        customAccount.withdraw(withdrawalAmount);

        // Closing the scanner to prevent resource leaks
        scanner.close();
    }
}


4.Define a base class Person with attributes name and age.
Create a subclass Employee that inherits from Person and adds attributes like employeeID and salary.
Use the super keyword to initialize the Person attributes in the Employee constructor

class Person {
    private String name;
    private int age;

    // Constructor for Person class
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter methods for name and age
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

class Employee extends Person {
    private int employeeID;
    private double salary;

    // Constructor for Employee class using super keyword to initialize Person attributes
    public Employee(String name, int age, int employeeID, double salary) {
        super(name, age);
        this.employeeID = employeeID;
        this.salary = salary;
    }

    // Getter methods for employeeID and salary
    public int getEmployeeID() {
        return employeeID;
    }

    public double getSalary() {
        return salary;
    }
}

public class Main {
    public static void main(String[] args) {
        // Create an Employee object with sample input
        Employee employee = new Employee("John Doe", 30, 12345, 50000.0);

        // Access attributes from the Person class
        System.out.println("Employee Name: " + employee.getName());
        System.out.println("Employee Age: " + employee.getAge());

        // Access attributes from the Employee class
        System.out.println("Employee ID: " + employee.getEmployeeID());
        System.out.println("Employee Salary: $" + employee.getSalary());
    }
}


