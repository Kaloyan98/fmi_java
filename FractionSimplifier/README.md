Task Description:

Create a public class FractionSimplifier with a method:

public static String simplify(String fraction)

The method should, given a string representing a fraction, return a string representing the simplified fraction that is equivalent to the input.
A fraction is considered simplified if there is no common divisor, other than 1, for both the numerator and denominator.
For example, 4/6 is not simplified because 4 and 6 have a common divisor of 2. If an improper fraction is equal to a whole number, the method should return the whole number as a string.

Examples:

Method Call	Result
simplify("4/6")	       "2/3"
simplify("10/11")	    "10/11"
simplify("100/400")    "1/4"
simplify("8/4")	        "2"
