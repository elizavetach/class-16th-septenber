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
### Task 8kyu: 
You will be given an array a and a value x. All you need to do is check whether the provided array contains the value.
Array can contain numbers or strings. X can be either.
Return true if the array contains the value, false if not.
### My solution: 
```
public class Solution {

    public static boolean check(Object[] a, Object x) {
        for (int i = 0; i < a.length; i++)
            if (a[i] == x)
                return true;
        return false;
    }

}```
### Fav solution:
```Java
import java.util.Arrays;
class Solution
{
    static boolean check(Object[] a, Object x)
    {
        return Arrays.asList(a).contains(x);
    }
}```
[Task link](https://www.codewars.com/kata/57cc975ed542d3148f00015b/java)
