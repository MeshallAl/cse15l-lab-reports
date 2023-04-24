CSE 15L Lab Report 2
---
## Part 1:
**Code**

```
import java.io.IOException;

import java.net.URI;

class Handler implements URLHandler {
    String result = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(result);
        } 
        else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                result += parameters[1] + "\n";
                return(String.format(result));
            }
            else{
            return "404 Not Found!";
            }
        }
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

This is the code for StringServer. It is mainly derived from the example code from lab 2. Alongside this code there is the `Server.java` file which contains
all the required code to intiate the webpage.

### Example 1;
![image](https://user-images.githubusercontent.com/130005669/233852567-b9d8dbfc-d502-4f73-8210-95d8ef0e2c83.png)

In this example, I have run the code twice to add and showcase the multiple lines of output. The first thing to happen is the intialization of the server. 
Upon compiling the file with a port number as an argument, the StringServer file starts a server with the given port as `args[0]` number via the other file's `server` class 
methods effectivily intializing and creating an URI. I then load the page again with `/add-message/?s=Welcome to the String Server`. This calls upon the `handleRequest` 
class. The method first checks for the correct path arguements, in this case "`/add-message`". Since it is present, the method finds the query part (after `?`) and splits
it by the `=` symbol assigning it to the `parameters` variable. The second element of `parameters` is then added to the string variable `result`. In this case it was 
"Welcome to String Server". Then the new line symbol (`\n`) is added and returned. Then through `ServerHttpHandler` and the `handle` method the content of result is printed
on to the webpage. I then reload the page with  `/add-message/?s=Each time it adds a new line of text`. This calls the same methods and consequently adds 
"Each time it adds a new line of text" to the `result` varaible with another `\n` at the end resulting into the text the appears on the webpage above.

### Example 2;
![image](https://user-images.githubusercontent.com/130005669/233874086-18c94e91-a6e7-4d2a-99bc-bcf1c10aee1c.png)

Very similar to the last example, I have run the code four times. The first thing to happen is the intialization of the server. Upon compiling the file with a port number
as an argument, the StringServer file starts a server with the given port as `args[0]` number via the other file's `server` class 
methods effectivily intializing and creating an URI. I then load the page again with `/add-message/?s=Double`. This calls upon the `handleRequest` 
class. The method first checks for the correct path arguements, in this case "`/add-message`". Since it is present, the method finds the query part (after `?`) and splits
it by the `=` symbol assigning it to the `parameters` variable. The second element of `parameters` is then added to the string variable `result`. In this case it was 
"Double". Then the new line symbol (`\n`) is added and returned. Then through `ServerHttpHandler` and the `handle` method the content of result is printed
on to the webpage. I then reload the page with  `/add-message/?s=%20`. This calls the same methods but due to the HTML URL encode, `%20` appears as a blank space. This is
then added to `result` varaible with another `\n` at the end resulting into an empty line. I call the same line again creating another blank line. Then I reload the page
with `/add-message/?s=Space` which adds "Space"  and `\n` to result and finally results in the image above.

## Part 2:

The buggy method that I will use for this part is the `reversedInPlace` method which is supposed to take an array and reverse it without creating or using another array.

The original buggy code;

```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

A test that tests a input that causes a failure;

```
@Test
  public void testReversedInPlaceFail(){
    int[] input1 = {1,2,3};
    int[] input2 = {3,2,1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals( input2, input1);
  }

```

A test that tests an input that does not cause a failure;

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = {1,1,1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1,1,1}, input1);
	}
  
```

Result of running these tests;

![image](https://user-images.githubusercontent.com/130005669/233877136-b8b2980d-3337-4aed-8897-922b348bbf03.png)

Fixing the bug; 

(Buggy original)
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {  
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

Fixed code;

```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
      int temp = arr[i]; 
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

The bug was consisted of two parts. The first is the within the for-loop's declaration. In the code it was iterating through every element whilst switching the element with 
the one in its reversed position. If the code would have worked, it would effectivly reassign every element back to its place. As a result, I changed the for loop to only
iterate through half the elements. The second issue is code assigns the element's value to the value of its revered position's value. While intially correctly placing the 
value, it loses the value of the element. As a result, I created a temporary variable to hold that value and then assign the reversed position's  element that value.

## Part 3:

I have learnt a lot from both of the labs. In lab 2, I learnt the basics of using GitHub desktop. I now know the process of "forking" and "cloning" a repository as well 
as updating files through the "commit" and "push". I additionally learned the basics of creating a webpage and the different parts of URLs. In lab 3, I learnt how to use 
and run JUnit through VScode and certain terminolgy regarding debugging code. 
