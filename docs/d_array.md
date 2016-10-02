# Arrays

##  Introduction

An array is an aggregate data structure that is designed to store a group of objects of the same or different types. Arrays can hold primitives as well as references. The array is the most efficient data structure for storing and accessing a sequence of objects.

Here is the list of most important array features you must know (i.e. be able to program)

* copying and cloning
* insertion and deletion
* searching and sorting

You already know that the Java language has only two data types, primitives and references. Which one is an array? Is it primitive? An array is not a primitive data type - it has a field (and only one), called length. Formally speaking, an array is a reference type, though you cannot find such a class in the Java APIs. Therefore, you deal with arrays as you deal with references. One of the major diffeences between refeences and primituives is that you cannot copy arrays by assigning one to another:

```java
int[] a = {9, 5, 4};
int[] b = a;
```

The assignment operator creates an alias to the object, like in the picture below

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/alias.jpg)

Since these two references a and b refer to the same object, comparing them with the double equal sign "==" will always return true. In the next code example,

```java
int [] a = {1,2,3};
int [] b = {1,2,3};
```

a and b refer to two different objects (though with identical contents). Comparing them with the double equal sign will return false. How would you compare two objects with identical contents? In short, using the equals method. For array comparison, the Java APIs provides the Arrays class.

## The Arrays class

The java.util.Arrays class is a convenience class for various array manipulations, like comparison, searching, printing, sorting and others. Basically, this class is a set of static methods that are all useful for working with arrays. The code below demonstrates a proper invocation of equals:

```java
int[] a = {1,2,3};
int[] b = {1,2,3};
if( Arrays.equals(a, b) )
   System.out.println("arrays with identical contents");
```

Another commonly used method is toString() which takes care of of printing

```java
int[] a = {1,2,3};
System.out.println(Arrays.toString(a));
```

Here is the example of sorting

```java
int[] a = {3,2,1};
Arrays.sort(a);
System.out.println(Arrays.toString(a));
```

In addition to that, the class has other utility methods for supporting operations over multidimensional arrays.

## Copying arrays

There are four ways to copy arrays

using a loop structure
using Arrays.copyOf()
using System.arraycopy()
using clone()
The first way is very well known to you

```java
int[] a = {1, 2, 3};
int[] b = new int[a.length];
for(int i= 0; i < a.length; i++) b[i] = a[i];
```

The next choice is to use Arrays.copyOf()

```java
int[] a = {1, 2, 3};
int[] b = Arrays.copyOf(a, a.length);
```

The second parameter specifies the length of the new array, which could either less or equal or bigger than the original length.

The most efficient copying data between arrays is provided by System.arraycopy() method. The method requires five arguments. Here is its signature

```java
public static void arraycopy(Object source,
                             int srcIndex,
                             Object destination,
                             int destIndex,
                             int length)
```
                         
The method copies length elements from a source array starting with the index srcIndex to a new array destination at the index destIndex.The above code example can be rewritten as it follows

```java
int[] a = {1, 2, 3};
int[] b = new int[a.length];
System.arraycopy(a, 0, b, 0, 3)
```

And the last copying choice is the use of cloning. Cloning involves creating a new array of the same size and type and copying all the old elements into the new array. The clone() method is defined in the Object class and its invocation is demonstrated by this code segment

```java
int[] a = {1, 2, 3};
int[] b = (int[]) a.clone();
```

Note, that casting (int[]) is the must.

Examine the code in ArrayCopyPrimitives.java for further details.

## Challenges

* [Arrays: Left Rotation](https://www.hackerrank.com/challenges/ctci-array-left-rotation)

## References

1. [Array Data Structure](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/arrays.html)
