Task Description:

Create a public class FunnelChecker with a method:

public static boolean isFunnel(String str1, String str2)

The method should determine, given two strings str1 and str2, whether the second string can be obtained from the first by removing exactly one character.

Examples:

Method Call	Result
isFunnel("leave", "eave")  	      true
isFunnel("reset", "rest")	        true
isFunnel("dragoon", "dragon")  	  true
isFunnel("eave", "leave")	        false
isFunnel("sleet", "lets")	        false
isFunnel("skiff", "ski")	        false
