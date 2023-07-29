# ATM_Stimulator

import java.io.*;
import java.util.*;

public class ATMStimulator {
    private static double accountBalance = 1000.0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        boolean isRunning = true;

        System.out.println("Welcome to the ATM Simulator!");

        while (isRunning) {
            showMenu();
            int choice = scanner.nextInt();
            scanner.nextLine(); 

            switch (choice) {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    withdrawFunds(scanner);
                    break;
                case 3:
                    depositMoney(scanner);
                    break;
                case 4:
                    isRunning = false;
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }

        System.out.println("Thank you for using the ATM Simulator!");
        scanner.close();
    }

    private static void showMenu() {
        System.out.println("\nMain Menu:");
        System.out.println("1. Check Balance");
        System.out.println("2. Withdraw Funds");
        System.out.println("3. Deposit Money");
        System.out.println("4. Exit");
        System.out.print("Enter your choice: ");
    }

    private static void checkBalance() {
        System.out.println("Your account balance: $" + accountBalance);
    }

    private static void withdrawFunds(Scanner scanner) {
        System.out.print("Enter the amount to withdraw: ");
        double amount = scanner.nextDouble();
        scanner.nextLine(); 

        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive value.");
        } else if (amount > accountBalance) {
            System.out.println("Insufficient funds.");
        } else {
            accountBalance -= amount;
            System.out.println("Withdrawal successful. Remaining balance: $" + accountBalance);
        }
    }

    private static void depositMoney(Scanner scanner) {
        System.out.print("Enter the amount to deposit: ");
        double amount = scanner.nextDouble();
        scanner.nextLine(); 

        if (amount <= 0) {
            System.out.println("Invalid amount. Please enter a positive value.");
        } else {
            accountBalance += amount;
            System.out.println("Deposit successful. Updated balance: $" + accountBalance);
        }
    }
}
