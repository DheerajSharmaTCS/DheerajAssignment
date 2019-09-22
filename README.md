# DheerajAssignment

/***Description: selenium testing code***

-Created java code to generate random numbers and stored it in an array.
-Then created 2 test cases Test1 and Test2 for verifying presence of random generated numbers 
 and other to check sorted list respectively.
-Using TestNG annotations to created test cases and report generation in test output folder.
-Everything is inside src/test.SortTestingProgram class.
-Github repository: https://github.com/DheerajSharmaTCS/DheerajAssignment.

*/


package test;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Random;

import org.testng.Assert;
import org.testng.Reporter;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

public class SortTestingProgram {

	ArrayList<Integer> obtainedList = new ArrayList<Integer>();
	ArrayList<Integer> sortedList = new ArrayList<Integer>();

	/*
	 * Created generateList() method to obtain a list of numbers between 1 to 100,
	 * assuming this obtainedList getting from UI application
	 */
	@BeforeTest
	public void generateList() {
		System.out.println("Testing Started");
		Random NumGenerator = new Random();
		for (int i = 0; i < 50; i++) {
			int number = NumGenerator.nextInt(100);
			obtainedList.add(number);
			System.out.println(obtainedList.get(i).toString());
		}

	}

	@Test(priority = 5)
	public void Test1() {
		Reporter.log("Obtained List for numbers -: ");
		for (int i = 0; i < 50; i++) {
			Reporter.log(obtainedList.get(i).toString());
		}
		Assert.assertNotNull(obtainedList); // verify presence of list
	}

	@Test(priority = 1)
	public void Test2() {
		Collections.sort(obtainedList);
		Reporter.log("Sorted List for numbers   --: ");
		for (int i = 0; i < 50; i++) {
			Reporter.log(obtainedList.get(i).toString());
		}
		sortedList.addAll(obtainedList);
		if (obtainedList.equals(sortedList)) {
			Assert.assertTrue(obtainedList.equals(sortedList));
			Reporter.log("<br><br>" + "The numbers are in sorted way.");
		} else {
			Reporter.log("<br><br>" + "The numbers are not in sorted way.");
		}
	}

}
