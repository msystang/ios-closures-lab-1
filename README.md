# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```
Answer:
```swift
func applyKTimes(_ k: Int, _ closure: () -> ()) {
for _ in 1...k {
closure()
}
}
applyKTimes(3) {
print("Hello Closures!") }
```

## Question 2 DONE

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`

Answer:
```swift
let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]

let multiples = numbers.filter { (a) -> Bool in
return a % 3 == 0
}

print(multiples)
```

## Question 3 DONE

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`

Asnwer:
```swift
let numbers = [4, 7, 1, 9, 6, 5, 6, 9]

let largestNumber = numbers.reduce(0, {x, y in
return x > y ? x : y
})
```
## Question 4 DONE

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`

Answer:
```swift
let strings = ["We", "Heart", "Swift"]

let oneString = strings.reduce("", {a, b in
a + " " + b
})
print(oneString)
```

## Question 5 DONE

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

Answer:
```
let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]

//a. Use `sortedBy` to sort `cities` in alphabetical order.
let citiesSorted = cities.sorted()
print(citiesSorted)

//b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.
let citiesSortedSecondChar = cities.sorted() { $0.dropFirst() < $1.dropFirst() }
print(citiesSortedSecondChar)

//c. Use `sortedBy` to sort `cities` in order of the length of the city name.
let citiesSortedLength = cities.sorted() { $0.count < $1.count }
print(citiesSortedLength)
```

## Question 6 DONE

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.

Answer:
```swift
let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]

//a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.
let citiesWithPopulationSorted = citiesWithPopulation.sorted() { $0.1 < $1.1 }
print(citiesWithPopulationSorted)

//b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.
let citiesWithPopulationSortedReversed = citiesWithPopulation.sorted() { String($0.0.reversed()) < String($1.0.reversed()) }
print(citiesWithPopulationSortedReversed)
```

## Question 7 DONE

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution
```
Answer:
```swift
var numbers = [1, 2, 3, 4, 5, 6]

func findDivisors(num: Int) -> Int {
var counter = 0
for i in 1...num {
if num % i == 0 {
counter += 1
}
}
return counter
}

let numbersSortedByFactors = numbers.sorted() { findDivisors(num: $0) < findDivisors(num: $1) }
print(numbersSortedByFactors)
```

## Question 8 DONE

Find the sum of the squares of all the odd numbers from `numbers` and then print it.

`var numbers = [1, 2, 3, 4, 5, 6]`

a. Write code that removes all the odd numbers from the array.

b. Write code that squares all the numbers in the array.

c. Write code that finds the sum of the array.

d. Now use `map`, `filter` and `reduce` to solve this problem.

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`

Answer:
```swift
var numbers = [1, 2, 3, 4, 5, 6]

//a. Write code that removes all the odd numbers from the array.
var oddNumbers = [Int]()

for i in numbers {
if i % 2 != 0 {
oddNumbers.append(i)
}
}
print(oddNumbers)

//b. Write code that squares all the numbers in the array.
var squaredNumbers = [Int]()

for i in oddNumbers {
squaredNumbers.append(i*i)
}
print(squaredNumbers)

//c. Write code that finds the sum of the array.
var sum = 0

for i in squaredNumbers {
sum += i
}
print(sum)

//d. Now use `map`, `filter` and `reduce` to solve this problem.

let filteredOddNumbers = numbers.filter() {$0 % 2 != 0}
print(filteredOddNumbers)

let mapSquaredNumbers = filteredOddNumbers.map() {$0*$0}
print(mapSquaredNumbers)

let reduceSum = mapSquaredNumbers.reduce(0, +)
print(reduceSum)
```

## Question 9 DONE

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

Output:

```swift
1
4
9
16
```
Answer:
```swift
func forEach(array: [Int], _ closure: (Int) -> ()) {
for i in array {
closure(i)
}
}

forEach(array: [1, 2, 3, 4]) {
print($0 * $0)
}
```

## Question 10 DONE

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
combineArrays(array1,array2) {
    $0 * $1
}
```

Output: `[5,10,15,12]`

Answer:
```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]

func combineArrays (_ arr1: [Int],_ arr2: [Int], closure:(Int,Int) -> Int ) -> [Int] {
var array3 = [Int]()

for i in 0...arr1.count-1 {
array3.append(closure(arr1[i],arr2[i]))
}
return array3
}

combineArrays(array1,array2) {
$0 * $1
}
```

## Question 11

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```
Answer: 
```swift
//a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

let theInts = [1, 2, 3, 44, 555, 6600, 10763]

func intsToStrings (_ arr: [Int], closure:(Int) -> String) -> [String] {
var theStrings = [String]()
for i in arr {
theStrings.append(closure(i))
}
return theStrings
}


//b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

let asString: (Int) -> String = { String($0) }
print(intsToStrings(theInts, closure: asString))

//c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

let evenOdd: (Int) -> String = {
if $0 % 2 == 0 {
return "Even"
} else {
return "Odd"
}
}
print(intsToStrings(theInts, closure: evenOdd))

//d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

let englishWords: (Int) -> String = {
let digitLetterDict: [Character:String] = ["1":"one", "2":"two", "3":"three", "4":"four", "5":"five", "6":"six", "7":"seven", "8":"eight", "9":"nine", "0":"zero"]
let stringNum = String($0)
var wordArray = [Character]()
var numberAsLetter: String = ""
var stringLetterNumber: String = ""

for char in stringNum {
wordArray.append(char)
}

for num in wordArray {
numberAsLetter = digitLetterDict[num]!
stringLetterNumber.append(contentsOf: "\(numberAsLetter) ")
}
return stringLetterNumber
}

print(intsToStrings(theInts, closure: englishWords))
```

## Question 12

let myArray = [34,42,42,1,3,4,3,2,49]

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
let mySortedArray = myArray.sort(ascendingOrder)
let ascendingOrder =
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
let mySecondSortedArray = myArray.sort(descendingOrder)
let descendingOrder =
```


## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.


## Question 14

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

`var codeString = "aldfjaekwjnfaekjnf"`

b) Sort the string below in ascending order according the dictionary `letterValues`

`var codeStringTwo = "znwemnrfewpiqn"`

## Question 15

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]
```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc
```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.

d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```
