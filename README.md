# SeaseExercise7
SeaseExercise7

package edu.cpt167.sease.project5;

import java.util.Scanner;

public class SeaseMainClass 
{
	
public static final String DESTINATION_A_NAME = "Rome, Italy";
public static final String DESTINATION_B_NAME = "London, England";
public static final String DESTINATION_C_NAME = "KeyWest, Florida";
public static final String DESTINATION_QUIT_NAME = "Quit";
public static final Double DESTINATION_A_PRICE = 1500.00;
public static final Double DESTINATION_B_PRICE = 750.00;
public static final Double DESTINATION_C_PRICE = 500.00;
public static final String TRANSPORTATION_A_NAME = "Airplane";
public static final String TRANSPORTATION_B_NAME = "Boat";
public static final Double TRANSPORTATION_A_PRICE = 500.00;
public static final Double TRANSPORTATION_B_PRICE = 250.00;
public static final String UPGRADE_A_NAME = "First-class transportation";
public static final String UPGRADE_B_NAME = "First-class lodging";
public static final String UPGRADE_C_NAME = "Guided tours";
public static final String UPGRADE_D_NAME = "All upgraded services";
public static final String UPGRADE_E_NAME = "No upgraded services";
public static final Double UPGRADE_A_PRICE = 75.00;
public static final Double UPGRADE_B_PRICE = 125.00;
public static final Double UPGRADE_C_PRICE = 50.00;
public static final Double UPGRADE_D_PRICE = 200.00;
public static final Double UPGRADE_E_PRICE = 0.00;
	
	public static void main(String[] args) 
	{
		
	//INTRODUCTION section
		
	//declare and initialize the Scanner
	Scanner input = new Scanner(System.in);
	//declare and initialize variables
	String personName = "";
	char selectionDestination = ' ';
	char selectionTransportation = ' ';
	char selectionUpgrade = ' ';
	String nameDestination = "";
	String nameTransportation = "";
	String nameUpgrade = "";
	double costLodging = 0.0;
	double costTransportation = 0.0;
	double costUpgrade = 0.0;
	double costTrip = 0.0;
	int countDestinationA = 0;
	int countDestinationB = 0;
	int countDestinationC = 0;
	int counterTrip = 0;
	double totalSalesTrip = 0.0;
	 
	//display the welcome banner
		
	displayWelcomeBanner();
			
	//INPUT section	
	
	//prompts the user for their name
	personName = getPersonName(input);
	 
	//prompts the user for their desired destination
	selectionDestination = validateSelectionDestination(input);
	 
		while (selectionDestination != 'Q') 
		{
			
		//prompts the user to select the transportation type
		selectionTransportation = validateSelectionTransportation(input);
		
		//prompts the user to select an upgrade 
		selectionUpgrade = validateSelectionUpgrade(input);
	
			if (selectionDestination == 'A')
			{
			//assignment statement
			nameDestination = DESTINATION_A_NAME;
			//assignment statement
			costLodging = DESTINATION_A_PRICE;
			countDestinationA++;
			}//End of if
			
			else if (selectionDestination == 'B')
			{
			//assignment statement
			nameDestination = DESTINATION_B_NAME;
			//assignment statement
			costLodging = DESTINATION_B_PRICE;
			countDestinationB++;
			}//End of else if
			
			else
			{
			//assignment statement
			nameDestination =  DESTINATION_C_NAME;
			//assignment statement
			costLodging = DESTINATION_C_PRICE;	
			countDestinationC++;
			}
			
			if (selectionTransportation == 'A')
			{
			//assignment statement
			nameTransportation = TRANSPORTATION_A_NAME;
			//assignment statement
			costTransportation = TRANSPORTATION_A_PRICE;
			}//End of if
			else
			{
			//assignment statement
			nameTransportation = TRANSPORTATION_B_NAME;
			//assignment statement
			costTransportation = TRANSPORTATION_B_PRICE;	
			}//End of else
			
			if (selectionUpgrade == 'A')
			{
			//assignment statement
			nameUpgrade = UPGRADE_A_NAME;
			//assignment statement
			costUpgrade = UPGRADE_A_PRICE;
			}//End of if
			
			else if (selectionUpgrade == 'B')
			{
			//assignment statement
			nameUpgrade = UPGRADE_B_NAME;
			//assignment statement
			costUpgrade = UPGRADE_B_PRICE;	
			}//End of else if
			
			else if (selectionUpgrade == 'C')
			{
			//assignment statement
			nameUpgrade = UPGRADE_C_NAME;
			//assignment statement
			costUpgrade = UPGRADE_C_PRICE;	
			}//End of else if
			
			else if (selectionUpgrade == 'D')
			{
			//assignment statement
			nameUpgrade = UPGRADE_D_NAME;
			//assignment statement
			costUpgrade = UPGRADE_D_PRICE;	
			}//End of else if
			
			else
			{
			//assignment statement
			nameUpgrade = UPGRADE_E_NAME;
			//assignment statement
			costUpgrade = UPGRADE_E_PRICE;	
			}//End of else
			
		//assignment statement to add up all the costs
		costTrip = costLodging + costTransportation + costUpgrade;
		//assignment statement to add one to the total trip amount
		counterTrip++;
		//assignment statement to calculate the total between all trips
		totalSalesTrip = totalSalesTrip + costTrip;
		
		//Output Section
		
		//report 
		displayReportTrip(nameDestination, costLodging, nameTransportation, costTransportation, nameUpgrade, costUpgrade, costTrip);
		
		selectionDestination = validateSelectionDestination(input);
			
		}//End of while loop
	//output selection structure
	//test to see if report should be printed
		
	if (counterTrip > 0)
	{
	displayFinalReport(personName, countDestinationA, countDestinationB, countDestinationC, counterTrip, totalSalesTrip);
	}
	//BORDER - output line used to make the output easier to read
	System.out.println("\n***** ***** ***** **** ***** ***** ***** ***** ***** *****");
		
	displayFareWellMessage(personName);
	
	//Close scanner
	input.close();
					
	}//End of main method
	
//Void method section

public static void displayWelcomeBanner()
{
System.out.println("Welcome to the TRAVEL Program!");
System.out.println("This program will allow you to input Travel locations");
System.out.println("and give you an amount on how much each one will cost.");
//BORDER - output line used to make the output easier to read
System.out.println("***** ***** ***** **** ***** ***** ***** ***** ***** *****");
}//END OF void method to display the welcome banner

public static String getPersonName(Scanner borrowedInput)
{
String localPersonName = "";
//prompts user for their name
System.out.println("Please enter your first name: ");
//assignment statement
localPersonName = borrowedInput.nextLine();
return localPersonName;
}

public static char validateSelectionDestination (Scanner borrowedInput)
{
char localSelectionDestination = ' ';
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("DESTINATION MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-15s%7s%5.2f%12s\n", "[A] ",  DESTINATION_A_NAME, "$", DESTINATION_A_PRICE, "/5 day stay" );
System.out.printf("%-6s%-8s%7s%5.2f%13s\n", "[B] ", DESTINATION_B_NAME,"$", DESTINATION_B_PRICE, "/5 day stay");
System.out.printf("%-6s%-18s%4s%5.2f%13s\n", "[C] ", DESTINATION_C_NAME,"$", DESTINATION_C_PRICE,  "/5 day stay");
System.out.printf("%-6s%-8s\n", "[Q] ", DESTINATION_QUIT_NAME);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
//assignment statement
localSelectionDestination = borrowedInput.next().toUpperCase().charAt(0);
//repetition structure
//validation loop for Destination
while (localSelectionDestination != 'A' && localSelectionDestination != 'B' && localSelectionDestination != 'C' && localSelectionDestination != 'Q')
{
//SIMPLE, SINGLE STATEMENT, ERROR MESSAGE
System.out.println("\n~~~Invalid selection.~~~\n");
//menu
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("DESTINATION MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-15s%7s%5.2f%12s\n", "[A] ",  DESTINATION_A_NAME, "$", DESTINATION_A_PRICE, "/5 day stay" );
System.out.printf("%-6s%-8s%7s%5.2f%13s\n", "[B] ", DESTINATION_B_NAME,"$", DESTINATION_B_PRICE, "/5 day stay");
System.out.printf("%-6s%-18s%4s%5.2f%13s\n", "[C] ", DESTINATION_C_NAME,"$", DESTINATION_C_PRICE,  "/5 day stay");
System.out.printf("%-6s%-8s\n", "[Q] ", DESTINATION_QUIT_NAME);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
//assignment statement
localSelectionDestination = borrowedInput.next().toUpperCase().charAt(0);
}//END OF validation loop selection of the Destination
return localSelectionDestination;	
}//End of validateSelectionDestination method

public static char validateSelectionTransportation (Scanner borrowedInput)
{
char localSelectionTransportation = ' ';
	
//menu
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("TRANSPORTATION MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-8s%4s%5.2f%6s\n", "[A] ", TRANSPORTATION_A_NAME, "$ ", TRANSPORTATION_A_PRICE, "/seat");
System.out.printf("%-6s%-8s%4s%5.2f%6s\n", "[B] ", TRANSPORTATION_B_NAME, "$ ", TRANSPORTATION_B_PRICE, "/seat");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
//assignment statement
localSelectionTransportation = borrowedInput.next().toUpperCase().charAt(0);
//repetition structure
//validation loop for Transportation selection

while (localSelectionTransportation != 'A' && localSelectionTransportation != 'B')
{
//SIMPLE, SINGLE STATEMENT, ERROR MESSAGE
System.out.println("\n~~~Invalid selection.~~~\n");
//menu
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("TRANSPORTATION MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-8s%4s%5.2f%6s\n", "[A] ", TRANSPORTATION_A_NAME, "$ ", TRANSPORTATION_A_PRICE, "/seat");
System.out.printf("%-6s%-8s%4s%5.2f%6s\n", "[B] ", TRANSPORTATION_B_NAME, "$ ", TRANSPORTATION_B_PRICE, "/seat");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
			
//assignment statement
localSelectionTransportation = borrowedInput.next().toUpperCase().charAt(0);
}//END OF validation loop - for Transportation menu
return localSelectionTransportation;
}//End of static validateSelectionTransportation method

public static char validateSelectionUpgrade(Scanner borrowedInput)
{
char localSelectionUpgrade = ' ';
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("UPGRADE MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-8s%7s%8.2f\n", "[A]", UPGRADE_A_NAME, "$", UPGRADE_A_PRICE );
System.out.printf("%-6s%-8s%14s%8.2f\n", "[B]", UPGRADE_B_NAME,"$", UPGRADE_B_PRICE);
System.out.printf("%-6s%-8s%21s%8.2f\n", "[C]", UPGRADE_C_NAME,"$", UPGRADE_C_PRICE);
System.out.printf("%-6s%-8s%12s%8.2f\n", "[D]", UPGRADE_D_NAME,"$", UPGRADE_D_PRICE);
System.out.printf("%-6s%-8s%13s%8.2f\n", "[E]", UPGRADE_E_NAME,"$", UPGRADE_E_PRICE);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
//assignment statement
localSelectionUpgrade = borrowedInput.next().toUpperCase().charAt(0);
//repetition structure
//validation loop for Upgrade menu
while (localSelectionUpgrade != 'A' && localSelectionUpgrade != 'B' && localSelectionUpgrade != 'C' && localSelectionUpgrade != 'D' && localSelectionUpgrade != 'E')
{
//SIMPLE, SINGLE STATEMENT, ERROR MESSAGE
System.out.println("\n~~~Invalid selection.~~~\n");
//menu
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu title
System.out.println("UPGRADE MENU");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu options
System.out.printf("%-6s%-8s%7s%8.2f\n", "[A]", UPGRADE_A_NAME, "$", UPGRADE_A_PRICE );
System.out.printf("%-6s%-8s%14s%8.2f\n", "[B]", UPGRADE_B_NAME,"$", UPGRADE_B_PRICE);
System.out.printf("%-6s%-8s%21s%8.2f\n", "[C]", UPGRADE_C_NAME,"$", UPGRADE_C_PRICE);
System.out.printf("%-6s%-8s%12s%8.2f\n", "[D]", UPGRADE_D_NAME,"$", UPGRADE_D_PRICE);
System.out.printf("%-6s%-8s%13s%8.2f\n", "[E]", UPGRADE_E_NAME,"$", UPGRADE_E_PRICE);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//menu prompt
System.out.print("Enter your selection here: ");
//assignment statement
localSelectionUpgrade = borrowedInput.next().toUpperCase().charAt(0);
}//END OF validation loop selection of the Upgrade menu
return localSelectionUpgrade;
}//End of char validateSelectionUpgrade method

public static void displayReportTrip(String nameDestination, double costLodging, String nameTransportation, double costTransportation, String nameUpgrade, double costUpgrade, double costTrip)
{
//report
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//report title
System.out.println("Trip Report");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
System.out.printf("%-6s%-11s%7s\n", "Destination Name", "", nameDestination);
System.out.printf("%-6s%-8s%7s%10.2f\n", "Lodging Price","", "$", costLodging);
System.out.printf("%-6s%-8s%7s\n", "Transportation Type", "", nameTransportation);
System.out.printf("%-6s%-1s%7s%10.2f\n", "Transportation Price","", "$", costTransportation);
System.out.printf("%-6s%-10s%7s\n", "Upgrade selection", "", nameUpgrade);
System.out.printf("%-6s%-14s%1s%10.2f\n", "Upgrade Price", "", "$", costUpgrade);
System.out.printf("%-6s%-6s%7s%10.2f\n", "Total Trip Cost","", "$", costTrip);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
	
	
}//End of void displayReportTrip
public static void displayFinalReport(String personName, int countDestinationA, int countDestinationB, int countDestinationC, int counterTrip, double totalSalesTrip)
{
//report
System.out.println("\n~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//report title
System.out.println("FINAL REPORT");
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
//report details
System.out.printf("%-18s%20s\n", "Traveler Name ", personName);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
System.out.printf("%-18s%17s%3d\n", "Count of Trips: ", "", counterTrip);
System.out.printf("%-18s%17s%3d\n", DESTINATION_A_NAME, "", countDestinationA);
System.out.printf("%-18s%17s%3d\n", DESTINATION_B_NAME, "", countDestinationB);
System.out.printf("%-18s%17s%3d\n", DESTINATION_C_NAME, "", countDestinationC);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");
System.out.printf("%-18s%10s%2s%8.2f\n", "Total Trip Sales","", "$ ", totalSalesTrip);
System.out.println("~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~ ~~~~");	
}//END OF void method to display the final report

public static void displayFareWellMessage(String personName)
{

System.out.println(personName + ", thank you for using the TRAVEL Program ");
System.out.println("Have a good one!");

//BORDER - output line used to make the output easier to read
System.out.println("***** ***** ***** **** ***** ***** ***** ***** ***** *****");
}//END OF void method to display the welcome banner



}
