Task Description:

Create a public class WordAnalyzer with a method:

public static String getSharedLetters(String word1, String word2)

The method should, given two strings, return a string containing only the characters that appear in both input strings.
The input strings consist only of lowercase and uppercase Latin letters, and the comparison of strings should be case-insensitive.
The resulting string should be sorted lexicographically. If there are no common characters between the two strings, an empty string should be returned.

Examples:

Method Call	Result
getSharedLetters("house", "home")    	"eho"
getSharedLetters("Micky", "mouse")     "m"
getSharedLetters("house", "villa")     ""
