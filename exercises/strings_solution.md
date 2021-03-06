# Solution to exercises: strings

### charAt(int index)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String text = scanner.nextLine();

        System.out.println("Output:");
        for (int i = 0; i < text.length(); i++) {
            char c = text.charAt(i);
            System.out.println("Index " + i + " Character " + c);
        }
    }
}
```

### compareTo(String anotherString)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s1 = scanner.next();
        String s2 = scanner.next();

        System.out.print("Output: ");
        if (s1.compareTo(s2) < 0) {
            System.out.println(s1 + ", " + s2);
        }
        else {
            System.out.println(s2 + ", " + s1);
        }
    }
}
```

### endsWith(String suffix)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s1 = scanner.next();
        String s2 = scanner.next();

        System.out.print("Output: ");
        if (s1.endsWith(s2)) {
            System.out.println(s2 + " is a suffix of " + s1);
        }
        else {
            System.out.println(s2 + " is NOT a suffix of " + s1);
        }
    }
}
```

### contains(String str)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s1 = scanner.next();
        String s2 = scanner.next();

        System.out.print("Output: ");
        if (s1.contains(s2)) {
            System.out.println(s2 + " is part of " + s1);
        }
        else {
            System.out.println(s2 + " is NOT part of " + s1);
        }
    }
}
```

### replace(char oldChar, char newChar) and replace(String target, String replacement)

```java
class StringTest {
    public static void main(String[] args) {

        String encrypted = "lala#lwve#-rwgra22lalang!#<3";

        String x1 = encrypted.replace('w', 'o');
        String x2 = x1.replace('#', ' ');
        String x3 = x2.replace('2', 'm');
        String x4 = x3.replace("lala", "i");
        String decrypted = x4.replace('-', 'p');

        System.out.println(decrypted);
    }
}
```

A more elegant alternative is:

```java
class StringTest {
    public static void main(String[] args) {

        String encrypted = "lala#lwve#-rwgra22lalang!#<3";

        String decrypted = encrypted
                .replace('w', 'o')
                .replace('#', ' ')
                .replace('2', 'm')
                .replace("lala", "i")
                .replace('-', 'p');

        System.out.println(decrypted);
    }
}
```

Both print: `i love programming! <3`.

### startsWith(String prefix)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s1 = scanner.next();
        String s2 = scanner.next();

        System.out.print("Output: ");
        if (s1.startsWith(s2)) {
            System.out.println(s2 + " is a prefix of " + s1);
        }
        else {
            System.out.println(s2 + " is NOT a prefix of " + s1);
        }
    }
}
```

### substring(int beginIndex, int endIndex)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s = scanner.next();
        int splitPos = scanner.nextInt();

        String part1 = s.substring(0, splitPos);
        String part2 = s.substring(splitPos);

        System.out.print("Output: " + part1 + " - " + part2);
    }
}
```

### String.valueOf(int i) and Integer.parseInt()

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Input: ");

        String xString = scanner.next();
        int xInt = Integer.parseInt(xString);
        int yInt = xInt + 10;
        String yString = String.valueOf(yInt);

        System.out.print("Output: " + yString);
    }
}
```

### equals(Object anObject) and equalsIgnoreCase(String anotherString)

```java
import java.util.Scanner;

class StringTest {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.println("Input:");
        String s1 = scanner.next();
        String s2 = scanner.next();

        System.out.print("Output: ");
        if (s1.equals(s2)) {
            System.out.println("Equal");
        }
        else if (s1.equalsIgnoreCase(s2)) {
            System.out.println("Not equal but equal with case ignored");
        }
        else {
            System.out.println("Not equal");
        }
    }
}
```

## Counting characters

```java
class CharCount {

    public static void main(String[] args) {

        String s = "Als Gregor Samsa eines Morgens aus unruhigen Träumen erwachte " +
                "fand er sich in seinem Bett zu einem ungeheueren Ungeziefer verwandelt.";

        int numberOfE = count(s, 'e');
        int numberOfU = count(s, 'u');

        System.out.println("There are " + numberOfE + " 'e's and " + numberOfU + " 'u's.");
    }

    /* Count how many times a character is present in a string */
    public static int count(String text, char c) {

        int charCount = 0;
        int n = text.length();

        for(int i = 0; i < n; i++) {

            char t = text.charAt(i);
            if (t == c) {
                charCount++;
            }

            // Also possible:
            // if (text.charAt(i) == c) ...
        }

        return charCount;
    }
}
```

## Reverse

Two possibilities:

```java
public static String reverse(String s) {
    String r = "";
    for (int i = 0; i < s.length(); i++) {
        r = s.charAt(i) + r;
    }
    return r;
}
```

Or:

```java
public static String reverse(String s) {
    String r = "";
    for (int i = s.length() - 1; i >= 0; i--) {
        r += s.charAt(i);
    }
    return r;
}
```

## Palindrome

It's very simple if we can reuse `reverse`:

```java
public static boolean isPalindrome(String word) {
    return word.equalsIgnoreCase(reverse(word));
}
```
