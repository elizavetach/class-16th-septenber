# class-09-09
#### Task 1. 
### Task 8kyu, Abbreviate a Two Word Name: 
Write a function to convert a name into initials. This kata strictly takes two words with one space in between them.
The output should be two capital letters with a dot separating them.
It should look like this:
Sam Harris => S.H
patrick feeney => P.F
### My solution:
```public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    String[] names = name.split(" ");
    return (names[0].charAt(0) + "." + names[1].charAt(0)).toUpperCase();
  }
}
```
### Fav solution:
```
public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    return (name.charAt(0) + "." + name.charAt(name.indexOf(" ") + 1)).toUpperCase();
  }
}
```
[Task link]( https://www.codewars.com/kata/57eadb7ecd143f4c9c0000a3/java)

 

##### Task 2. 
### Task 8kyu, You only need one - Beginner: 
You will be given an array a and a value x. All you need to do is check whether the provided array contains the value.
Array can contain numbers or strings. X can be either.
Return true if the array contains the value, false if not.
### My solution: 
```public class Solution {

    public static boolean check(Object[] a, Object x) {
        for (int i = 0; i < a.length; i++)
            if (a[i] == x)
                return true;
        return false;
    }

}
```

### Fav solution:

```Java
import java.util.Arrays;
class Solution
{
    static boolean check(Object[] a, Object x)
    {
        return Arrays.asList(a).contains(x);
    }
}
```

[Task link](https://www.codewars.com/kata/57cc975ed542d3148f00015b/java)




# class-16-09
#### Task 1. 
### Task 7kyu, Switcheroo: 
Given a string made up of letters a, b, and/or c, switch the position of letters a and b (change a to b and vice versa). Leave any incidence of c untouched.
Example:
'acb' --> 'bca'
'aabacbaa' --> 'bbabcabb'
### My solution:
```public class Switch {
  public static String switcheroo(String x) {
     String ans="";
        String arr[]= x.split("");
        for( String i:arr)
            if( i.equals("a")) ans+="b";
            else if( i.equals("b")) ans+="a";
            else ans+=i;
        return ans;
  }
}
```
### Fav solution:
```public class Switch {
    public static String switcheroo(String x){
        return x.replaceAll("a","x")
                .replace("b","a")
                .replace("x","b");
    }
}
```
[Task link](https://www.codewars.com/kata/57f759bb664021a30300007d)

 

##### Task 2. 
### Task 8kyu, Over The Road: 
You've just moved into a perfectly straight street with exactly n identical houses on either side of the road. Naturally, you would like to find out the house number of the people on the other side of the street. The street looks something like this:

Street
1|   |6
3|   |4
5|   |2
  you
Evens increase on the right; odds decrease on the left. House numbers start at 1 and increase without gaps. When n = 3, 1 is opposite 6, 3 opposite 4, and 5 opposite 2.

Example (address, n --> output)
Given your house number address and length of street n, give the house number on the opposite side of the street.

1, 3 --> 6
3, 3 --> 4
2, 3 --> 5
3, 5 --> 8
Note about errors
If you are timing out, running out of memory, or get any kind of "error", read on. Both n and address could get upto 500 billion with over 200 random tests. If you try to store the addresses of 500 billion houses in a list then you will run out of memory and the tests will crash. This is not a kata problem so please don't post an issue. Similarly if the tests don't complete within 12 seconds then you also fail.

To solve this, you need to think of a way to do the kata without making massive lists or huge for loops. Read the discourse for some inspiration :)
### My solution: 
```class CodeWars {
  public static long overTheRoad(long address, long n) {

        if (address%2 == 0){
            long x = (n*2) - address;
            return 1+x;
        }
        else {
            long x = (n*2) - address;
            return x+1;
        }
        
    }
}
```

### Fav solution:

```class CodeWars {
  public static long overTheRoad(long address, long n) {
    return n*2+1-address;
  }
}
```

[Task link](https://www.codewars.com/kata/5f0ed36164f2bc00283aed07)

# class-23-09
#### Task 1. 
### Task 7kyu, Descending Order: 

Your task is to make a function that can take any non-negative integer as an argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.
Examples:
Input: 42145 Output: 54421
Input: 145263 Output: 654321
Input: 123456789 Output: 987654321

### My solution:
```public class DescendingOrder {
  public static int sortDesc(final int num) {
        if (num < 0) throw new IllegalArgumentException("Negative number: " + num);

        return Integer.parseInt(Integer.toString(num).codePoints()
                .sorted()
                .collect(StringBuilder::new, StringBuilder::appendCodePoint, StringBuilder::append)
                .reverse()
                .toString());
  }
}```
### Fav solution:
```import java.util.Comparator;
import java.util.stream.Collectors;

public class DescendingOrder {
  public static int sortDesc(final int num) {
    return Integer.parseInt(String.valueOf(num).chars().mapToObj(s -> String.valueOf(Character.getNumericValue(s))).sorted(Comparator.reverseOrder()).collect(Collectors.joining()));
  }
}```
[Task link]( https://www.codewars.com/kata/5467e4d82edf8bbf40000155)

 

##### Task 2. 
### Task 6kyu, Find the unique number: 

There is an array with some numbers. All numbers are equal except for one. Try to find it!
findUniq([ 1, 1, 1, 2, 1, 1 ]) === 2
findUniq([ 0, 0, 0.55, 0, 0 ]) === 0.55
It’s guaranteed that array contains at least 3 numbers.
The tests contain some very huge arrays, so think about performance.
This is the first kata in series:
Find the unique number (this kata)
Find the unique string
Find The Unique

### My solution: 
```function findUniq(arr) {
  arr = arr.sort()
  if (arr[0] === arr[1]){
    return arr[arr.length -1]
  } else {
    return arr[0]
  } 
}```

### Fav solution:

```function findUniq(arr) {
 return arr.filter(function(elem){
  return arr.indexOf(elem)===arr.lastIndexOf(elem)
 })[0] 
 
}
```

[Task link]( https://www.codewars.com/kata/585d7d5adb20cf33cb000235)


# class-23-09
#### Task 1. 
### Task 6kyu, Create Phone Number: 

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.
Example
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) // => returns "(123) 456-7890"
The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!

### My solution:
```public class Kata {
  public static String createPhoneNumber(int[] numbers) {
    String phoneNumber = new String("(xxx) xxx-xxxx");
    
    for (int i : numbers) {
      phoneNumber = phoneNumber.replaceFirst("x", Integer.toString(i));
    }
    
    return phoneNumber;
  }
}
```

### Fav solution:

```public class Kata {
  public static String createPhoneNumber(int[] numbers) {
    return String.format("(%d%d%d) %d%d%d-%d%d%d%d", java.util.stream.IntStream.of(numbers).boxed().toArray());
  }
}
```
[Task link](https://www.codewars.com/kata/525f50e3b73515a6db000b83)

 

##### Task 2. 
### Task 6kyu, Playing on a chessboard: 

With a friend we used to play the following game on a chessboard (8, rows, 8 columns). On the first row at the bottom we put numbers:
1/2, 2/3, 3/4, 4/5, 5/6, 6/7, 7/8, 8/9
On row 2 (2nd row from the bottom) we have:
1/3, 2/4, 3/5, 4/6, 5/7, 6/8, 7/9, 8/10
On row 3:
1/4, 2/5, 3/6, 4/7, 5/8, 6/9, 7/10, 8/11
until last row:
1/9, 2/10, 3/11, 4/12, 5/13, 6/14, 7/15, 8/16
When all numbers are on the chessboard each in turn we toss a coin. The one who get "head" wins and the other gives him, in dollars, the sum of the numbers on the chessboard. We play for fun, the dollars come from a monopoly game!
Task
How much can I (or my friend) win or loses for each game if the chessboard has n rows and n columns? Add all of the fractional values on an n by n sized board and give the answer as a simplified fraction.
### My solution: 
```public class Suite2 {
	
	public static String game(long n) {
    long sum = n*n;
		if (n % 2 == 0) {
			return "[" + sum/2 +"]";
		}else{
			return "[" + sum + "," + " 2]";
		}
	}
}}
```

### Fav solution:

```public class Suite2 {
	
	public static String game(long n) {
		return n % 2 == 0 ? "["+n*n/2+"]" : "["+n*n+", "+"2]";
	}
}
```

[Task link](https://www.codewars.com/kata/55ab4f980f2d576c070000f4/java)

# class-30-09
#### Task 1. 
### Task 6kyu, Salesman's Travel: 

A traveling salesman has to visit clients. He got each client's address e.g. "432 Main Long Road St. Louisville OH 43071" as a list.
The basic zipcode format usually consists of two capital letters followed by a white space and five digits. The list of clients to visit was given as a string of all addresses, each separated from the others by a comma, e.g. :
"123 Main Street St. Louisville OH 43071,432 Main Long Road St. Louisville OH 43071,786 High Street Pollocksville NY 56432".
To ease his travel he wants to group the list by zipcode.
Task
The function travel will take two parameters r (addresses' list of all clients' as a string) and zipcode and returns a string in the following format:
zipcode:street and town,street and town,.../house number,house number,...
The street numbers must be in the same order as the streets where they belong.
If a given zipcode doesn't exist in the list of clients' addresses return "zipcode:/"

### My solution:
```function travel(r, zipcode) {
    const addressList = r.split(",");

    const streets = [];
    const numbers = [];

    addressList.forEach(address => {
        let zip = address.substring(address.length - 8, address.length);
        if (zip === zipcode) {
            let number = address.substring(0, address.indexOf(" ") + 1);
            let street = address.substring(address.indexOf(" "), address.length -8);
            
            streets.push(street.trim());
            numbers.push(number.trim());
        }
    });
    return `${zipcode}:${streets.join(",")}/${numbers.join(",")}`;
}
```
### Fav solution:
```function travel(r, zipcode) {
  re = RegExp('(\\d+)\\s+(.+)\\s+'+zipcode+'$')
  streets = r.split(',').map(x=>x.match(re)).filter(x=>x)
  return zipcode+':'+streets.map(x=>x[2])+'/'+streets.map(x=>x[1])
}
```
[Task link]( https://www.codewars.com/kata/56af1a20509ce5b9b000001e)

 

##### Task 2. 
### Task 6kyu, Linked Lists - Length & Count: 
### My solution: 
```function Node(data) {
  this.data = data;
  this.next = null;
}

function length(head) {
  let length = 0;
  let current = head;
  
  while ( current != null ) {
    current = current.next
    length++;
  }
  
  return length;
}

function count(head, data) {
  let current = head;
  let count = 0;
  
  while ( current != null ) {
    if ( current.data === data )
      count++;
      
    current = current.next;
  }
  
  return count;
}
```

### Fav solution:

```class Node {
  constructor(data) {
    Object.assign(this, {data, next: null});
  }
}

const length = head =>
  head ? 1 + length(head.next) : 0;

const count = (head, data) =>
  head ? (head.data === data) + count(head.next, data) : 0;
```

[Task link]( https://www.codewars.com/kata/55beec7dd347078289000021)





# class-07-10
#### Task 1. 
### Task 6kyu, Data Reverse: 

A stream of data is received and needs to be reversed.
Each segment is 8 bits long, meaning the order of these segments needs to be reversed, for example:
11111111  00000000  00001111  10101010
 (byte1)   (byte2)   (byte3)   (byte4)
should become:
10101010  00001111  00000000  11111111
 (byte4)   (byte3)   (byte2)   (byte1)
The total number of bits will always be a multiple of 8.
The data is given in an array as such:
[1,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0,0,0,1,1,1,1,1,0,1,0,1,0,1,0]
Note: In the C and NASM languages you are given the third parameter which is the number of segment blocks.

### My solution:
```function dataReverse(data) {
  let a = [];
  while (data.length)
    a.unshift(...data.splice(0, 8));
  return a;
}
```
### Fav solution:
```const dataReverse = data =>
  [...data.join(``).match(/.{8}|$/g).reverse().join(``)].map(Number);
```
[Task link]( https://www.codewars.com/kata/569d488d61b812a0f7000015)

 

##### Task 2. 
### Task 6kyu, English beggars: 

Born a misinterpretation of this kata, your task here is pretty simple: given an array of values and an amount of beggars, you are supposed to return an array with the sum of what each beggar brings home, assuming they all take regular turns, from the first to the last.
For example: [1,2,3,4,5] for 2 beggars will return a result of [9,6], as the first one takes [1,3,5], the second collects [2,4].
The same array with 3 beggars would have in turn have produced a better out come for the second beggar: [5,7,3], as they will respectively take [1,4], [2,5] and [3].
Also note that not all beggars have to take the same amount of "offers", meaning that the length of the array is not necessarily a multiple of n; length can be even shorter, in which case the last beggars will of course take nothing (0).
Note: in case you don't get why this kata is about English beggars, then you are not familiar on how religiously queues are taken in the kingdom ;)
Note 2: do not modify the input array.

### My solution: 
```function beggars(values, n){
  var outputValues = [];
  for (var i = 0; i < n; i++) {
    var sum = 0;
    for (var j = i; j < values.length; j += n) {
      sum += values[j];
    }
    outputValues.push(sum);
  }
  return outputValues;
}
```

### Fav solution:

```const beggars = (vals, n) => vals.reduce((a, v, x) => { a[x%n] += v; return a; }, Array(n).fill(0)); 
```

[Task link]( https://www.codewars.com/kata/59590976838112bfea0000fa)






# class-14-10
#### Task 1. 
### Task 6kyu, Your order, please: 
Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.
Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).
If the input string is empty, return an empty string. The words in the input String will only contain valid consecutive numbers.
Examples
"is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
"4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
""  -->  ""

### My solution:
```public class Order {
   public static String order(String words) {
        String[] arr = words.split(" ");
        StringBuilder result = new StringBuilder("");
        for (int i = 0; i < 10; i++) {
            for (String s : arr) {
                if (s.contains(String.valueOf(i))) {
                    result.append(s + " ");
                }
            }
        }
        return result.toString().trim();
    }
}
```
### Fav solution:
```import java.util.*;
import java.util.stream.Collectors;
public class Order {
  public static String order(String words) {
    return Arrays.stream(words.split(" "))
      .sorted(Comparator.comparing(s -> s.replaceAll("\\D+", "")))
      .collect(Collectors.joining(" "));
  }
}
```
[Task link]( https://www.codewars.com/kata/55c45be3b2079eccff00010f)

 

##### Task 2. 
### Task 6kyu, Row of the odd triangle: 
Given a triangle of consecutive odd numbers:

             1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
...
find the triangle's row knowing its index (the rows are 1-indexed), e.g.:

odd_row(1)  ==  [1]
odd_row(2)  ==  [3, 5]
odd_row(3)  ==  [7, 9, 11]
Note: your code should be optimized to handle big inputs.

### My solution: 
```public class UserSolution {
  public static long[] oddRow(int n) {
    long[] arr = new long[n];
    
    for (int i = 0, j = 0; i < 2 * n; i += 2, j++)
      arr[j] = (long) n * (n - 1) + 1 + i;
    
    return arr;
  }
}
```

### Fav solution:

```import static java.util.stream.LongStream.iterate;

class UserSolution {
  static long[] oddRow(int n) {
    return iterate((long) n * (n - 1) + 1, i -> i + 2).limit(n).toArray();
  }
}
```

[Task link]( https://www.codewars.com/kata/5d5a7525207a674b71aa25b5)






# class-21-10
#### Task 1. 
### Task 6kyu, Encrypt this!: 
Acknowledgments:
I thank yvonne-liu for the idea and for the example tests :)

Description:
Encrypt this!

You want to create secret messages which can be deciphered by the Decipher this! kata. Here are the conditions:

Your message is a string containing space separated words.
You need to encrypt each word in the message using the following rules:
The first letter must be converted to its ASCII code.
The second letter must be switched with the last letter
Keepin' it simple: There are no special characters in the input.
Examples:
Kata.encryptThis("Hello") => "72olle"
Kata.encryptThis("good") => "103doo"
Kata.encryptThis("hello world") => "104olle 119drlo"

### My solution:
```public class Kata {

  public static String encryptThis(String text) {
    StringBuilder enc = new StringBuilder();
    for (String word : text.split(" ")) {
      StringBuilder sb = new StringBuilder(word);
      int lastIdx = sb.length() - 1;      
      if (lastIdx > 0) {
        char lastCh = sb.charAt(lastIdx);
        sb.setCharAt(lastIdx, sb.charAt(1));
        sb.setCharAt(1, lastCh);
      }
      enc.append(lastIdx < 0 ? "" : (byte)sb.charAt(0) + sb.substring(1)).append(" ");
    }
    return enc.toString().replaceFirst("\\s++$", ""); // trim tail only
  }
  
}
```
### Fav solution:
```import static java.util.regex.Pattern.compile;
import static java.util.stream.Collectors.joining;

public class Kata {
    public static String encryptThis(String text) {
        return compile(" ").splitAsStream(text)
                           .map(w -> w.isEmpty() ? "" : (int) w.charAt(0) + (w.length() > 2 ? w.replaceFirst(".(.)(.*)(.)", "$3$2$1") : w.substring(1)))
                           .collect(joining(" "));
    }
}
```
[Task link]( https://www.codewars.com/kata/5848565e273af816fb000449/java)

 

##### Task 2. 
### Task 6kyu, Equal Sides Of An Array: 
You are going to be given an array of integers. Your job is to take that array and find an index N where the sum of the integers to the left of N is equal to the sum of the integers to the right of N. If there is no index that would make this happen, return -1.

For example:

Let's say you are given the array {1,2,3,4,3,2,1}:
Your function will return the index 3, because at the 3rd position of the array, the sum of left side of the index ({1,2,3}) and the sum of the right side of the index ({3,2,1}) both equal 6.

Let's look at another one.
You are given the array {1,100,50,-51,1,1}:
Your function will return the index 1, because at the 1st position of the array, the sum of left side of the index ({1}) and the sum of the right side of the index ({50,-51,1,1}) both equal 1.

Last one:
You are given the array {20,10,-80,10,10,15,35}
At index 0 the left side is {}
The right side is {10,-80,10,10,15,35}
They both are equal to 0 when added. (Empty arrays are equal to 0 in this problem)
Index 0 is the place where the left side and right side are equal.

Note: Please remember that in most programming/scripting languages the index of an array starts at 0.

Input:
An integer array of length 0 < arr < 1000. The numbers in the array can be any integer positive or negative.

Output:
The lowest index N where the side to the left of N is equal to the side to the right of N. If you do not find an index that fits these rules, then you will return -1.

Note:
If you are given an array with multiple answers, return the lowest correct index.

### My solution: 
```public class Kata {
  public static int findEvenIndex(int[] arr) {
     for(int i = 0; i < arr.length; i++){
       if(leftSum(arr, i) == rightSum(arr, i))
         return i;
     }
     
     return -1;
  }
  
  public static long leftSum(int[] arr,int idx){
    long result = 0;
    
    for(int i = 0; i < idx; i++){
      result += arr[i];
    }
    
    return result;
  }
  
  public static long rightSum(int[] arr, int idx){
    long result = 0;
    
    for(int i = idx + 1; i < arr.length; i++){
      result += arr[i];
    }
    
    return result;
  }
}
```

### Fav solution:

```import java.util.Arrays;
public class Kata {
  public static int findEvenIndex(int[] arr) {
        int s1= Arrays.stream(arr).sum(), s2=0;
        for (int i=0; i<arr.length; i++){
            if (s1-arr[i] == s2)
                return i;
            s1-=arr[i];
            s2+=arr[i];
        }
        return -1;
  }
}
```

[Task link]( https://www.codewars.com/kata/5679aa472b8f57fb8c000047/java)






# class-28-10
#### Task 1. 
### Task 6kyu, Give me a Diamond: 
Jamie is a programmer, and James' girlfriend. She likes diamonds, and wants a diamond string from James. Since James doesn't know how to make this happen, he needs your help.

Task
You need to return a string that looks like a diamond shape when printed on the screen, using asterisk (*) characters. Trailing spaces should be removed, and every line must be terminated with a newline character (\n).

Return null/nil/None/... if the input is an even number or negative, as it is not possible to print a diamond of even or negative size.

Examples
A size 3 diamond:

 *
***
 *
...which would appear as a string of " *\n***\n *\n"

A size 5 diamond:

  *
 ***
*****
 ***
  *
...that is:

"  *\n ***\n*****\n ***\n  *\n"

### My solution:
```class Diamond {
  public static String print(int n) {
    if (n % 2 == 0 || n < 0) {
      return null;
    }
    StringBuilder diamond = new StringBuilder();
    for (int i = 1; i <= n; i+=2) {
      appendLine(diamond, i, n);
    }
    for (int i = n-2; i > 0; i-=2) {
      appendLine(diamond, i, n);
    }
    return diamond.toString();
	}
  
  private static void appendLine(StringBuilder diamond, int size, int totalSize) {
    int spaces = (totalSize-size)/2;
    for (int j = 0; j < spaces; j++) {
      diamond.append(" ");
    }
    for (int j = 0; j < size; j++) {
      diamond.append("*");
    }
    diamond.append("\n");
  }
}
```
### Fav solution:
```class Diamond {
public static String print(int n) {
    if (n % 2  == 0 || n <= 0) {return null;}
    StringBuffer expected = new StringBuffer();
    for (int i = 1; i <= n; i+=2) {
      expected.append(" ".repeat((n - i) / 2) + "*".repeat(i) + "\n");
    }
    for (int i = n - 2; i >= 1; i-=2) {
      expected.append(" ".repeat((n - i) / 2) + "*".repeat(i) + "\n");
    }
    return expected.toString();
  }
}
```
[Task link]( https://www.codewars.com/kata/5503013e34137eeeaa001648/java)

 

##### Task 2. 6 kyu. 
Let us consider this example (array written in general format):

ls = [0, 1, 3, 6, 10]

Its following parts:

ls = [0, 1, 3, 6, 10]
ls = [1, 3, 6, 10]
ls = [3, 6, 10]
ls = [6, 10]
ls = [10]
ls = []
The corresponding sums are (put together in a list): [20, 20, 19, 16, 10, 0]

The function parts_sums (or its variants in other languages) will take as parameter a list ls and return a list of the sums of its parts as defined above.

Other Examples:
ls = [1, 2, 3, 4, 5, 6] 
parts_sums(ls) -> [21, 20, 18, 15, 11, 6, 0]

ls = [744125, 935, 407, 454, 430, 90, 144, 6710213, 889, 810, 2579358]
parts_sums(ls) -> [10037855, 9293730, 9292795, 9292388, 9291934, 9291504, 9291414, 9291270, 2581057, 2580168, 2579358, 0]
Notes
Take a look at performance: some lists have thousands of elements.
Please ask before translating.

### My solution: 
```class SumParts {

  public static int[] sumParts(int[] ls) {
    int[] result = new int[ls.length + 1];
    int counter = 0;
    for (int idx = ls.length - 1; idx >= 0; idx--) {
      counter = counter + ls[idx];
      result[idx] = counter;
    }
    return result;
  }
}
```

### Fav solution:

```class SumParts {

  public static int[] sumParts(int[] ls) {
    int[] result = new int[ls.length+1];
    for(int i = ls.length-1; i >= 0; --i) {
      result[i] = result[i+1] + ls[i];
    }
    return result;
  }
}
```

[Task link]( https://www.codewars.com/kata/5ce399e0047a45001c853c2b/java)






# class-11-11
#### Task 1. 
### Task 6kyu, Convert string to camel cas: 
Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case). The next words should be always capitalized.

Examples
"the-stealth-warrior" gets converted to "theStealthWarrior"
"The_Stealth_Warrior" gets converted to "TheStealthWarrior"

### My solution:
```import java.lang.StringBuilder;
class Solution{

  static String toCamelCase(String s){
    StringBuffer sb = new StringBuffer();
    
    boolean flToUpperCase = false;
    for ( char ch: s.toCharArray() ) {
      if ( ch == '-' || ch == '_' )
        flToUpperCase = true;
      else {
        sb.append( ( flToUpperCase ) ? Character.toUpperCase(ch) : ch );
        flToUpperCase = false;
      }
    }
    
    return sb.toString();
  }
}```
### Fav solution:
```import java.util.Arrays;

class Solution{

  static String toCamelCase(String str){
    String[] words = str.split("[-_]");
    return Arrays.stream(words, 1, words.length)
            .map(s -> s.substring(0, 1).toUpperCase() + s.substring(1))
            .reduce(words[0], String::concat);
  }
}
```
[Task link]( hhttps://www.codewars.com/kata/517abf86da9663f1d2000003/java)

 

##### Task 2 6kyu Hidden "Cubic" numbers. 
We search non-negative integer numbers, with at most 3 digits, such as the sum of the cubes of their digits is the number itself; we will call them "cubic" numbers.

153 is such a "cubic" number : 1^3 + 5^3 + 3^3 = 153
These "cubic" numbers of at most 3 digits are easy to find, even by hand, so they are "hidden" with other numbers and characters in a string.

The task is to find, or not, the "cubic" numbers in the string and then to make the sum of these "cubic" numbers found in the string, if any, and to return a string such as:

"number1 number2 (and so on if necessary) sumOfCubicNumbers Lucky" 
if "cubic" numbers number1, number2, ... were found.

The numbers in the output are to be in the order in which they are encountered in the input string.

If no cubic numbers are found return the string: `"Unlucky"``.

Examples:
 - s = "aqdf&0#1xyz!22[153(777.777" 
   the groups of at most 3 digits are 0 and 1 (one digit), 22 (two digits), 153, 777, 777 (3 digits)
   Only 0, 1, 153 are cubic and their sum is 154
   Return: "0 1 153 154 Lucky"

- s = "QK29a45[&erui9026315"
  the groups are 29, 45, 902, 631, 5. None is cubic.
  Return: "Unlucky"
Notes
In the string "001234" where 3 digits or more follow each other the first group to examine is "001" and the following is "234". If a packet of at most three digits has been taken, whether or not "cubic", it's over for that packet.

When a continuous string of digits exceeds 3, the string is split into groups of 3 from the left. The last grouping could have 3, 2 or 1 digits.

e.g "24172410" becomes 3 strings comprising "241", "724" and "10"

e.g "0785" becomes 2 strings comprising "078" and "5".
### My solution: 
```import static java.util.Arrays.stream;
import static java.util.stream.Collectors.joining;

import java.util.Scanner;
import java.util.function.IntPredicate;
import java.util.regex.MatchResult;

class Cubes {

    public String isSumOfCubes(String input) {
        final var matches = new Scanner(input).findAll("-?(\\d{3}|\\d{2}|\\d)")
                .map(MatchResult::group)
                .mapToInt(Integer::parseInt)
                .filter(n -> n >= 0 && n < 1000)
                .filter(IS_CUBIC)
                .toArray();

        return matches.length == 0
                ? "Unlucky"
                : "%s %d Lucky".formatted(
                        stream(matches)
                                .mapToObj(String::valueOf)
                                .collect(joining(" ")),
                        stream(matches).sum());
    }

    private static final IntPredicate IS_CUBIC = i ->
            String.valueOf(i).chars()
                    .mapToObj(c -> "" + (char) c)
                    .mapToInt(Integer::valueOf)
                    .map(n -> n * n * n)
                    .sum() == i;
}
```

### Fav solution:

```import java.util.ArrayList;

class Cubes {
  static String isSumOfCubes(String s) {
    var cubes = new ArrayList<String>();
    for (String num : s.replaceAll("[^\\d]", " ").trim().split("\\s+")) {
      for (String top3 : num.split("(?<=\\G...)")) {
        if (top3.equals(top3.chars().map(n -> (int) Math.pow(n - 48., 3)).sum() + "")) {
          cubes.add(top3);
        }
      }
    }
    return cubes.isEmpty() ? "Unlucky" : String.join(" ", cubes) + " " + cubes.stream().mapToInt(Integer::parseInt).sum() + " Lucky";
  }
}
```

[Task link]( https://www.codewars.com/kata/55031bba8cba40ada90011c4/java)






# class-25-11
#### Task 1. 
### Task 6kyu, Find the odd int: 

Given an array of integers, find the one that appears an odd number of times.

There will always be only one integer that appears an odd number of times.

Examples
[7] should return 7, because it occurs 1 time (which is odd).
[0] should return 0, because it occurs 1 time (which is odd).
[1,1,2] should return 2, because it occurs 1 time (which is odd).
[0,1,0,1,0] should return 0, because it occurs 3 times (which is odd).
[1,2,2,3,3,3,4,3,3,3,2,2,1] should return 4, because it appears 1 time (which is odd).

### My solution:
```public class FindOdd {
	public static int findIt(int[] A) {
    int odd = 0;
    
    for (int i : A) {
      odd ^= i;
    }
  
  	return odd;
  }
}
```
### Fav solution:
```public class FindOdd {

    public static int findIt(int[] a) {
        int count;
        int odd = 0;
        for (int i = 0; i < a.length; i++) {
            count = 0;
            int x = a[i];
            for (int j = 0; j < a.length; j++)
            {
                if (x == a[j]) count++;
            }
            if (count % 2 == 1) odd = a[i];


        }return odd;
    }
}
```
[Task link]( https://www.codewars.com/kata/54da5a58ea159efa38000836/java)

 

##### Task 2 6kyu Multiples of 3 or 5. 
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in. Additionally, if the number is negative, return 0 (for languages that do have them).

Note: If the number is a multiple of both 3 and 5, only count it once.

Courtesy of projecteuler.net (Problem 1)

### My solution: 
```public class Solution {

  public int solution(int number) {
  	int sum=0;
    
    for (int i=0; i < number; i++){
    	if (i%3==0 || i%5==0){sum+=i;}
    }
    return sum;
  }
}
```

### Fav solution:

```import java.util.stream.IntStream;

public class Solution {
  public int solution(int number) {
    return IntStream.range(0, number)
                    .filter(n -> (n % 3 == 0) || (n % 5 == 0))
                    .sum();
  }
}
```

[Task link]( https://www.codewars.com/kata/514b92a657cdc65150000006/java)






# class-09-12
#### Task 1. 
### Task 6kyu, Counting Duplicates: 


Count the number of Duplicates
Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

Example
"abcde" -> 0 # no characters repeats more than once
"aabbcde" -> 2 # 'a' and 'b'
"aabBcde" -> 2 # 'a' occurs twice and 'b' twice (`b` and `B`)
"indivisibility" -> 1 # 'i' occurs six times
"Indivisibilities" -> 2 # 'i' occurs seven times and 's' occurs twice
"aA11" -> 2 # 'a' and '1'
"ABBA" -> 2 # 'A' and 'B' each occur twice

### My solution:
```public class CountingDuplicates {
  public static int duplicateCount(String text) {
    int ans = 0;
    text = text.toLowerCase();
    while (text.length() > 0) {
      String firstLetter = text.substring(0,1);
      text = text.substring(1);
      if (text.contains(firstLetter)) ans ++;
      text = text.replace(firstLetter, "");
    }
    return ans;
  }
}
```
### Fav solution:
```import java.util.stream.Collectors;

public class CountingDuplicates {
  public static int duplicateCount(String text) {
    return (int)text.toLowerCase().chars().boxed().collect(Collectors.groupingBy(k->k,Collectors.counting())).values().stream().filter(e->e>1).count();
  }
}
```
[Task link]( https://www.codewars.com/kata/54bf1c2cd5b56cc47f0007a1/java)

 

##### Task 2 6kyu Take a Ten Minutes Walk. 
You live in the city of Cartesia where all roads are laid out in a perfect grid. You arrived ten minutes too early to an appointment, so you decided to take the opportunity to go for a short walk. The city provides its citizens with a Walk Generating App on their phones -- everytime you press the button it sends you an array of one-letter strings representing directions to walk (eg. ['n', 's', 'w', 'e']). You always walk only a single block for each letter (direction) and you know it takes you one minute to traverse one city block, so create a function that will return true if the walk the app gives you will take you exactly ten minutes (you don't want to be early or late!) and will, of course, return you to your starting point. Return false otherwise.

Note: you will always receive a valid array containing a random assortment of direction letters ('n', 's', 'e', or 'w' only). It will never give you an empty array (that's not a walk, that's standing still!).

### My solution: 
```public class TenMinWalk {
  public static boolean isValid(char[] walk) {
    if (walk.length != 10) {
      return false;
    }
    int x = 0, y = 0;
    for (int i = 0; i < 10; i++) {
      switch (walk[i]) {
        case 'n':
          y++;
          break;
        case 'e':
          x++;
          break;
        case 's':
          y--;
          break;
        case 'w':
          x--;
          break;
      }
    }
    return x == 0 && y == 0;
  }
}
```

### Fav solution:

```public class TenMinWalk {
    public static boolean isValid(char[] walk) {
        String s = new String(walk);
        return s.chars().filter(p->p=='n').count()==s.chars().filter(p->p=='s').count()&&
                s.chars().filter(p->p=='e').count()==s.chars().filter(p->p=='w').count()&&s.chars().count()==10;
    }
}
```

[Task link]( https://www.codewars.com/kata/54da539698b8a2ad760






# class-16-12
#### Task 1. 
### Task kyu, PaginationHelper: 

For this exercise you will be strengthening your page-fu mastery. You will complete the PaginationHelper class, which is a utility class helpful for querying paging information related to an array.

The class is designed to take in an array of values and an integer indicating how many items will be allowed per each page. The types of values contained within the collection/array are not relevant.

The following are some examples of how this class is used:

PaginationHelper<Character> helper = new PaginationHelper(Arrays.asList('a', 'b', 'c', 'd', 'e', 'f'), 4);
helper.pageCount(); //should == 2
helper.itemCount(); //should == 6
helper.pageItemCount(0); //should == 4
helper.pageItemCount(1); // last page - should == 2
helper.pageItemCount(2); // should == -1 since the page is invalid

// pageIndex takes an item index and returns the page that it belongs on
helper.pageIndex(5); //should == 1 (zero based index)
helper.pageIndex(2); //should == 0
helper.pageIndex(20); //should == -1
helper.pageIndex(-10); //should == -1

### My solution:
```import java.util.List;

public class PaginationHelper<I> {

    private final List<I> collection;
    private final int itemsPerPage;

    /**
     * The constructor takes in an array of items and a integer indicating how many
     * items fit within a single page
     */
    public PaginationHelper(List<I> collection, int itemsPerPage) {
        this.collection = collection;
        this.itemsPerPage = itemsPerPage;
    }
    
    /**
     * returns the number of items within the entire collection
     */
    public int itemCount() {
        return collection.size();
    }
    
    /**
     * returns the number of pages
     */
    public int pageCount() {
        final int size = collection.size();
        int result = size / itemsPerPage;
        if (size % itemsPerPage > 0) result += 1;
        return result;
    }
    
    /**
     * returns the number of items on the current page. page_index is zero based.
     * this method should return -1 for pageIndex values that are out of range
     */
    public int pageItemCount(int pageIndex) {
        final int result = collection.size() - itemsPerPage * pageIndex;
        return result < 0 ? -1 : (result > itemsPerPage) || (result == 0) ? itemsPerPage : result;
    }
    
    /**
     * determines what page an item is on. Zero based indexes
     * this method should return -1 for itemIndex values that are out of range
     */
    public int pageIndex(int itemIndex) {
        if (itemIndex >= collection.size() || itemIndex < 0) return -1;
        return itemIndex / itemsPerPage;
    }
}
```
### Fav solution:
```import java.util.List;

public class PaginationHelper<I> {

    private final int itemsPerPage;
    private final List<I> items;

    public PaginationHelper(List<I> items, int itemsPerPage) {
        this.items = items;
        this.itemsPerPage = itemsPerPage;
    }

    public int itemCount() {
        return items.size();
    }

    public int pageCount() {
        return (int) Math.ceil(itemCount() / (float) itemsPerPage);
    }

    public int pageItemCount(int pageIndex) {
        return pageIndex < 0 || pageIndex >= pageCount() ? -1 : pageIndex < pageCount() - 1 ? itemsPerPage : itemCount() % itemsPerPage;
    }

    public int pageIndex(int itemIndex) {
        return itemIndex < 0 || itemIndex >= itemCount() ? -1 : itemIndex / itemsPerPage;
    }

}
```
[Task link]( https://www.codewars.com/kata/515bb423de843ea99400000a/java)

 

##### Task 2 5kyu Simple Pig Latin. 
Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.

Examples
pigIt('Pig latin is cool'); // igPay atinlay siay oolcay
pigIt('Hello world !');     // elloHay orldway !

### My solution: 
```public class PigLatin {
    public static String pigIt(String str) {
        String s = "";
    		for (String STR : str.split(" ")) {
    			if(!STR.matches("\\W")) {
    				s += STR.substring(1) + STR.charAt(0) + "ay";
    			}
    			else
    				s += STR;
    			s += " ";
    		}
    		return s.substring(0, s.length() - 1);
    }
}
```

### Fav solution:

```public class PigLatin {
    public static String pigIt(String str) {
        return str.replaceAll("(\\w)(\\w*)", "$2$1ay");
    }
}
```

[Task link]( https://www.codewars.com/kata/520b9d2ad5c005041100000f/java)





