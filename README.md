# Perfect-Number-or-Not-in-Java

Perfect Number or Not in Java
Check Whether or Not the Number is a Perfect Number in Java
Given an integer input as the number, the objective is to check whether or not the number can be represented as the sum of its factors except the number itself. Therefore, we write a code to Check Whether or Not a Number is a Perfect Number in Java Language.

Example
Input : 6
Output : Yes, it's a Perfect Number
Since, 6 = 1 + 2 + 3 (which are its divisors)
Check Whether or Not the Number is a Perfect Number in Java
Check Whether or Not the Number is a Perfect Number in Java Language
Method 1: Using range until the num – 1 (for loop)
Method 2: Using range until the num – 1 (while loop)
Method 3: Using range until num/2
Method 4: Using range until num/2 and a function
Method 5: Using recursion
Method 6: Using range until √num
We’ll discuss the above-mentioned methods in detail in the upcoming sections. Do check the blue box mentioned below for a better understanding of the above mentioned problem.

Perfect Number
A Number that can be represented as the sum of it's factors except the number itself is known as the Perfect Number.
Let's try and understand it better using an example

Example
Input : 6
Output : Yes, It's a Prefect Number
Explanation : Number = 6
Factors of 6 except 6 are 1, 2 and 3. 
When we add the three we get 6 itself. Therefore, it's a Perfect Number.
As mentioned above, 6 is a perfect number as it can be represented as the sum of it's factors except the number itself.
Perfect Number in Java
Method 1: Using range until num -1 (for loop)
Time Complexity: O(N)
Space Complexity: O(1)
Java Code
Run
public class Main
 {
   public static void main (String[]args)
   {

     int n = 28, sum = 0;

     for (int i = 1; i < n; i++)
       {
     	if (n % i == 0)
 	        sum = sum + i;
       }

     if (sum == n)
       System.out.println (n + " Is a perfect number");
     else
       System.out.println (n + " Is not a perfect number");

   }
 }
Output
28 Is a Perfect Number
Method 2: Using range until num -1 (while loop)
Time Complexity: O(N)
Space Complexity: O(1)
Java Code
Run
class Main
{
    public static void main (String[]args)
    {

        int num = 28, sum = 0, i = 1;

        // iteratively check for all numbers if they are divisors
        while(i < num)
        {
            // check if i is a divisor, if yes then add to sum
            if(num % i == 0)
                sum = sum + i;
            i++;
        }

        if (sum == num)
            System.out.println (num + " Is a perfect number");
        else
            System.out.println (num + " Is not a perfect number");

    }
}
Output
28 Is a Perfect Number
Method 3: In range until num/2 
This method uses optimization that all divisors of the number(excluding itself) can be found in the range [1, num/2]

Time Complexity: O(N)
Space Complexity: O(1)
Java Code
Run
class Main
{
    public static void main (String[]args)
    {

        int num = 28, sum = 0, i = 1;

        // all divisors of the numbers (excluding the number itself)
        // can be found before num/2
        // note we will need to use '=' sign as for even numbers
        // like 28, half of the number i.e 14 will also be the divisor
        while(i <= num/2)
        {
            // check if i is a divisor, if yes then add to sum
            if(num % i == 0)
                sum = sum + i;
            i++;
        }

        if (sum == num)
            System.out.println (num + " Is a perfect number");
        else
            System.out.println (num + " Is not a perfect number");

    }
}
Output
28 Is a Perfect Number
Method 4: Using range until number/2 and a function
We will use a function for the logic of a perfect number. This method also uses optimization that all divisors of the number(excluding itself) can be found before = number/2.

Time Complexity: O(N)
Space Complexity: O(1)
Java Code
Run
class Main
{
    public static void main (String[]args)
    {
        int num = 28;

        if (isPerfect(num))
            System.out.println (num + " Is a perfect number");
        else
            System.out.println (num + " Is not a perfect number");

    }

    private static boolean isPerfect(int num) {
        int sum = 0;
        
        // all divisors of num(excluding itself) can be found before num/2
        // remember put = sign as for even numbers like 28
        // half of it i.e. 14 would be divisor too e
        for (int i = 1; i <= num/2; i++){
            if (num % i == 0)
                sum = sum + i;
        }

        if (sum == num)
            return true;

        return false;
    }
}
Output
28 Is a Perfect Number
Method 5: Using Recursion
This method uses recursion in Java

Time Complexity: O(N)
Space Complexity: O(1)
Java Code
Run
class Main
{
    static long sum = 0;
    static long isPerfect(long num, int i)
    {
        // since, all factors can be found will num/2
        // we will only check in this range
        if(i <= num/2)
        {
            if(num % i ==0)
                sum = sum + i;

            i++;
            // recursively call isPerfect
            isPerfect(num, i);
        }

        //returns the sum
        // when i becomes > num/2
        return sum;
    }
    //driver code
    public static void main(String args[])
    {
        long num = 28;

        if(isPerfect(num, 1) == num)
            System.out.println(num+" is a perfect number");
        else
            System.out.println(num+" is not a perfect number");
    }
}
Output
28 is a Perfect Number
Method 6: Using range until √(Number)
This method uses observations that all factors come in pairs.

Time Complexity: O(√N)
Space Complexity: O(1)
All Factors come in pairs
For n = a * b (For each a there exists a unique b)

Example 1 : 100
(1,100), (2, 50), (4, 25), (5, 20), (10, 100)

Example 2 : 28
(1, 28), (2, 14), (4, 7)
Note : We will need to ignore pair of 1. As it will be the number itself.
Shorten the Loop
We can shorten the loop running between [1, num] to [1, √num]

Since we will find all pairs before √num (n = sqrt(n) * sqrt(n))

Example: For 28, all pairs can be found before √28 = 5.2
Java Code
Run
class Main
{
    public static void main (String[]args)
    {

        int n = 28;

        if(n == getDivisorsSum(n))
            System.out.println (n + " is a perfect number");
        else
            System.out.println (n + " is not a perfect number");

    }

    static int getDivisorsSum(int n)
    {
        int sum = 0;

        for(int i = 1; i < Math.sqrt(n); i++)
        {
            if (n % i == 0)
            {
                // For n : (1, n) will always be pair of divisor
                // acc to def., we must ignore adding num itself as divisor
                // when calculating for perfect number
                if(i == 1)
                    sum = sum + i;

                    // Example For 100 (10,10)  will be one pair
                    // But, we should add value to the sum just once
                else if(i == n/i)
                    sum = sum + i;

                    // add both pairs as divisors
                    // For any divisor i, n/i will also be a divisor
                else
                    sum = sum + i + n/i;
            }
        }
        return sum;
    }
}
Output
28 Is a Perfect Number
