# java3
a program of an atm interface using java
import java.util.Scanner;

class ATM {
    private static double balance = 1000.00;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int option;

        do {
            System.out.println("Welcome to the ATM!");
            System.out.println("1: Check Balance");
            System.out.println("2: Deposit Money");
            System.out.println("3: Withdraw Money");
            System.out.println("4: Exit");
            System.out.print("Please select an option: ");
            option = scanner.nextInt();

            switch (option) {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    depositMoney(scanner);
                    break;
                case 3:
                    withdrawMoney(scanner);
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    break;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        } while (option != 4);

        scanner.close();
    }

    private static void checkBalance() {
        System.out.printf("Your current balance is: $%.2f%n", balance);
    }

    private static void depositMoney(Scanner scanner) {
        System.out.print("Enter the amount to deposit: $");
        double depositAmount = scanner.nextDouble();
        if (depositAmount > 0) {
            balance += depositAmount;
            System.out.printf("You have successfully deposited $%.2f. Your new balance is $%.2f.%n", depositAmount, balance);
        } else {
            System.out.println("Invalid deposit amount. Please try again.");
        }
    }

    private static void withdrawMoney(Scanner scanner) {
        System.out.print("Enter the amount to withdraw: $");
        double withdrawAmount = scanner.nextDouble();
        if (withdrawAmount > 0 && withdrawAmount <= balance) {
            balance -= withdrawAmount;
            System.out.printf("You have successfully withdrawn $%.2f. Your new balance is $%.2f.%n", withdrawAmount, balance);
        } else if (withdrawAmount > balance) {
            System.out.println("Insufficient funds. Please try again.");
        } else {
            System.out.println("Invalid withdrawal amount. Please try again.");
        }
    }
}
