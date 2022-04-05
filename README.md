# AwesomeDart
 All Dart Resources

# dart-cheat-sheet
A curated list of awesome stuff needed to get started with your flutter development journey

[![Book] (https://www.programming-books.io/essential/dart/getting-started-with-dart-ae9c97e065fb42c4985598d4d57f9b0b)]

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome) ![Branch master](https://img.shields.io/badge/branch-master-brightgreen.svg?style=flat-square)[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/temidtech/dart-cheat-sheet/master/LICENSE)

 ## Table of Contents

- [String interpolation](#string-interpolation)
- [Functions](#functions)
- [Parsing](#parsing)
- [List Arrays](#list-arrays)
- [Lambda Functions](#lambda-functions)
- [Null-aware Operators](#null-aware-operators)
- [Conditional Property Access](#conditional-property-access)
- [Collections Literals](#collections-literals)
- [Arrow Syntax](#arrow-syntax)
- [Iterations](#iterations)
- [Map](#map)
- [Variables](#variables)
- [Class](#class)
- [Getters and Setters](#getters-and-setters)
- [Futures: Async and Await](#future-async-await)
- [JSON and serialization](#json-and-serialization)
- [Reading and decoding a file](#Reading-and-decoding-a-file)



## String interpolation

Every language has it's own way of interpolating two ore more words or characters. In dart, you can put value of an expression inside a string as follows:

###  Example

 ```dart
    int x=6;
    int y=2;
    String sum = '${x+y}';          // result is 8
    String subtraction = '${x-y}';  // result is 4
    String upperCase = '${"hello".toUpperCase()}'; // result is HELLO
    String concatXY = '$x$y'; // result is '62'
 ```

 ## Functions
Dart lang is an OOL(Object-oriented language), In this language, functions are objects and have a type, Function. This implies that functions can be assigned to 
variables or passed as args to other functions. Interestingly, you can also call an instance of a class as if it were a fuction. That's awesome, right?

###  Example

 ```dart
    String fullName(){
        String firstName = "Temidayo";
        String lastName = "Adefioye";
        return '$firstName $lastName'; // returns 'Temidayo Adefioye'
    }
 ```

 ```dart
    int length(String text){
        return text.length; // returns length of text
    }
 ```

 The above function can be rewritten in a more concise way:

  ```dart
    int length(String text) => return text.length; // returns length of text
 ```

 The above approach is applicable where functions contain just ONE expression. This is also referred to as shorthand syntax.

 ## Parsing

Parsing a string to a number such as integer and double is very key. As a developer, often times I need to convert(parse) a string value
coming from a server-side to a number, tryParse method comes in handy. Take a look at this code snippet:

###  Example

 ```dart
    var a = "121";
    var b = "120.56";
    var c = "100.a12";         
    var d = "abc";
    String parseA = int.tryParse(a); // result is 121
    String parseB = double.tryParse(b); // result is 120.56
    String parseC = double.tryParse(c); // result is null (that string contains invalid number)
    String parseD = double.tryParse(d); // result is null (that string contains invalid number)
 ```

  ## List Arrays

Perhaps the most common collection in nearly every programming language is the array or ordered set of objects. Please note that Dart arrays are Lists.

###  Example

 ```dart
    var numList = [1,2,3,5,6,7];
    var countryList = ["Nigeria","United States","United Kingdom","Ghana","IreLand","Germany"];
    String numLength = numList.length; // result is 6
    String countryLength = countryList.length; // result is 6
    String countryIndex = countryList[1]; // result is 'United States'
    String numIndex = numList[0]; // result is 1

    countryList.add("Poland"); // Adds a new item to the list.

    var emailList = new List(3); // Set a fixed list size 
    var emailList = new List<String>(); // instance of a list of type String

 ```

 ## Lambda Functions

Lambda functions provide you with a short and concise way of representing small functions. They are also referred to as Arrow functions. In dart, if you need to write quick throw away functions without necessarily naming them, lambda fucntion is all you need. With the power of this function you can do the following and more:

###  Example

 ```dart
    var numList = new List<int>.generate(5,(i) => i);
    print(numList); //result: {0,1,2,3,4}
    var loans = numList.map( (n) => "\#$n").toList();
    print(loans); // result: {#0, #1, #3, #4}

    printMsg()=> print("Hello world");

    // You can declare a state function this way in flutter
     _DashboardState createState() => _DashboardState(); 

    // How about creating a widget using lambda?
    Card makeCard(Asset assetViewModel) => Card(
          elevation: 8.0,
          margin: new EdgeInsets.symmetric(horizontal: 10.0, vertical: 6.0),
          child: Container(
            decoration: BoxDecoration(color: Colors.white),
            child: makeListTile(assetViewModel), // where makeListTile is a custom widget created already
          ),
    );


 ```

  ## Null-aware Operators

Handling null exceptions in app development is very essential, as this allows you to create a seamless experience for your app users. Dart provides you with some handy operators for dealing with values that might be null. One is the ??= assignment operator, which assigns a value of a variable only if that variable is currently null:

###  Example

 ```dart
    int x; // The initial value of any object is null
    x ??=6;
    print(x); // result: 6

    x ??=3;
    print(x); // result is still 6

    print(null ?? 10); // result: 10. Display the value on the left if it's not null else return the value on the right

 ```


  ## Conditional Property Access

To properly safegaurd access to a property or method of an object that might be null, put a question mark (?) before the (.)

###  Example

 ```dart

    userObject?.userName

    //The code snippet above is equivalent to following:

    (userObject !=null) ? userObject.userName : null

    //You can chain multiple uses of ?. together in a single expression

    userObject?.userName?.toString()

    // The preceeding code returns null and never calls toString() if either userObject or userObject.userName is null

 ```

   ## Collections Literals

With literals you can create Dart's built-in lists, maps and sets without hassle.

###  Example

 ```dart

final fruitList = ["Orange","Bannana","Carrot","Apple"]; // A list of fruit
final countrySet = {"Nigeria","United States","Poland","Italy"}; // A set of country
final credMap = {
    'userName': 'temi',
    'password': 'xmen'
} // A map of user credentials

 ```

 You maybe wondering why we didn't explicitly declare a type for all of the collections above. It's interesting to know that dart's type inference can assign types to these variables for you. In this case, the inferred types are List<String>, Set<String> and Map<String,String>.

 Please note that you can choose to specify a type for your variable declaration like this:

  ```dart

final fruitList = <String>[];
final countrySet = <String>{};
final credMap = <String, String>{};

 ```

   ## Arrow Syntax

 Remember Lambda Functions as discussed earlier in this sheet? We used a symbol => to define our lambda expression. You can check out Lambda function section for more explanation.

###  Example

 ```dart

String _firstName = "Michael";
String _lastName = "Jones";
String _middleName = "Will";

String get fullName => '$_firstName $_middleName $_lastName'; // result: 'Michael Will Jones'


 ```

  ## Iterations

Just like every other programming language out there, you can perform iterations in dart. Here is a for loop example

###  Example

 ```dart

for (int i=0; i<=20; i++){
    print(i); // prints 1 to 20
}

var fruitList = ["Orange","Bannana","Carrot","Apple"];
for (final fruit in fruits){
    print(fruit); // prints all types of fruit in the list
}

 ```

   ## Map 

Map can either be declared using literals or map constructor. To learn more about map declaration using literals, please go to the Collections Literals section. Here is how you can declare map using a map constructor:

###  Example

 ```dart
var user = new Map();
// To initialize the map, do this:
user['firstName'] = 'Paul';
user['lastName'] = 'Pogba';

// Result: {firstName: Paul, lastName: Pogba}


// Below are map properties

- Keys
- Values
- Length
- isEmpty
- isNotEmpty

// Below are map functions

- addAll()
- clear()
- remove()
- forEach()
 ```

   ## Variables

Here's an example of creating a variable and initializing it:

###  Example

 ```dart
int x = 2; // explicitly typed
var p = 5; // type inferred
p = "cool"; // ops! throws an error
dynamic z = 8; // variable can take on any type
z = "cool"; // cool

// if you never intend to change a variable use final or const. Something like this:

final email = "temid@gmail.com"; // you can't change the value
final String email = "temid@gmail.com"; // you can't change the value

// iPhone 11 Pro max calculator using const

const qty = 5;
const totalCost = 1099 * qty;

 ```

   ## Class

In Dart, the class keyword is used to declare a class. Here is a basic example:

###  Example

 ```dart
class Car {  
   // field 
   String engine = "E1001"; 
   // function 
   void disp() { 
      print(engine); 
   } 
}

 ```

   ## Getters and Setters

Getters and setters are special methods that provide read and write access to an object’s properties. Each instance variable of your class has an implicit getter, and a setter if needed. In dart, you can take this even further by implementing your own getters and setters. If you've had any experience in Object-Oriented Programming you'll feel right at home. Here is a basic syntax for a class:

###  Example

 ```dart
class className {
 fields;
 getters/setters
 constructor
 methods/functions
}
 ```

```dart
class Person {
  String firstName;
  String lastName;
  double height;
  int personAge;
  int yearofBirth;
  double weight;

  int get age {
    return personAge;
  }

  void set age(int currentYear) {
    personAge = currentYear - yearofBirth;
  }

  // We can also eliminate the setter and just use a getter.
  //int get age {
  //  return DateTime.now().year - yearofBirth;
  //}

  Person({this.firstName,this.lastName,this.personAge,this.yearofBirth,this.weight});
}
 ```

 We can implement Person class this way:

```dart
void main() {
 Person person = Person(firstName:"Thanos",lastName:"Rednos",yearofBirth:1990,weight:200.5);
  print(person.firstName); // output - Thanos
  print(person.lastName); // output - Rednos
  person.age = 2019;
  print(person.age); // output - 29

}
```


   ## Futures: Async and Await

The async and await keywords provide a declarative way to define asynchronous functions and use their results. Remember these two basic guidelines when using async and await:

- To define an async function, add async before the function body:
- The await keyword works only in async functions.

###  Example

 ```dart
Future<String> login() {
  // Imagine that this function is
  // more complex and slow.
  String userName="Temidjoy";
  return
   Future.delayed(
     Duration(seconds: 4), () => userName);
}

// Asynchronous
main() async {
  print('Authenticating please wait...');
  print(await userName());
}

 ```

   ## JSON and serialization

Most mobile and web apps use JSON for tasks such as exchanging data with a web server. With Dart support for JSON serialization and deserialization: converting Dart objects to and from JSON, data exchange is made easy in flutter development.

The following libraries and packages are useful across Dart platform:

- [dart:convert](https://dart.dev/guides/libraries/library-tour#dartconvert---decoding-and-encoding-json-utf-8-and-more)
   Converters for both JSON and UTF-8 (the character encoding that JSON requires).
- [package:json_serializable](https://pub.dev/packages/json_serializable)
   An easy-to-use code generation package. When you add some metadata annotations and use the builder provided by this package, the Dart build system generates serialization and deserialization code for you.
- [package:built_value](https://pub.dev/packages/built_value)
   A powerful, opinionated alternative to json_serializable.


You need to serialize and deserialize JSON in your Flutter project? [see this example](https://flutter.dev/docs/development/data-and-backend/json) to quickly get started.



   ## Reading and decoding a file

The code snippet below reads a file and runs two transforms over the stream. It first converts the data from UTF8 and then runs it through a LineSplitter. All lines are printed, except any that begin with a hashtag, #.

###  Example

 ```dart
import 'dart:convert';
import 'dart:io';

Future<void> main(List<String> args) async {
  var file = File(args[0]);
  var lines = utf8.decoder
      .bind(file.openRead())
      .transform(LineSplitter());
  await for (var line in lines) {
    if (!line.startsWith('#')) print(line);
  }
}

 ```
 
 ## List of Algorithms

See our [directory](https://github.com/TheAlgorithms/Dart/blob/master/DIRECTORY.md) for full list of all algorithms. A few of the algorithms (the most common ones) are explained here.

## Search Algorithms

### Linear
![alt text][linear-image]

From [Wikipedia][linear-wiki]: linear search or sequential search is a method for finding a target value within a list. It sequentially checks each element of the list for the target value until a match is found or until all the elements have been searched.
  Linear search runs in at the worst linear time and makes at most n comparisons, where n is the length of the list.

__Properties__
* Worst case performance    O(n)
* Best case performance    O(1)
* Average case performance    O(n)
* Worst case space complexity    O(1) iterative


### Binary
![alt text][binary-image]

From [Wikipedia][binary-wiki]: Binary search, also known as half-interval search or logarithmic search, is a search algorithm that finds the position of a target value within a sorted array. It compares the target value to the middle element of the array; if they are unequal, the half in which the target cannot lie is eliminated and the search continues on the remaining half until it is successful.

__Properties__
* Worst case performance    O(log n)
* Best case performance    O(1)
* Average case performance    O(log n)
* Worst case space complexity    O(1)

----------------------------------------------------------------------------------------------------------------------

## Sort Algorithms


### Bubble
![alt text][bubble-image]

From [Wikipedia][bubble-wiki]: Bubble sort, sometimes referred to as sinking sort, is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, which indicates that the list is sorted.

__Properties__
* Worst case performance    O(n^2)
* Best case performance    O(n)
* Average case performance    O(n^2)

###### View the algorithm in [action][bubble-toptal]



### Insertion
![alt text][insertion-image]

From [Wikipedia][insertion-wiki]: Insertion sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

__Properties__
* Worst case performance    O(n^2)
* Best case performance    O(n)
* Average case performance    O(n^2)

###### View the algorithm in [action][insertion-toptal]


### Quick
![alt text][quick-image]

From [Wikipedia][quick-wiki]: Quicksort (sometimes called partition-exchange sort) is an efficient sorting algorithm, serving as a systematic method for placing the elements of an array in order.

__Properties__
* Worst case performance    O(n^2)
* Best case performance    O(n log n) or O(n) with three-way partition
* Average case performance    O(n^2)

###### View the algorithm in [action][quick-toptal]

### Selection
![alt text][selection-image]

From [Wikipedia][selection-wiki]: The algorithm divides the input list into two parts: the sublist of items already sorted, which is built up from left to right at the front (left) of the list, and the sublist of items remaining to be sorted that occupy the rest of the list. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list. The algorithm proceeds by finding the smallest (or largest, depending on sorting order) element in the unsorted sublist, exchanging (swapping) it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right.

__Properties__
* Worst case performance    O(n^2)
* Best case performance    O(n^2)
* Average case performance    O(n^2)

###### View the algorithm in [action][selection-toptal]


### Merge
![alt text][merge-image]

From [Wikipedia][merge-wiki]: Merge sort (also commonly spelled mergesort) is a divide and conquer algorithm that was invented by John von Neumann in 1945. The algorithm dirst divides the list into the smallest unit (1 element), then compares each element with the adjacent list to sort and merge the two adjacent lists. Finally all the elements are sorted and merged. It is an efficient, general-purpose, comparison-based sorting algorithm.

__Properties__
* Worst case performance    O(n log n)
* Best case performance    O(n log n)
* Average case performance    O(n log n)

###### View the algorithm in [action][merge-toptal]


### Shell
![alt text][shell-image]

From [Wikipedia][shell-wiki]:  Shellsort is a generalization of insertion sort that allows the exchange of items that are far apart.  The idea is to arrange the list of elements so that, starting anywhere, considering every nth element gives a sorted list.  Such a list is said to be h-sorted.  Equivalently, it can be thought of as h interleaved lists, each individually sorted.

__Properties__
* Worst case performance O(nlog2 2n)
* Best case performance O(n log n)
* Average case performance depends on gap sequence

###### View the algorithm in [action][shell-toptal]

### Time-Complexity Graphs

Comparing the complexity of sorting algorithms (Bubble Sort, Insertion Sort, Selection Sort)

[Complexity Graphs](https://github.com/prateekiiest/Python/blob/master/sorts/sortinggraphs.png)

[bubble-toptal]: https://www.toptal.com/developers/sorting-algorithms/bubble-sort
[bubble-wiki]: https://en.wikipedia.org/wiki/Bubble_sort
[bubble-image]: https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Bubblesort-edited-color.svg/220px-Bubblesort-edited-color.svg.png "Bubble Sort"

[insertion-toptal]: https://www.toptal.com/developers/sorting-algorithms/insertion-sort
[insertion-wiki]: https://en.wikipedia.org/wiki/Insertion_sort
[insertion-image]: https://upload.wikimedia.org/wikipedia/commons/7/7e/Insertionsort-edited.png "Insertion Sort"

[quick-toptal]: https://www.toptal.com/developers/sorting-algorithms/quick-sort
[quick-wiki]: https://en.wikipedia.org/wiki/Quicksort
[quick-image]: https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif "Quick Sort"

[merge-toptal]: https://www.toptal.com/developers/sorting-algorithms/merge-sort
[merge-wiki]: https://en.wikipedia.org/wiki/Merge_sort
[merge-image]: https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif "Merge Sort"

[selection-toptal]: https://www.toptal.com/developers/sorting-algorithms/selection-sort
[selection-wiki]: https://en.wikipedia.org/wiki/Selection_sort
[selection-image]: https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/Selection_sort_animation.gif/250px-Selection_sort_animation.gif "Selection Sort Sort"

[shell-toptal]: https://www.toptal.com/developers/sorting-algorithms/shell-sort
[shell-wiki]: https://en.wikipedia.org/wiki/Shellsort
[shell-image]: https://upload.wikimedia.org/wikipedia/commons/d/d8/Sorting_shellsort_anim.gif "Shell Sort"

[linear-wiki]: https://en.wikipedia.org/wiki/Linear_search
[linear-image]: http://www.tutorialspoint.com/data_structures_algorithms/images/linear_search.gif

[binary-wiki]: https://en.wikipedia.org/wiki/Binary_search_algorithm
[binary-image]: https://upload.wikimedia.org/wikipedia/commons/f/f7/Binary_search_into_array.png
