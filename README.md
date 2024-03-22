import java.util.InputMismatchException;


import java.util.Scanner;



public class Main
{

  // Function to validate input choice (Y/N)
  static boolean validateChoice (char choice)
  {
	return (choice == 'Y' || choice == 'y' || choice == 'N' || choice == 'n');


  }

  // Function to validate name input
  static boolean validateName (String name)
  {
	// Regular expression to match names with only letters and accept Roman numerals
	return name.matches
	  ("^(?!\\s*$)([a-zA-Z]{1,}|(?i)(?:X{0,3})(?:IX|IV|V?I{0,3}))(\\s+[a-zA-Z]*)*$");
  }



  // Function to validate course selection
  static boolean validateCourse (String course)
  {
	return (course.equals ("1") || course.equals ("2")
			|| course.equals ("3")
			|| course.equals ("4") || course.equals ("5"));


  }



  // Function to display job postings based on student's skill
  static void displayJobPostings (String studentCourse)
  {
	System.out.println ("Job Postings for " + studentCourse + ":");


	System.out.println ("1. Indeed");


	System.out.println ("2. Jobstreet");


	System.out.println ("3. Glassdoor");


	System.out.println ("4. LinkedIn");


	System.out.println ("5. Crossover");



  }

  // Function to prompt the user if they need anything else
  static void promptForAdditionalNeeds (String studentCourse, int timesAsked)
  {
	Scanner scanner = new Scanner (System.in);


	System.out.println
	  ("Is there anything else you need? Would you like us to help you search for job postings on the website?");


	System.out.println ("If not, please end the program.");


	System.out.print ("(Y/N): ");


	char choice = scanner.next ().charAt (0);


	if (choice == 'N' || choice == 'n')
	  {
		System.out.println
		  ("It's been a pleasure helping you. Good luck in your endeavor!");
		System.exit (0);		// End the program
	  }


	else if (choice == 'Y' || choice == 'y')
	  {
		// Proceed to display job postings based on the student's skill
		displayJobPostings (studentCourse);
		// Ask which job posting they would like to check for job posting
		System.out.print
		  ("Enter the number corresponding to the job posting you would like to check: ");
		int jobChoice = scanner.nextInt ();
		scanner.nextLine ();	// Ignore newline character in the input buffer

	  }
	else
	  {


		System.out.println ("Invalid choice. Please enter 'Y' or 'N'.");
		// Handle invalid input by recursively calling the function
		promptForAdditionalNeeds (studentCourse, timesAsked);
	  }


  }



  // Function to prompt the student to rate skills and calculate average rating
  static void rateSkills (String studentCourse, Scanner scanner)
  {
	// Define the skills for each course
	String[][]skills = {
	  {"Engine troubleshooting", "Electrical system diagnosis",
	   "Safety measures",

	   "Cooling system maintenance", "Oil change",
	   "Starting system schematics",

	   "Transmission installation", "Braking system repair", "Safety & tools",

	   "Servicing differential and front axle"},

// Define skills for other courses similarly
	  {"Skill 1 for course 2", "Skill 2 for course 2", "Skill 3 for course 2",

	   "Skill 4 for course 2", "Skill 5 for course 2", "Skill 6 for course 2",

	   "Skill 7 for course 2", "Skill 8 for course 2", "Skill 9 for course 2",

	   "Skill 10 for course 2"},

	  {"Skill 1 for course 3", "Skill 2 for course 3", "Skill 3 for course 3",

	   "Skill 4 for course 3", "Skill 5 for course 3", "Skill 6 for course 3",

	   "Skill 7 for course 3", "Skill 8 for course 3", "Skill 9 for course 3",

	   "Skill 10 for course 3"},


	  {"Skill 1 for course 4", "Skill 2 for course 4", "Skill 3 for course 4",

	   "Skill 4 for course 4", "Skill 5 for course 4", "Skill 6 for course 4",

	   "Skill 7 for course 4", "Skill 8 for course 4", "Skill 9 for course 4",

	   "Skill 10 for course 4"},


	  {"Skill 1 for course 5", "Skill 2 for course 5", "Skill 3 for course 5",

	   "Skill 4 for course 5", "Skill 5 for course 5", "Skill 6 for course 5",

	   "Skill 7 for course 5", "Skill 8 for course 5", "Skill 9 for course 5",

	   "Skill 10 for course 5"}

	};



	System.out.println
	  ("Please rate each of the following skills from 1 to 5 (1 being the lowest and 5 being the highest):");


	int totalRating = 0;
	for (int i = 0; i < 10; ++i)
	  {
		int rating;
		do


		  {


			System.out.print ("Skill " + (i + 1) + ": " +
							  skills[Integer.parseInt (studentCourse) -
									 1][i] + ": ");
			while (!scanner.hasNextInt ())
			  {
				System.out.println ("Invalid input. Please enter a number.");
				scanner.next ();	// Consume invalid input
			  }


			rating = scanner.nextInt ();
			if (rating < 1 || rating > 5)
			  {
				System.out.println
				  ("Invalid rating. Please rate each skill from 1 to 5.");
			  }


		  }


		while (rating < 1 || rating > 5);
		totalRating += rating;
	  }


	// Calculate average rating
	double averageRating = (double) totalRating / 10.0;

	// Display message based on average rating
	if (averageRating >= 4.5)
	  {
		System.out.
		  println ("Congratulations! You have an average rating of " +
				   averageRating +
				   ". Your skills align with what these companies are seeking in potential candidates:");
		switch (Integer.parseInt (studentCourse))
		  {
		  case 1:


			System.out.println ("1. Automotive Servicing Company A");
			System.out.println ("2. Automotive Servicing Company B");
			System.out.println ("3. Automotive Servicing Company C");
			System.out.println ("4. Automotive Servicing Company D");
			System.out.println ("5. Automotive Servicing Company E");
			break;
		  case 2:


			System.out.println ("1. Drafting Technology Company F");
			System.out.println ("2. Drafting Technology Company G");
			System.out.println ("3. Drafting Technology Company H");
			System.out.println ("4. Drafting Technology Company I");
			System.out.println ("5. Drafting Technology Company J");
			break;
		  case 3:


			System.out.println ("1. Computer Programming Company K");
			System.out.println ("2. Computer Programming Company L");
			System.out.println ("3. Computer Programming Company M");
			System.out.println ("4. Computer Programming Company N");
			System.out.println ("5. Computer Programming Company O");
			break;
		  case 4:


			System.out.println ("1. Computer Servicing System Company P");
			System.out.println ("2. Computer Servicing System Company Q");
			System.out.println ("3. Computer Servicing System Company R");
			System.out.println ("4. Computer Servicing System Company S");
			System.out.println ("5. Computer Servicing System Company T");
			break;
		  case 5:


			System.
			  out.println ("1. Hotel and Restaurant Servicing Company U");
			System.
			  out.println ("2. Hotel and Restaurant Servicing Company V");
			System.
			  out.println ("3. Hotel and Restaurant Servicing Company W");
			System.
			  out.println ("4. Hotel and Restaurant Servicing Company X");
			System.
			  out.println ("5. Hotel and Restaurant Servicing Company Y");
			break;
		  }


		// Provide link for portfolio and cover letter submission
		System.out.println
		  ("Kindly submit your portfolio and cover letter through the provided link: [Application Link].");


		System.out.println
		  ("After submitting your application, anticipate the employer contacting you in 5-7 working days.");

		// End the program
		System.exit (0);




	  }
	else
	  {


		System.out.println ("Your average rating is " + averageRating +
							". Proceeding to display job postings based on your skill.");



		// Proceed to display job postings based on the student's skill
		displayJobPostings (studentCourse);

		// Ask which job posting they would like to check for job posting
		System.out.print
		  ("Enter the number corresponding to the job posting you would like to check: ");




	  }


  }



  public static void main (String[]args)
  {
	Scanner scanner = new Scanner (System.in);

	// Input Information
	System.out.println ("Enter applicant information:");
	System.out.print ("Last Name: ");
	String studentLastName = scanner.nextLine ().trim ();
	while (!validateName (studentLastName))
	  {
		System.out.print ("Invalid input. Please enter a valid last name: ");
		studentLastName = scanner.nextLine ().trim ();
	  }

	System.out.print ("First Name: ");
	String studentFirstName = scanner.nextLine ().trim ();
	while (!validateName (studentFirstName))
	  {
		System.out.print ("Invalid input. Please enter a valid first name: ");
		studentFirstName = scanner.nextLine ().trim ();
	  }

	System.out.print ("Middle Name: ");
	String studentMiddleName = scanner.nextLine ().trim ();
	while (!validateName (studentMiddleName))
	  {
		System.
		  out.print ("Invalid input. Please enter a valid middle name: ");
		studentMiddleName = scanner.nextLine ().trim ();
	  }

	// Validate age
	int age = 0;				// Initialize age variable

// Validate age
boolean validAge = false;

        do {
            System.out.print("Age: ");
            try {
                age = Integer.parseInt(scanner.nextLine());
                if (age >= 18) {
                    validAge = true;
                } else {
                    System.out.println("Sorry, this program is only for individuals aged 18 and above.");
                    System.exit(0); // Terminate the program if age is below 18
                }
            } catch (NumberFormatException e) {
                System.out.println("Please enter a valid number for age.");
            }
        } while (!validAge);
        
	// Ask if they would like help from TechtaCoders
	System.out.print("Would you like help from TechtaCoders? (Y/N): ");
char helpChoice = scanner.next().charAt(0);

while (helpChoice != 'Y' && helpChoice != 'y' && helpChoice != 'N' && helpChoice != 'n') {
    System.out.print("Invalid input. Please enter 'Y' or 'N': ");
    helpChoice = scanner.next().charAt(0);

	  }

	if (helpChoice == 'N' || helpChoice == 'n')
	  {
		// Proceed to the next step
		System.out.println ("Proceeding to the next step...");

		// Ask if the student is ready to proceed
		System.out.print ("Are you ready to proceed? (Y/N): ");
char readyChoice = scanner.next().charAt(0);

while (readyChoice != 'Y' && readyChoice != 'y' && readyChoice != 'N' && readyChoice != 'n') {
    System.out.print("Invalid input. Please enter 'Y' or 'N': ");
    readyChoice = scanner.next().charAt(0);
		  }

		if (readyChoice == 'N' || readyChoice == 'n')
		  {
			System.out.println ("Thank you for your time. Goodbye!");
			return;
		  }
	  }

	// Select TechtaCoder
	System.out.
	  println ("Great! Choose a TechtaCoder from the options below:");


	System.out.println ("1. Mark");
	System.out.println ("2. Erich");


	System.out.println ("3. Larsen");
	System.out.println ("4. Wenjie");


	System.out.println ("5. Abraham");
	System.out.println ("6. Ken");


	System.out.print ("Enter the number corresponding to the TechtaCoder: ");
	int coderChoice = 0;
	boolean validCoderChoice = false;

	while (!validCoderChoice)
	  {
		try
		{
		  coderChoice = scanner.nextInt ();
		  scanner.nextLine ();	// Consume newline character

		  if (coderChoice >= 1 && coderChoice <= 6)
			{
			  validCoderChoice = true;
			}
		  else
			{
			  System.out.print
				("Invalid choice. Please enter a number between 1 and 6.: ");
			}
		}
		catch (InputMismatchException e)
		{
		  System.out.print ("Invalid input. Please enter a number: ");
		  scanner.nextLine ();	// Consume invalid input
		}
	  }

	// Display selected TechtaCoder
	String techtaCoder;
	switch (coderChoice)
	  {
	  case 1:
		techtaCoder = "Mark";
		break;
	  case 2:
		techtaCoder = "Erich";
		break;
	  case 3:
		techtaCoder = "Larsen";
		break;
	  case 4:
		techtaCoder = "Wenjie";
		break;
	  case 5:
		techtaCoder = "Abraham";
		break;
	  case 6:
		techtaCoder = "Ken";
		break;
	  default:
		techtaCoder = "Mark";
		break;
	  }

	System.out.println ("Chosen TechtaCoder: " + techtaCoder);

	// Ask the student to wait for the chosen TechtaCoder to assist
	System.out.println ("Please wait for " + techtaCoder + " to assist you.");

	// Ask if the student is ready to proceed
	System.out.print ("Are you ready to proceed? (Y/N): ");


	char readyChoice = scanner.next ().charAt (0);


	if (!validateChoice (readyChoice))
	  {
		System.out.print ("Invalid input. Please enter 'Y' or 'N': ");


		readyChoice = scanner.next ().charAt (0);
	  }


	if (readyChoice == 'N' || readyChoice == 'n')
	  {
		System.out.println ("Thank you for your time. Goodbye!");

		return;
	  }



	// Ask which course matches their skill
	System.out.println
	  ("Which course matches your skills? Type the number you selected.");


	System.out.println ("1. Automotive Servicing");


	System.out.println ("2. Drafting Technology");


	System.out.println ("3. Computer Programming");


	System.out.println ("4. Computer Servicing System");


	System.out.println ("5. Hotel and Restaurant Servicing");


	boolean validCourse = false;
	String studentCourse = "";


	while (!validCourse)
	  {
		System.out.print ("Enter course number: ");


		studentCourse = scanner.next ();


		if (!validateCourse (studentCourse))
		  {
			System.out.println ("Please enter a number from 1 to 5.");
		  }


		else
		  {


			validCourse = true;
		  }


	  }



	// Ask if they would like to get a resume template
	System.out.print ("Would you like to get a resume template? (Y/N): ");
	char resumeChoice = scanner.next ().charAt (0);

	while (!validateChoice (resumeChoice))
	  {
		System.out.print ("Invalid input. Please enter 'Y' or 'N': ");
		resumeChoice = scanner.next ().charAt (0);
	  }

	if (resumeChoice == 'Y' || resumeChoice == 'y')
	  {
		System.out.println ("Resume Template Link: [Enter Link]");
	  }


	// Ask if they would like to get interview samples
	System.out.print ("Would you like to get interview samples? (Y/N): ");
	char interviewChoice = scanner.next ().charAt (0);

	while (!validateChoice (interviewChoice))
	  {
		System.out.print ("Invalid input. Please enter 'Y' or 'N': ");
		interviewChoice = scanner.next ().charAt (0);
	  }

	if (interviewChoice == 'Y' || interviewChoice == 'y')
	  {
		System.out.print ("Interview Samples Link: ");
		switch (studentCourse.charAt (0))
		  {
		  case '1':


			System.out.println ("Automotive Servicing - [Enter Link]");
			break;
		  case '2':


			System.out.println ("Drafting Technology - [Enter Link]");
			break;
		  case '3':


			System.out.println ("Computer Programming - [Enter Link]");
			break;
		  case '4':


			System.out.println ("Computer Servicing System - [Enter Link]");
			break;
		  case '5':


			System.out.
			  println ("Hotel and Restaurant Servicing - [Enter Link]");
			break;
		  default:


			System.out.println ("Invalid course.");
			break;


		  }


	  }



	// Ask if they would like to get a reviewer
	System.out.print ("Would you like to get a reviewer? (Y/N): ");
	char reviewerChoice = scanner.next ().charAt (0);

	while (!validateChoice (reviewerChoice))
	  {
		System.out.print ("Invalid input. Please enter 'Y' or 'N': ");
		reviewerChoice = scanner.next ().charAt (0);
	  }

	if (reviewerChoice == 'Y' || reviewerChoice == 'y')
	  {
		System.out.print ("Reviewer Link: ");
		switch (studentCourse.charAt (0))
		  {
		  case '1':


			System.out.println ("Automotive Servicing - [Enter Link]");
			break;
		  case '2':


			System.out.println ("Drafting Technology - [Enter Link]");
			break;
		  case '3':


			System.out.println ("Computer Programming - [Enter Link]");
			break;
		  case '4':


			System.out.println ("Computer Servicing System - [Enter Link]");
			break;
		  case '5':


			System.out.
			  println ("Hotel and Restaurant Servicing - [Enter Link]");
			break;
		  default:


			System.out.println ("Invalid course.");
			break;


		  }


	  }



	// Prompt the student to rate skills and calculate average rating
	rateSkills (studentCourse, scanner);

	// Ask which job posting they would like to check for job posting
	int jobChoice = scanner.nextInt ();
	scanner.nextLine ();		// Ignore newline character in the input buffer

// Display link based on job posting selection
	switch (jobChoice)
	  {
	  case 1:


		if (studentCourse.equals ("1"))
		  {
			System.out.
			  println ("Automotive Servicing - Indeed: [Enter Link]");
		  }


		else if (studentCourse.equals ("2"))
		  {
			System.out.println ("Drafting Technology - Indeed: [Enter Link]");
		  }


		else if (studentCourse.equals ("3"))
		  {
			System.out.
			  println ("Computer Programming - Indeed: [Enter Link]");
		  }


		else if (studentCourse.equals ("4"))
		  {
			System.out.println
			  ("Computer Servicing System - Indeed: [Enter Link]");
		  }


		else if (studentCourse.equals ("5"))
		  {
			System.out.println
			  ("Hotel and Restaurant Servicing - Indeed: [Enter Link]");
		  }


		break;
	  case 2:


		if (studentCourse.equals ("1"))
		  {
			System.out.
			  println ("Automotive Servicing - Jobstreet: [Enter Link]");
		  }


		else if (studentCourse.equals ("2"))
		  {
			System.out.
			  println ("Drafting Technology - Jobstreet: [Enter Link]");
		  }


		else if (studentCourse.equals ("3"))
		  {
			System.out.
			  println ("Computer Programming - Jobstreet: [Enter Link]");
		  }


		else if (studentCourse.equals ("4"))
		  {
			System.out.println
			  ("Computer Servicing System - Jobstreet: [Enter Link]");
		  }


		else if (studentCourse.equals ("5"))
		  {
			System.out.println
			  ("Hotel and Restaurant Servicing - Jobstreet: [Enter Link]");
		  }


		break;
	  case 3:


		if (studentCourse.equals ("1"))
		  {
			System.out.
			  println ("Automotive Servicing - Glassdoor: [Enter Link]");
		  }


		else if (studentCourse.equals ("2"))
		  {
			System.out.
			  println ("Drafting Technology - Glassdoor: [Enter Link]");
		  }


		else if (studentCourse.equals ("3"))
		  {
			System.out.
			  println ("Computer Programming - Glassdoor: [Enter Link]");
		  }


		else if (studentCourse.equals ("4"))
		  {
			System.out.println
			  ("Computer Servicing System - Glassdoor: [Enter Link]");
		  }


		else if (studentCourse.equals ("5"))
		  {
			System.out.println
			  ("Hotel and Restaurant Servicing - Glassdoor: [Enter Link]");
		  }


		break;
	  case 4:


		if (studentCourse.equals ("1"))
		  {
			System.out.
			  println ("Automotive Servicing - LinkedIn: [Enter Link]");
		  }


		else if (studentCourse.equals ("2"))
		  {
			System.out.
			  println ("Drafting Technology - LinkedIn: [Enter Link]");
		  }


		else if (studentCourse.equals ("3"))
		  {
			System.out.
			  println ("Computer Programming - LinkedIn: [Enter Link]");
		  }


		else if (studentCourse.equals ("4"))
		  {
			System.out.println
			  ("Computer Servicing System - LinkedIn: [Enter Link]");
		  }


		else if (studentCourse.equals ("5"))
		  {
			System.out.println
			  ("Hotel and Restaurant Servicing - LinkedIn: [Enter Link]");
		  }


		break;
	  case 5:


		if (studentCourse.equals ("1"))
		  {
			System.out.
			  println ("Automotive Servicing - Crossover: [Enter Link]");
		  }


		else if (studentCourse.equals ("2"))
		  {
			System.out.
			  println ("Drafting Technology - Crossover: [Enter Link]");
		  }


		else if (studentCourse.equals ("3"))
		  {
			System.out.
			  println ("Computer Programming - Crossover: [Enter Link]");
		  }


		else if (studentCourse.equals ("4"))
		  {
			System.out.println
			  ("Computer Servicing System - Crossover: [Enter Link]");
		  }


		else if (studentCourse.equals ("5"))
		  {
			System.out.println
			  ("Hotel and Restaurant Servicing - Crossover: [Enter Link]");
		  }


		break;
	  default:


		System.out.println ("Invalid choice.");
		break;
		
		

	  }



	System.out.println
	  ("It has been a pleasure helping you. Best of luck with your application!");


  }


}
