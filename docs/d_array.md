## Arrays

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

### The Arrays class

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

## Insertion and Deletion

Arrays in Java have no methods and only one `immutable` field `length`. Once an array is created, its length is fixed and cannot be changed. What do you do to resize the array? You allocate the array with a different size and copy the contents of the old array to the new array. This code example demonstrates deletion from an array of primitives

```java
public char[] delete(char[] data, int pos)
{
	if(pos >= 0 && pos < data.length)
	{
		char[] tmp = new char[data.length-1];
		System.arraycopy(data, 0, tmp, 0, pos);
		System.arraycopy(data, pos+1, tmp, pos, data.length-pos-1);
		return tmp;
	}
	else
		return data;
}
```

The first arraycopy copies the elements from index 0 to index pos-1, the second arraycopy copies the elements from index pos+1 to data.length.

Examine the code in ArrayDemo.java for further details.

## The ArrayList class

The java.util.ArrayList class supports an idea of a dynamic array - an array that grows and shrinks on demand to accomodate the number of elements in the array. Below is a list of commonly used methods

* `add(object)` - adds to the end
* `add(index, object)` - inserts at the index
* `set(index, object)` - replaces at the index
* `get(index)` - returns the element at that index
* `remove(index)` - deletes the element at that index
* `size()` - returns the number of elements

The following code example will give you a heads up into how some of them are used.

```
/* ADD */
      ArrayList<Integer> num = new ArrayList<Integer>();
      for(int i = 0; i < 10; i++) num.add(i);
      System.out.println(num);


/* REMOVE even integers */
      for(int i = 0; i < num.size(); i++)
      	if(num.get(i)%2 == 0) num.remove(i);
      System.out.println(num);
```

## Copying arrays of objects

This topic is more complex for understanding.. Let us start with a simple loop structure

```
Object[] obj1 = {new Integer(10),
                new StringBuffer("foobar"),
                new Double(12.95)};
Object[] obj2 = new Object[obj1.length];
for(int i = 0; i ‹ obj1.length; i++)
	obj2[i] = obj1[i];
```

At the first glance we might think that all data is copied. In reality, the internal data is shared between two arrays. The figure below illustrates the inner structure

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/copy1.bmp)

The assignment operator `obj2[i] = obj1[i]` is a crucial part of understanding the concept. You cannot copy references by assigning one to another. The assignment creates an alias rather than a copy. Let us trace down changes in the above picture after execution the following statements

```
obj1[0] = new Integer(5);
```

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/copy2.bmp)

and `((StringBuffer) obj1[1]).append('s');`

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/copy3.bmp)

As you see, `obj1[0]` and `obj2[0]` now refer to different objects. However, `obj1[1]` and `obj2[1]` refer to the same object (which is "foobars"). Since both arrays shares the data, you must be quite careful when you modify your data, because it might lead to unexpected effects.

The same behavior will take place again, if we use Arrays.copuyOf(), System.arraycopy() and clone(). Examine the code example ArrayCopyReferences.java for further details.

## Multi-dimensional arrays
In many practical application there is a need to use two- or multi-dimensional arrays. A two-dimensional array can be thought of as a table of rows and columns. This creates a table of 2 rows and 4 columns:

```
int[][] ar1 = new int[2][4];
```

You can create and initialize an array by using nested curcly braces. For example, this creates a table of 3 rows and 2 columns:

```
int[][] ar2 = {{1,2},{3,4},{5,6}};
```

Generally speaking, a two-dimensional array is not exactly a table - each row in such array can have a different length. Consider this code fragment

```
Object[][] obj = {{new Integer(1),new Integer(2)},
                  {new Integer(10), "bozo", new Double(1.95)}};
```

The accompanying picture sheds a bit of light on internal representation

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/2d.bmp)

From the picture you clearly see that a two-dimensional array in Java is an array of arrays. The array obj has two elements obj[0] and obj[1] that are arrays of length 2 and 3 respectively.

### Cloning 2D arrays

The procedure is even more confusing and less expected. Consider the following code segment

```
Object[][] obj = {{new Integer(1),new Integer(2)},
                  {new Integer(10), "bozo", new Double(1.95)}};

Object[][] twin = (Object[][]) obj.clone();
```

The procedure of clonig 2d arrays is virtually the same as cloning an array of references. Unfortunately, built-in clone() method does not actualy clone each row, but rather creates references to them Here is a graphical interpretation of the above code

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/clone4.bmp)

Let us change the value of `obj[1][1]`

```
obj[1][1] = "xyz";
```

This assignment effects the value of `twin[1][1]` as well

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/clone4a.bmp)

Such a copy is called a "shallow" copy. The default behavior of clone() is to return a shallow copy of the object. If we want a "deep" copy instead, we must provide our own implementation by overriding Object's clone() method.

The idea of a "deep" copy is simple - it makes a distinct copy of each of the object's fields, recursing through the entire object. A deep copy is thus a completely separate object from the original; changes to it don't affect the original, and vise versa. In relevance to the above code, here is a deep clone graphically

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/clone6.bmp)

Further, making a complete deep copy is not always needed. Consider an array of immutable objects. As we know, immutable objects cannot be modified, allowing clients to share the same instance without interfering with each other. In this case there is no need to clone them, which leads to the following picture

![](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/pix/clone5.bmp)

Always in this course we will create data structures of immutable objets, therefore implementing the clone method will require copying a structure (a shape) and sharing its internal data. We will discuss these issues later on in the course.

## Challenges

* [Arrays: Left Rotation](https://www.hackerrank.com/challenges/ctci-array-left-rotation)

## References

* ["Array Data Structure". *Victor S.Adamchik, CMU*. 2009](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Arrays/arrays.html)
