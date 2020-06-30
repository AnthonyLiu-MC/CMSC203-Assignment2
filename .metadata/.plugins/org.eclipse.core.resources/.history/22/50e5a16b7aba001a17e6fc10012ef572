import javax.swing.JOptionPane;
import java.io.*;
import java.text.DecimalFormat;
import java.util.Random;

/****************************************************************
 * CMSC203 Assignment 2 Summer I 2020
 * Program: Assignment 2 Birthday Gift
 * Instructor: Dr. Grinberg
 * Description: A program takes in the names, ages, and choices of gifts from
 * user and returns order information to user.
 * Due: 07/05/2020
 * I pledge that I have completed the programming assignment independently
 * I have not given my code to any student.
 * Anthony Liu
 ****************************************************************/

public class Birthday{

	public static void main (String[] args) throws IOException {

		// Writes dialog welcome message
		JOptionPane.showMessageDialog(null, "Welcome to the Toy Company \nto choose gifts for young children");

		// Console Header message
		System.out.println("BIRTHDAY GIFTS");
		System.out.println();

		// Initialize variable for do while loop
		String anotherGift = "";

		// Total cost of order
		double totalCost = 0;

		// Formatter of totalCost
		DecimalFormat dollar = new DecimalFormat("#,##0.00");

		// Loop that asks user for order information, stops when user does not need
		// another gift
		do {

			// Initialize and open dialog input for child's name, age, and toy
			String name = JOptionPane.showInputDialog("Enter the name of the child");
			int age = Integer.parseInt(JOptionPane.showInputDialog("How old is the child?"));
			String pickedToy = JOptionPane.showInputDialog("Choose a toy: a plushie, blocks, or a book");

			// Checks if pickedToy is a valid input, asks for another input if it is invalid
			while (!pickedToy.equalsIgnoreCase("plushie") && !pickedToy.equalsIgnoreCase("blocks")
					&& !pickedToy.equalsIgnoreCase("book")) {

				pickedToy = JOptionPane.showInputDialog("Invalid Toy: Please choose plushie, blocks, or book"); 
			}

			// Creates toy object with user input
			Toy toy = new Toy(pickedToy, age);

			// boolean flag to determine if toy is age appropriate
			boolean goodGift = toy.ageOK();

			// Asks user if they want to cancel toy if it isn't age appropriate
			if (!goodGift) {
				String giftOk = JOptionPane
						.showInputDialog("Not age appropriate, do you want to cancel this toy request? Yes or No");
				if (giftOk.equalsIgnoreCase("no")) {
					goodGift = true;
				} else {

					anotherGift = "yes";

				}

			}
			
			//Asks user if they want to add a card or balloon with gift
			if (goodGift) {

				String card = JOptionPane.showInputDialog("Do you want a card with the gift? Yes or No");
				toy.addCard(card); //Adds card cost to toy cost

				String balloon = JOptionPane.showInputDialog("Do you want a balloon with the gift? Yes or No");
				toy.addBalloon(balloon); //Adds balloon cost to toy cost
				
				System.out.println("The gift for " + name + toy.toString()); //Prints out string of gift information
				totalCost += toy.getCost(); //Adds cost of toy to totalCost

				anotherGift = JOptionPane.showInputDialog("Do you want another toy? Yes or No");

			}

		} while (anotherGift.toLowerCase().equals("yes"));

		// Create random object and format random 5 digit number
		Random rand = new Random();
		int num = rand.nextInt(100000);
		String orderNumber = String.format("%05d", num);

		// Prints total cost, order number, and programmer's name to console
		System.out.println("The total cost of your order is $" + dollar.format(totalCost));
		System.out.println("Order number is: " + orderNumber);
		System.out.println("Programmer: Anthony Liu");

	}

}
