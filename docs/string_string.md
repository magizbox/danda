## String

String manipulation is a basic operation of many algorithms and utilities such as data validation, text parsing, file conversions and others. The Java APIs contain three classes that are used to work with character data:

* `Character` -- A class whose instances can hold a single character value.
* `String` -- An immutable class for working with multiple characters.
* `StringBuffer` and `StringBuilder` -- Mutable classes for working with multiple characters.

The String and StringBuffer classes are two you will use the most in your programming assignments. You use the String class in situations when you want to prohibit data modification; otherwise you use the StringBuffer class.

### The String class

In Java Strings can be created in two different ways. Either using a new operator

```
String demo1 = new String("This is a string");

char[] demo2 = {'s','t','r','i','n','g'};
String str = new String(demo2);
```
or using a string literal

```
String demo3 = "This is a string";
```

The example below demonstrates differences between these initializations

```
String s1 = new String("Fester");
String s2 = new String("Fester");
String s3 = "Fester";
String s4 = "Fester";
```

Then

```
s1 == s2 returns false
s1 == s3 returns false
s3 == s4 returns true
```

Because of the importance strings in real life, Java stores (at compile time) all strings in a special internal table as long as you create your strings using a string literal String s3 = "Fester". This process is called canonicalization - it replaces multiple string objects with a single object. This is why in the above example s3 and s4 refer to the same object. Also note that creating strings like s3 and s4 is more efficient. Review the code example StringOptimization.java that demonstrates time comparisons between these two ways of string creation.

Here are some important facts you must know about strings:

**1.** A string is not an array of characters.
Therefore, to access a particular character in a string, you have to use the charAt() method. In this code snippet we get the fourth character which is 't':

```
String str = "on the  edge of history";
char ch = str.charAt(3);
```

**2.** The toString() method is used when we need a string representation of an object.

The method is defined in the Object class. For most important classes that you create, you will want to override toString() and provide your own string representation.

**3.** Comparing strings content using == is the most common mistake beginners do. You compare the content using either equals() or compareTo() methods.

### Basic String methods

The String class contains an enormous amount of useful methods for string manipulation. The following table presents the most common String methods:

* str.charAt(k)	returns a char at position k in str.
* str.substring(k)	returns a substring from index k to the end of str
* s.substring(k, n)	returns a substring from index k to index n-1 of str
* str.indexOf(s)	returns an index of the first occurrence of String s in str
* str.indexOf(s, k)	returns an index of String s starting an index k in str
* str.startsWith(s)	returns true if str starts with s
* str.startsWith(s, k)	returns true if str starts with s at index k
* str.equals(s)	returns true if the two strings have equal values
* str.equalsIgnoreCase(s)	same as above ignoring case
* str.compareTo(s)	compares two strings
* s.compareToIgnoreCase(t)	same as above ignoring case

Examine the code in [BasicStringDemo.java](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/strings.html) for further details.

### The StringBuffer class

In many cases when you deal with strings you will use methods available in the companion StringBuffer class. This mutable class is used when you want to modify the contents of the string. It provides an efficient approach to dealing with strings, especially for large dynamic string data. StringBuffer is similar to ArrayList in a way that the memory allocated to an object is automatically expanded to take up additional data.

Here is an example of reversing a string using string concatenation

```
public static String reverse1(String s)
{
   String str = "";

   for(int i = s.length() - 1; i>=0; i--)
      str += s.charAt(i);

   return str;
}
```

and using a StringBuffer's append

```
public static String revers2(String s)
{
   StringBuffer sb = new StringBuffer();

   for(int i = s.length() - 1; i>=0; i--)
      sb.append(s.charAt(i));

   return sb.toString();
}
```

Another way to reverse a string is to convert a String object into a StringBuffer object, use the reverse method, and then convert it back to a string:

```
public static String reverse3(String s)
{
   return new StringBuffer(s).reverse().toString();
}
```

The performance difference between these two classes is that StringBuffer is faster than String when performing concatenations. Each time a concatenation occurs, a new string is created, causing excessive system resource consumption.

Review the code example [StringOverhead.java](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/code/StringOverhead.java) that demonstrates time comparisons of concatenation on Strings and StringBuffer.

### StringTokenizer

This class (from java.util package) allows you to break a string into tokens (substrings). Each token is a group of characters that are separated by delimiters, such as an empty space, a semicolon, and so on. So, a token is a maximal sequence of consecutive characters that are not delimiters. Here is an example of the use of the tokenizer (an empty space is a default delimiter):

```
String s = "Nothing is as easy as it looks";
StringTokenizer st = new StringTokenizer(s);
while (st.hasMoreTokens())
{
    String token = st.nextToken();
    System.out.println( "Token [" + token + "]" );
}
```

Here, hasMoreTokens() method checks if there are more tokens available from the string, and nextToken() method returns the next token from the string tokenizer.

The set of delimiters (the characters that separate tokens) may be specified in the second argument of StringTokenizer. In the following example, StringTokenizer has a set of two delimiters: an empty space and an underscore:

```
String s = "Every_solution_breeds new problems";
StringTokenizer st = new StringTokenizer(s, " _");
while (st.hasMoreTokens())
{
    String token = st.nextToken();
    System.out.println( "Token [" + token + "]" );
}
```

### Regular Expressions

Regular expressions are the most common programming technique for scanning strings and extracting substrings based on common characteristics. They are an essential part of many programming languages. In the following table the left-hand column specifies the regular expression constructs, while the right-hand column describes the conditions under which each construct will match.

**Character Classes**

```
[abc]	        a, b, or c (simple class)
[^abc]	        Any character except a, b, or c (negation)
[a-zA-Z]	    a through z, or A through Z, inclusive (range)
[a-d[m-p]]	    a through d, or m through p: [a-dm-p] (union)
[a-z&&[def]]	d, e, or f (intersection)
[a-z&&[^bc]]	a through z, except for b and c: [ad-z] (subtraction)
[a-z&&[^m-p]]	a through z, and not m through p: [a-lq-z] (subtraction)
\\d	            any digit from 0 to 9
\\w	            any word character (a-z,A-Z,0-9 and _)
\\W	            any non-word character
\\s	            any whitespace character
?	            appearing once or not at all
*	            appearing zero or more times
+	            appearing one or more times
```

The Java String class has several methods that allow you to perform an operation using a regular expression on that string in a minimal amount of code.

#### The matches() method

The matches("regex") method returns true or false depending whether the string can be matched entirely by the regular expression "regex". For example,

```
"abc".matches("abc")
returns True,
```
but

```
"abc".matches("bc")
```

returns False. In the following code examples we match all strings that start with any number of dots (denoted by *), followed by "abc" and end with one or more underscores (denoted by +).

```
String regex = ".*"+"abc"+"_+";

"..abc___".matches(regex);

"abc___".matches(regex);

"abc_".matches(regex);
```

#### The replaceAll() method

The method replaceAll("regex", "replacement") replaces each substring of the myString that matches the given regular expression "regex" with the given "replacement". As an example, let us remove all non-letters from a given string

```
String str = "Nothing 2is as <> easy AS it +_=looks!";
str = str.replaceAll("[^a-zA-Z]", "");
```

The pattern "[a-zA-Z]" describes all letters (in upper and lower cases). Next we negate this pattern, to get all non-letters "[^a-zA-Z]".

In the next example, we replace a sequence of characters by "-"

```
String str = "aabfooaaaabfooabfoob";
str = str.replaceAll("a*b", "-");
```

The star "*" in the pattern "a*b" denotes that character "a" may be repeated zero or more times. The output: "-foo-foo-foo-";

#### The split() method

The split("regex") splits the string at each "regex" match and returns an array of strings where each element is a part of the original string between two "regex" matches.

In the following example we break a sentence into words, using an empty space as a delimiter:

```
String s = "Nothing is as easy as it looks";
String[] st = s.split(" ");
```

Tokens are stored in in an array of strings and could be be easily accessible using array indexes. In the next code example, we choose two delimiters: either an empty space or an underscore:

```
String s = "Every_solution_breeds new problems";
String[]st = s.split("_| ");
```

What if a string contains several underscores? We use "+", that denotes a repetitive pattern

```
String s = "Every_solution____breeds_new__problems";
String[] st = s.split("_+");
```

It's important to observe that split() might returns empty tokens. In the example below

```
String[] st = "Tomorrow".split("r");
```

we have three tokens, where the second token is empty string. That is so because split() returns tokens between two "regex" matches.

One of the widely use of split() is to break a given text file into words. This could be easily done by means of the metacharacter "\W" (any non-word character), which allows you to perform a "whole words only" search using a regular expression. A "word character" is either an alphabet character (a-z and A-Z) or a digit (0-9) or a underscore.

```
"Let's go, Steelers!!!".split("\\W");
```

returns the following array of tokens

```
[Let, s, go, Steelers]
```

Examine the code in [Split.java](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/code/Split.java) for further details.

#### Pattern matching

Pattern matching in Java is based on use of two classes

* [Pattern](http://java.sun.com/javase/6/docs/api/java/util/regex/Pattern.html)  - compiled representation of a regular expression.
* [Matcher](http://java.sun.com/javase/6/docs/api/java/util/regex/Matcher.html) - an engine that performs match operations.

A typical invocation is the following, first we create a pattern

```
String seq = "CCCAA";
Pattern p = Pattern.compile("C*A*");
```

In this example we match all substrings that start with any number of Cs followed by any number of As. Then we create a Matcher object that can match any string against our pattern

```
Matcher m = p.matcher(seq);
```

Finally, we do actual matching

```
boolean res = m.matches();
```

The Matcher class has another widely used method, called find(), that finds next substring that matches a given pattern. In the following example we cound the number of matches "ACC"

```
String seq = "CGTATCCCACAGCACCACACCCAACAACCCA";
Pattern p = Pattern.compile("A{1}C{2}");
Matcher m = p.matcher(seq);
int count = 0;
while( m.find() ) count++;
System.out.println("there are " + count + " ACC");
```

Examine the code example [Matching.java](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/code/Matching.java) for further details.

#### Pattern matching in Computational Biology

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/pix/helix.png)

The DNA (the genetic blueprint) of any species is composed of about 4 billion ACGT nucleotides. DNA forms a double helix that has two strands of DNA binding and twisting together. In pattern matching problems we ignore the fact that DNA forms a double helix, and think of it only as a single strand. The other strand is complimentary. Knowing one strand allows uniquely determine the other one. Thus, DNA is essentially a linear molecule that looks like a string composed out of only four characters A, C, G, and T:

```
CGTATCCCACAGCACCACACCCAACAACCC
```

Each nucleotides (also called a base) strongly binds to no more than two other bases. These links provides a linear model of DNA strand. The particular order of ACGT nucleotides is extremely important. Different orders generate humans, animals, corn, and other organisms. The size of the genome (a genome is all the DNA in an organism) does not necessarily correlate with the complexity of the organism it belongs to. Humans have less than a third as many genes as were expected.

Pattern matching in computational biology arises from the need to know characteristics of DNA sequences, such as

* find the best way to align two sequences.
* find any common subsequences
* determine how well a sequence fits into a given model.

Comparing various DNA sequencesn provide many uses. Current scientific theories suggest that very similar DNA sequences have a common ancestor. The more similar two sequences are, the more recently they evolved from a single ansestor. With such knowledge, for example, we can reconstruct a phylogenetic tree (known as a "tree of life".) that shows how long ago various organisms diverged and which species are closely related.

## Challenges

* [Strings: Making Anagrams](https://www.hackerrank.com/challenges/ctci-making-anagrams)

## References

* ["Strings". *Victor S.Adamchik, CMU*. 2009](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Strings/strings.html)
