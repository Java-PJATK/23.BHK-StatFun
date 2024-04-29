Let us now consider an example of two static functions: `isPrime` and `primesBetween`. Of course, as always in Java, they must be placed in a class. The first of these two functions checks if a given number is prime, the second prints prime numbers in a given interval invoking, for each number from the range, the first one.

# Listing 23 BHK-StatFun/StatFun.java

```java
public class StatFun {

    static boolean isPrime(int n) {
        n = n >= 0 ? n : -n;
        if (n <= 1) throw new IllegalArgumentException();
        if (n <= 3) return true;
        if (n%2 == 0) return false;
        boolean res = true;
        for (int p = 3; p*p <= n && res; p += 2)
            if (n%p == 0) res = false;
        return res;
    }

    static void primesBetween(int a, int b) {
        for (int num = a; num <= b; ++num) {
            boolean prime = isPrime(num);
            System.out.println(num + " is " +
                (prime ? "" : "NOT ") + "prime");
        }
    }

    public static void main (String[] args) {
        int c = 2;
        primesBetween(c, 20);
    }
} 
```


Explained

```java
// Declare a public class named StatFun
public class StatFun {

    // Define a static method isPrime that takes an integer n and returns a boolean value indicating if n is a prime number
    static boolean isPrime(int n) {
        // Ensure n is non-negative; if n is negative, make it positive
        n = n >= 0 ? n : -n;
        // If n is less than or equal to 1, throw an exception as these are not prime numbers
        if (n <= 1) throw new IllegalArgumentException();
        // If n is 2 or 3, return true as these are prime numbers
        if (n <= 3) return true;
        // If n is divisible by 2, return false as it's not a prime number
        if (n%2 == 0) return false;
        // Initialize a boolean variable res to true; it will be used to store the result
        boolean res = true;
        // Start a loop from 3, incrementing by 2 each time (to check only odd numbers), and continue as long as p squared is less than or equal to n and res is true
        for (int p = 3; p*p <= n && res; p += 2)
            // If n is divisible by p, set res to false as n is not a prime number
            if (n%p == 0) res = false;
        // Return the result stored in res
        return res;
    }

    // Define a static method primesBetween that takes two integers a and b and prints all prime numbers between them
    static void primesBetween(int a, int b) {
        // Start a loop from a to b inclusive
        for (int num = a; num <= b; ++num) {
            // Call the isPrime method for the current number num and store the result in the boolean variable prime
            boolean prime = isPrime(num);
            // Print the current number and whether it is prime or not
            System.out.println(num + " is " +
                (prime ? "" : "NOT ") + "prime");
        }
    }

    // Define the main method that will be the entry point of the program
    public static void main (String[] args) {
        // Declare an integer variable c and initialize it to 2
        int c = 2;
        // Call the primesBetween method with arguments c and 20 to print all prime numbers between 2 and 20
        primesBetween(c, 20);
    }
}
 
```

The program above prints:  

```
2 is prime
3 is prime
4 is NOT prime
5 is prime
6 is NOT prime
7 is prime
8 is NOT prime
9 is NOT prime
10 is NOT prime
11 is prime
12 is NOT prime
13 is prime
14 is NOT prime
15 is NOT prime
16 is NOT prime
17 is prime
18 is NOT prime
19 is prime
20 is NOT prime
```
