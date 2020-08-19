public class EmailApp {
	public static void main(String args[]) {
		Email e1 = new Email("sonika", "meka");
		System.out.println(e1.randomPassword(8));
		System.out.println(e1.showinfo());
	}
}

public class Email {
	private String firstName;
	private String lastName;
	private String password;
	private String department;
	private int mailBoxCapacity = 500;
	private String email;

	public Email(String firstName, String lastName) {
		this.firstName = firstName;
		this.lastName = lastName;
		this.department = setDepartment();
		int defaultPasswordLength = 0;
		this.password = randomPassword(defaultPasswordLength);
		System.out.println("Your password is: " + this.password);
		email = firstName.toLowerCase() + "." + lastName.toLowerCase() + "@" + department + ".macys.com";
	}

	public String setDepartment() {
		System.out.print("New Worker: " + firstName
				+ "\nDEPARTMENT CODES:\n1 for Sales\n2 for Development\n3 for Accounting\n0 for None\nEnter the department code: ");
		try (Scanner in = new Scanner(System.in)) {
			int departmentchoice = in.nextInt();
			if (departmentchoice == 1) {
				return "Sales";
			} else if (departmentchoice == 2) {
				return "Development";
			} else if (departmentchoice == 3) {
				return "Accounting";
			} else {
				return " ";
			}
		}
	}

	public String randomPassword(int length) {
		String passwordCollection = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#!$%^&*";
		char[] password = new char[length];
		for (int i = 0; i < length; i++) {
			int rand = (int) (Math.random() * passwordCollection.length());
			password[i] = passwordCollection.charAt(rand);
		}
		return new String(password);
	}

	public void setMailBoxCapacity(int capacity) {
		this.mailBoxCapacity = capacity;
	}

	public int getMailboxCapacity() {
		return mailBoxCapacity;
	}

	public String showinfo() {
		return "DISPLAY NAME: " + firstName + " " + lastName + "\nCOMPANY EMAIL" + email + "\nMAILBOX CAPACITY "
				+ mailBoxCapacity + " mb";
	}

}
