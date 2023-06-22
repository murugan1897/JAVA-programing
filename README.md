Bank Account Detalis Program
package arul;

import java.util.ArrayList;
import java.util.InputMismatchException;
import java.util.Scanner;

public class LogInAc {
	static String Un = "m";
	static int Ps = 1;
	static Scanner sc = new Scanner(System.in);
	static boolean flag = true;
	static {
		System.out.println("Welcome to Banking App\n_________________________");
	}

	public static void main(String[] args) throws InterruptedException {
		Thread.sleep(100);
		while (flag) {
			try {
				System.err.println(
						"Select the options=========>\n" + "1)LogInBankManager \n" + "2)LogInCustomerAc\n" + "3)exit");
				int choice = sc.nextInt();
				switch (choice) {
				case 1:
					logInBankManager();
					break;
				case 2:
					logInCustomerAc();
					break;
				case 3:
					flag = false;
					System.out.println("Thanks for using this app...............");
					break;

				default:
					System.out.println("invalid choice");
				}
			} catch (InputMismatchException e) {
				System.out.println("invalid input\n");
				sc.next();

			}
		}
	}

	public static void logInCustomerAc() throws InterruptedException {
		try {
			System.err.println("Welcome to the Customer log in_____________");
			System.out.println("Enter the User name");
			String s = sc.next();
			for (int i = 0; i < CustomerDetails.bm.list.size(); i++) {
				if (CustomerDetails.bm.list.get(i).getNAME().equals(s)) {
					System.out.println("Enter the User Acno");
					int p = sc.nextInt();
					if (CustomerDetails.bm.list.get(i).getAcno() == p) {
						CustomerDetails.LogInCustomerAc();
					} else {
						System.out.println("Wrong Password");
					}
				} else {
					System.out.println("Wrong UserName");
				}
			}
		}
		catch (InputMismatchException e) {
			System.err.println("invalid input");
			sc.next();
		}
	}

	public static void logInBankManager() throws InterruptedException {
		try {
			System.err.println("Welcome to the BankManager log in_______________");
			System.out.println("Enter the User name");
			String s = sc.next();
			if (Un.equals(s)) {
				System.out.println("Enter the Password");
				int p = sc.nextInt();
				if (Ps == p) {
					BankManager.LogInBankManager();
				} else {
					System.out.println("Wrong Passord");
				}
			} else {
				System.out.println("Wrong UserName");
			}
		} catch (InputMismatchException e) {
			System.err.println("invalid input");
			sc.next();
		}

	}

	public static void exit() {
		flag = false;
		System.out.println("Thankyou  using this app");
	}

}

