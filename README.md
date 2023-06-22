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
Bank AC Detalis

package arul;

class BankAcDetails {
	
	private String NAME;
	public double BAL;
	private int Acno;
	public long MobNO;
	public String IFSC;

	
	BankAcDetails(String NAME, double BAL, int Acno,long MobNo, String IFSC) {
		this.BAL = BAL;
		this.NAME = NAME;
		this.IFSC = IFSC;
		this.MobNO = MobNo;
		this.Acno = Acno;
	}


	@Override
	public String toString() {
		return "BankAcDetails [NAME=" + NAME + ", BAL=" + BAL + ", Acno=" + Acno + ", MobNO=" + MobNO + ", IFSC=" + IFSC
				+ "]";
	}


	/**
	 * @return the nAME
	 */
	public String getNAME() {
		return NAME;
	}


	/**
	 * @param nAME the nAME to set
	 */
	public void setNAME(String nAME) {
		NAME = nAME;
	}


	/**
	 * @return the bAL
	 */
	public double getBAL() {
		return BAL;
	}


	/**
	 * @param bAL the bAL to set
	 */
	public void setBAL(double bAL) {
		BAL = bAL;
	}


	/**
	 * @return the acno
	 */
	public int getAcno() {
		return Acno;
	}


	/**
	 * @param acno the acno to set
	 */
	public void setAcno(int acno) {
		Acno = acno;
	}


	/**
	 * @return the mobNO
	 */
	public long getMobNO() {
		return MobNO;
	}


	/**
	 * @param mobNO the mobNO to set
	 */
	public void setMobNO(long mobNO) {
		MobNO = mobNO;
	}


	/**
	 * @return the iFSC
	 */
	public String getIFSC() {
		return IFSC;
	}


	/**
	 * @param iFSC the iFSC to set
	 */
	public void setIFSC(String iFSC) {
		IFSC = iFSC;
	}

}
Bank Manager Login

package arul;

import java.util.ArrayList;
import java.util.InputMismatchException;
import java.util.Scanner;

public class BankManager {

	static Scanner sc = new Scanner(System.in);
	static ArrayList<BankAcDetails> list = new ArrayList<>();
	static boolean flag = true;
	
	public static void LogInBankManager() throws InterruptedException {
		boolean flag = true;
		Thread.sleep(100);
		while (flag) {
			try {
				
				System.err.println(
						"select the option====>\n" + "1) create\n" + "2) delete\n" + "3) search\n" + "4) Exit");
				int choice = sc.nextInt();
				switch (choice) {

				case 1:
					create1();
					break;
				case 2:
					delete();
					break;
				case 3:
					search(sc);

					break;

				case 4:
					flag = false;
					break;
				default:
					System.out.println("invalid choice");
				}

			}

			catch (InputMismatchException e) {
				System.out.println("invalid input");
				sc.next();
			}

		}

	}

	

	public static void create1() {
		try {
		System.out.println("Enter the Account details in order===>\n");
		System.out.println("NAME");
		String name = sc.next();
		System.out.println("BALANCE");
		double bal = sc.nextDouble();
		System.out.println("AC.NO");
		int acno = sc.nextInt();
		long s=9999999999l;
		long mob1=0;
		while(mob1<=s) {
			System.out.println("enter the Mobile Number");
			long mob=sc.nextLong();
		if(mob<=s&&mob>99999999) {
			
			 mob1=mob;break;
		}	
		else {
			System.out.println("Enter the 10 digit in Mobile Number");
		}
		}
		System.out.println("IFSC CODE");
		String ifsc = sc.next();
		list.add(new BankAcDetails(name, bal, acno, mob1, ifsc));
		System.out.println("add account succcesfully1");
		}
		catch(InputMismatchException e){
			System.out.println("invalid input");sc.next();
		}

	}

	public static void delete() {

		System.out.println("enter the delete account acnno");
		int s = sc.nextInt();
		for (int i = 0; i < list.size(); i++) {
			if (list.get(i).getAcno() == s) {
				System.out.println(list.remove(i));
				System.out.println("Account successfully deleted");
			}
		}

		System.out.println("accout delelted");
	}

	public static void search(Scanner sc) {
		try {
		System.out.println("Enter account number");
		int acno = sc.nextInt();

		for (int i = 0; i < list.size(); i++) {

			if (list.get(i).getAcno() == acno) {
				System.out.println("bal" + list.get(i));

			}
			else {
				System.out.println("This account not available");
			}
		}
	}
		catch(InputMismatchException e) {
			System.out.println("invalid input");sc.next();
		}
	}
}

Customer Login
package arul;

import java.util.Scanner;

public class CustemerSide {
	static BankManager me = new BankManager();
	static Scanner sc = new Scanner(System.in);
	
	public static void main(String[] args) {
		
		String n="murugan";
		String s=sc.next();
		System.out.println(s);
		if(n.equals(s)) {
			System.out.println("hisssss da");
		}
		else {
			System.out.println("pod");
		}
		
	}
 }
	
