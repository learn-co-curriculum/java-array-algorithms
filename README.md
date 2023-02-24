# Array Algorithms

## Learning Goals

- Discuss linear search algorithms using arrays.
- Analyze solving different problems using arrays.

## Elemental Search

We now know that arrays can store multiple values, such as people's names and
various numbers. But what can we do with them?

Consider we have a classroom of students, and the students' names are being
stored in array like so:

```java
public class StudentExample {
    public static void main(String[] args) {
        String[] students = {"Mike", "Maxine", "Elle", "Lucas", "Dustin", "Will"};
    }
}
```

Say the teacher is taking attendance and wants to see if "Dustin" is in the
class. How can we search the array?

Let's use a `for` loop to perform a linear search. A **linear search algorithm**
is a simple algorithm that means we will look at each element in the array until
the target element is found.

Consider the pseudocode for a linear search algorithm looking for a student:

```text
Goal: Find the student in an array with the name "Dustin".

for each student in the student array
    compare the name to see if it matches the name "Dustin".
    if the student's name is "Dustin"
        return true to indicate the student was found.

If we iterate through the entire array and no student has the name "Dustin"
    return false.        
```

Consider the following code that implements the pseudocode above:

```java
public class StudentExample {

    /**
     * Determine if the String element is in the array.
     * @param studentNames : String[] - array of student names to search.
     * @param name : String - the name of the student we want to find in the array
     * @return boolean - represents if the student's name was found in the array
     */
    public static boolean findStudent(String[] studentNames, String name) {
        for (String studentName : studentNames) {
            // If the student's name was found, return true
            if (studentName.equals(name)) {
                return true;
            }
        }
        
        // The student was not found, and we have exited the loop
        return false;
    }
    
    public static void main(String[] args) {
        String[] students = {"Mike", "Maxine", "Elle", "Lucas", "Dustin", "Will"};
        
        boolean isPresent = findStudent(students, "Dustin");
        System.out.println("Is Dustin in class? Answer: " + isPresent);
    }
}
```

Notice we have created the method `findStudent()` that will perform the linear
search throughout the array, `studentNames`. This means, we will go through each
`String` in the `studentNames` array looking for `name`.

We may also notice that the `if` statement compares the `studentName` to `name`
with the method `equals()` instead of the `==`. When comparing `String` values,
we need to use a method called `equals()` to properly compare the two values. In
a later lesson, we will learn why that is the case.

Let's run this program in the browser-based visualizer. Follow along below or
at the link
[here](https://pythontutor.com/visualize.html#code=public%20class%20StudentExample%20%7B%0A%0A%20%20%20%20/**%0A%20%20%20%20%20*%20Determine%20if%20the%20String%20element%20is%20in%20the%20array.%0A%20%20%20%20%20*%20%40param%20studentNames%20%3A%20String%5B%5D%20-%20array%20of%20student%20names%20to%20search.%0A%20%20%20%20%20*%20%40param%20name%20%3A%20String%20-%20the%20name%20of%20the%20student%20we%20want%20to%20find%20in%20the%20array%0A%20%20%20%20%20*%20%40return%20boolean%20-%20represents%20if%20the%20student's%20name%20was%20found%20in%20the%20array%0A%20%20%20%20%20*/%0A%20%20%20%20public%20static%20boolean%20findStudent%28String%5B%5D%20studentNames,%20String%20name%29%20%7B%0A%20%20%20%20%20%20%20%20for%20%28String%20studentName%20%3A%20studentNames%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20//%20If%20the%20student's%20name%20was%20found,%20return%20true%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20%28studentName.equals%28name%29%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20//%20The%20student%20was%20not%20found,%20and%20we%20have%20exited%20the%20loop%0A%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20String%5B%5D%20students%20%3D%20%7B%22Mike%22,%20%22Maxine%22,%20%22Elle%22,%20%22Lucas%22,%20%22Dustin%22,%20%22Will%22%7D%3B%0A%0A%20%20%20%20%20%20%20%20boolean%20isPresent%20%3D%20findStudent%28students,%20%22Dustin%22%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Is%20Dustin%20in%20class%3F%20Answer%3A%20%22%20%2B%20isPresent%29%3B%0A%20%20%20%20%7D%0A%7D&cumulative=false&curInstr=3&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false).

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=public%20class%20StudentExample%20%7B%0A%0A%20%20%20%20/**%0A%20%20%20%20%20*%20Determine%20if%20the%20String%20element%20is%20in%20the%20array.%0A%20%20%20%20%20*%20%40param%20studentNames%20%3A%20String%5B%5D%20-%20array%20of%20student%20names%20to%20search.%0A%20%20%20%20%20*%20%40param%20name%20%3A%20String%20-%20the%20name%20of%20the%20student%20we%20want%20to%20find%20in%20the%20array%0A%20%20%20%20%20*%20%40return%20boolean%20-%20represents%20if%20the%20student's%20name%20was%20found%20in%20the%20array%0A%20%20%20%20%20*/%0A%20%20%20%20public%20static%20boolean%20findStudent%28String%5B%5D%20studentNames,%20String%20name%29%20%7B%0A%20%20%20%20%20%20%20%20for%20%28String%20studentName%20%3A%20studentNames%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20//%20If%20the%20student's%20name%20was%20found,%20return%20true%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20%28studentName.equals%28name%29%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20//%20The%20student%20was%20not%20found,%20and%20we%20have%20exited%20the%20loop%0A%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20String%5B%5D%20students%20%3D%20%7B%22Mike%22,%20%22Maxine%22,%20%22Elle%22,%20%22Lucas%22,%20%22Dustin%22,%20%22Will%22%7D%3B%0A%0A%20%20%20%20%20%20%20%20boolean%20isPresent%20%3D%20findStudent%28students,%20%22Dustin%22%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Is%20Dustin%20in%20class%3F%20Answer%3A%20%22%20%2B%20isPresent%29%3B%0A%20%20%20%20%7D%0A%7D&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=3&heapPrimitives=nevernest&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

![findStudent-method](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-find-student-loop.png)

We can see that the `name` of interest here is "Dustin". We'll iterate through
this array to see a `String` with a value of "Dustin" exists. If we click
"Next >" twice, we'll see that the `studentName` is now assigned to the value
"Mike".

![compare-mike-and-dustin](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-mike-dustin-iteration.png)

Now we know that "Mike" does not equal "Dustin", so the conditional in the `if`
statement should be `false` and we'll move onto the next element in the array.
If we click "Next >" twice, we'll see that `studentName` is now assigned to the
value "Maxine".

![compare-max-and-dustin](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-max-dustin-iteration.png)

Just like before, we'll see that "Mike" does not equal "Dustin", so we'll skip
over the conditional again since it is `false`. Continue stepping through the
array. We'll see that it will set `studentName` to the values "Elle" and "Lucas"
next. But those values do not equal "Dustin".

When we get to step 14 (see the step number at the bottom of the code), we'll
finally see that `studentName` is now assigned to "Dustin":

![compare-dustin-and-dustin](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-dustin-dustin-iteration.png)

This time when we get to the `if` statement, we should enter in the `if` block
since "Dustin" does equal the value of the `name` variable!

![found-dustin](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-found-dustin.png)

The `findStudent()` method will then return the value `true`. Notice when it
does this, we don't ever assign `studentName` to the value of "Will". This is
because once we find the value we are looking for, the `return` statement will
take us out of the method - kind of like the `break` statement in a `switch`.

If we continue stepping through the program, it will eventually print:

```text
Is Dustin in class? Answer: true
```

This is an example of performing a linear search in an array.

<details>
    <summary>Using the code above, what would the method <code>findStudent(students, "Mike")</code> return?</summary>

  <p>Answer: <br>
     <p><code>true</code></p>
  </p>

  <p><code>students[0]</code> is initialized to the value "Mike".</p>
  <img src="https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-mike-mike-iteration.png">

</details>

<details>
    <summary>Using the code above, what would the method <code>findStudent(students, "Will")</code> return?</summary>

  <p>Answer: <br>
     <p><code>true</code></p>
  </p>

  <p><code>students[5]</code> is initialized to the value "Will".</p>
  <img src="https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-will-will-iteration.png">

</details>
<details>
    <summary>Using the code above, what would the method <code>findStudent(students, "Suzie")</code> return?</summary>

  <p>Answer: <br>
     <p><code>false</code></p>
  </p>

  <p>There is no <code>String</code> with a value of "Suzie" in the array.</p>
  <img src="https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/visualizer-suzie-not-found.png">

</details>

### Common Mistake

Elemental search is a common problem in programming. The number one mistake
students make when searching an array is the following:

```java
    public static boolean findStudent(String[] studentNames, String name) {
        for (String studentName : studentNames) {
            // If the student's name was found, return true
            if (studentName.equals(name)) {
                return true;
            } else {
                return false;
            }
        }
        
        return false;
    }
```

If we compare the code above that we stepped through with the code here, notice
we have another `return false` statement _inside_ the loop. This is incorrect as
it will only compare the first element of the array. We want to make sure we are
looking at every element of the array until the element in question is found.
See the
[visualizer](https://pythontutor.com/visualize.html#code=public%20class%20StudentExample%20%7B%0A%0A%20%20%20%20/**%0A%20%20%20%20%20*%20Determine%20if%20the%20String%20element%20is%20in%20the%20array.%0A%20%20%20%20%20*%20%40param%20studentNames%20%3A%20String%5B%5D%20-%20array%20of%20student%20names%20to%20search.%0A%20%20%20%20%20*%20%40param%20name%20%3A%20String%20-%20the%20name%20of%20the%20student%20we%20want%20to%20find%20in%20the%20array%0A%20%20%20%20%20*%20%40return%20boolean%20-%20represents%20if%20the%20student's%20name%20was%20found%20in%20the%20array%0A%20%20%20%20%20*/%0A%20%20%20%20public%20static%20boolean%20findStudent%28String%5B%5D%20studentNames,%20String%20name%29%20%7B%0A%20%20%20%20%20%20%20%20for%20%28String%20studentName%20%3A%20studentNames%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20//%20If%20the%20student's%20name%20was%20found,%20return%20true%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20%28studentName.equals%28name%29%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20//%20The%20student%20was%20not%20found,%20and%20we%20have%20exited%20the%20loop%0A%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20String%5B%5D%20students%20%3D%20%7B%22Mike%22,%20%22Maxine%22,%20%22Elle%22,%20%22Lucas%22,%20%22Dustin%22,%20%22Will%22%7D%3B%0A%0A%20%20%20%20%20%20%20%20boolean%20isPresent%20%3D%20findStudent%28students,%20%22Dustin%22%29%3B%0A%20%20%20%20%20%20%20%20System.out.println%28%22Is%20Dustin%20in%20class%3F%20Answer%3A%20%22%20%2B%20isPresent%29%3B%0A%20%20%20%20%7D%0A%7D&cumulative=false&curInstr=4&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false)
to step through this case of trying to search the array of student names for
"Dustin" again.

## More Searching

Let's consider another use case of working with arrays!

Let's write a program to take in decimal numbers from a user and then find the
minimum value.

We can start writing the program by prompting the user to enter in numerical
values to initialize an array.

```java
    public static void main(String[] args) {
        
        // Create an array of 3 integers
        double [] numbers = new double[3];

        // Prompt the user 3 times to provide an integer
        for (int index = 0; index < numbers.length; index++) {
            Scanner scanner = new Scanner(System.in);
            System.out.println("Enter a number:");
            double number = scanner.nextDouble();

            // Store the number given by the user in the array
            numbers[index] = number;
        }
    }
```

Note: In the example above, we did not consider a user entering invalid input
to simplify this example for demonstration purposes.

We'll use a `for` loop to prompt the user 3 times for input since the array
`numbers` is set to a fixed size of 3. We may also see that we are using a
classic `for` loop this time. This is because we want to know the index to
initialize the element in the array.

Once we have the array, we can create to find the minimum value:

```java
    public static double findMinimum(double[] numbers) {
        
    }
```

We'll have the method take in an array of `double` data types and return a
`double` with the minimum value.

Consider the following implementation for the `findMinimum()` method:

```java
    public static double findMinimum(double[] numbers) {
        double min = 0.0;
        
        // Iterate through the array of numbers
        for (double number : numbers) {
            
            // Check to see if the number in the array is less than the current min value
            if (number < min) {
                // If it is, re-assign the min to the smaller value
                min = number;
            }
        }

        return min;
    }
```

Let's breakdown the following code:

- We'll start off by initializing a `min` variable. The `min` variable will hold
  the value of the minimum value of the array.
- Iterate through the array by using a `for` loop:
  - Within the loop, check each value in the `numbers` array to see if it is
    less than the current `min` value.
    - If it is, re-assign the `min` value to the element in the array that is
      smaller.
- Once out of the loop, we have checked each value in the array. We can return
  the `min` value.

Let's call the `findMinimum()` method now in the `main()` method to complete the
program:

```java
public class ArrayExample {

    public static double findMinimum(double[] numbers) {
        double min = 0.0;

        // Iterate through the array of numbers
        for (double number : numbers) {

            // Check to see if the number in the array is less than the current min value
            if (number < min) {
                // If it is, re-assign the min to the smaller value
                min = number;
            }
        }

        return min;
    }

    public static void main(String[] args) {

        // Create an array of 3 integers
        double [] numbers = new double[3];

        // Prompt the user 3 times to provide an integer
        for (int index = 0; index < numbers.length; index++) {
            Scanner scanner = new Scanner(System.in);
            System.out.println("Enter a number:");
            double number = scanner.nextDouble();

            // Store the number given by the user in the array
            numbers[index] = number;
        }

        System.out.println("The minimum value is " + findMinimum(numbers));
    }
}
```

If we run this program with the user inputs 8.75, -3.1, and 2, we'll get the
following output:

```text
Enter a number:
8.75
Enter a number:
-3.1
Enter a number:
2
The minimum value is -3.1
```

Everything seems to work great! Let's write some unit tests to test the
`findMinimum()` method.

```java
class ArrayExampleTest {

    @Test
    void findMinimum() {
        double [] numbers = { 8.75, -3.1, 2 };
        assertEquals(-3.1, ArrayExample.findMinimum(numbers));
    }
}
```

Remember, to call the `findMinimum()` method from another class, we need to use
the syntax `ArrayExample.findMinimum(numbers)`.

Since we have already tested and ensure the case above worked, we can use that
array and assert that minimum value is indeed -3.1. If we run the unit test, it
should pass.

Let's add another test case with different values:

```java
    
    // Rename original test
    @Test
    void findMinimumTest1() {
        double [] numbers = { 8.75, -3.1, 2 };
        assertEquals(-3.1, ArrayExample.findMinimum(numbers));
    }

    // Create second unit test case
    @Test
    void findMinimumTest2() {
        double [] numbers = { 3, 2.5, 1 };
        assertEquals(1.0, ArrayExample.findMinimum(numbers));
    }
```

If we run both these unit tests, notice that the `findMinimumTest2()` fails:

```text
org.opentest4j.AssertionFailedError: 
Expected :1.0
Actual   :0.0
```

Based on the error, it looks like the `findMinimum()` method actually returned
a value of 0.0 instead of 1.0.

Let's run the debugger on the `findMinimumTest2()` and set a breakpoint at
`assertEquals(1.0, ArrayExample.findMinimum(numbers));`

![hit-breakpoint](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/intellij-debugger-hit-breakpoint-16.png)

If we click the "step-into" action and choose to step-into the `findMinimum()`
method, we'll start executing the `findMinimum()` method in the `ArrayExample`
class:

![step-into-findMinimum-method](https://curriculum-content.s3.amazonaws.com/java-mod-1/array-algorithms/intellij-debugger-step-into-find-minimum.png)

We'll see that we set the `min` value to 0.0. If we continue stepping through
the program, we'll notice we are comparing `min` with the elements in the array
to find the minimum value.

But there's something wrong with this logic.

0.0 is not a value in the array `numbers`! We cannot initialize `min` to 0.0
when trying to find a minimum value within an array.

So how do we fix it?

We need to compare the elements in the array with each other to find the minimum
value. Let's set `min` to the first element in the array instead:

```java
    public static double findMinimum(double[] numbers) {
        // Set the minimum value to the first number in the array
        double min = numbers[0];

        // Iterate through the array of numbers
        for (double number : numbers) {

            // Check to see if the number in the array is less than the current min value
            if (number < min) {
                // If it is, re-assign the min to the smaller value
                min = number;
            }
        }

        return min;
    }
```

Now if we run our unit tests, they both should pass! This is another common bug
found when performing a search.

## Conclusion

As we can see, there are quite a few problems we can solve using arrays!

A **linear search algorithm** is a simple algorithm that means we will look at
each element in the array until the target element is found. This type of
algorithm can help us find an element in an array, find the minimum/maximum
value in an array, and more!

Let's see some more of these problems in practice!
