# Ruby

## Time tracking

- 4 days left

### The String class

#### Introduction

1. The ***only*** time we use capital letters when we're programming is when we refer to Ruby classes. Example: `String`
2. All other times - variable names, file names, etc - we're going to use lowercase letters only
3. The name "String" is used in pretty much every programming language for the datatype that holds a piece of text, and refers to a string of *characters*

#### Creating strings

1. In Ruby, the formal way to create a new object is to use the `.new` method on the parent class. Example: `s = String.new`
    1. This will, however, just give us back an empty string `""`; but we can ask any object in Ruby what it is with the `.class` method

#### ASCII Codes

1. With the `String.new` approach, we would have to add each character to our variable `s` one by one
    1. The `.concat` method accepts a number as an argument, interprets it as an ASCII code, translates it into a single character, and adds it on to the end of the orginal string
    2. Example: 

    `my_string = String.new`

    `my_string = my_string.concat(32)`

    3. As you can see, even creating Strings follows the syntax of `noun.verb`
2. At the hardware level, computers only store integers (specifically, in *binary* form - using only `0`s and `1`s); so all other datatypes need to be encoded somehow as a number.
    1. **ASCII or American Standard Code for Information Interchange**, was one scheme that was developed in the early days of computing to store English characters as integers
    2. We currently use more sophisticated encoding schemes such as **Unicode** that supports glyphs from many more languages and even emojis

#### String literals

1. By typing the characters you want within quotes, you use the shortcut of creating string "**literals**. Example: "Thank goodness"
2. These kinds of exceptions to the regular grammar in order to make life easier are known as "**syntactic sugar**"

#### Methods

###### String addition, a.k.a. +

1. `.concat` can accept an integer as an argument, which it interprets as an ASCII code, translates into a single character, and adds to the original string: `pp "hi".concat(33)`
2. `.concat` can also accept a string literal as an argument, in which case it jsut adds the whole thing to the end of the original string: `pp "hi".concat(" there")
3. There's also a shorthand for `.concat`: `.+`
4. Another piece of sweet syntactic sugar that Ruby provides us with is that we can drop the `.` and the parentheses when using the `+` addition method: `pp "hi" + "there"`

###### String multiplication, a.k.a. *

1. `String`s can be multiplied by numbers using the `*` multiplication method: `"Ya" * 5` => `"YaYaYaYaYa"`
2. More syntactic sugar here, like with the `+` method above; you can say `"Ya" * 5` rather than `"Ya".*(5)`
3. Don't ever switch the order in which you write the expression because to changes the meaning of the expression, remember what's "under the hood"

###### reverse

1. The reverse method returns a new `String` with the characters from the `String` in reverse order: `pp "I can speak in backwords words".reverse` => `""sdrow sdrowkcab ni kaeps nac I"`

###### upcase

1. The upcase method returns a copy of the `String` with all lowercase letters replaced with their uppercase counterparts: `pp "love".upcase` => `"LOVE"`

###### downcase

1. The downcase method returns a copy of the `String` with all uppercase letters replaced with their lowercase counterparts: `pp "LOVE".downcase` => `"love"`

###### swapcase

1. The swapcase method returns a copy of the `String` with all uppercase letters replaced with their lowercase counterparts *and* vice versa: `pp "LOve".swapcase` => `"loVE"`

###### gsub

1. The `gsub` method returns a copy of the `String` it was called on with all occurrences of the first argument substituted for the second argument

###### strip

1. `strip` removes all leading and trailing whitespace: `pp "      This has a lot of space on the outside".strip` => `"This has a lot of space on the outside"`

###### capitalize

1. capitalize returns a `String` with the first character converted to uppercase and the remainder to lowercase: `pp "begin".capitalize` => `"Begin"`

### The Integer class

#### Introduction

1. Ruby differentiates between whole numbers (`Integer`s) and decimal numbers (`Float`s)

#### Syntax

1. `Integer`s begin with a digit (0-9) and end when Ruby meets anything other than a digit - *except* for underscores, which you can use as a **delimiter** if it helps to understand the number: so underscores work like commas to make it easier to read a number: 10000 => 10_000 

#### Methods

###### + - * / % ** (math)

1. The math methods have the same syntactic sugar that the `String` versions did, so we can say `12 + 5` rather than 12.+(5)`
2. `pp 12 / 5` will return `2` because the `Integer` version of division will only return another `Integer`, and so `/` only returns the whole part
    1. If you want the remainder, you have to use the **modulus** (`%`) operator: `pp 12 % 5` => `2`
3. To raise a number to a power, like 3^2, you use the double star operator (`**`): `pp 3 ** 2`

###### odd? and even?

1. The `.odd?` and `.even?` methods return `true` or `false` based on whether the number is odd or even
2. The question mark at the end is just another letter. Rubyists like to end method names with a question mark when methods return `true` or `false`

###### rand

1. `rand` is a special method like `pp` that are allowed to call on the left side of the dot
2. `rand` returns a random number and is very useful for all kinds of stuff, everything from games to statistical analysis: `rand(6)` => It will return a random integer between 0 and 5

###### String#to_i (`String` method)

1. Sometimes you have a `String` that contains a number, usually input from a user, and want to do math on it. `to_i` will attempt to convert a `String` object into an `Integer` object: `rand("9".to_i)`

###### to_s (`Integer` method)

1. When you want combine `Integer`s with `String`s, you need to convert the `Integer` into a `String` prior to output and the `Integer` method, `to_s` (or "to string"), solves that issue: `pp "My number is " + 70.to_s` => "My number is 70"

###### to_f 

1. The `to_f` (or "to float") method to convert an `Integer` to a `Float`, which is often handy for doing math

### The Float class

#### Introduction

1. Ruby calls decimal numbers `Float`s.
2. To create a `Float` rather than an `Integer`, just make sure to include a decimal point

#### Methods

###### + - * / % ** (math)

1. The math methods work almost identically as the `Integer` math methods, *except* for division (`/`), which returns a fractional result: `pp 12.0 / 5.0` => `2.4`
2. If either side of an equation is a `Float`, then `Float` division will be performed: `pp 12 / 5.0` => `2.4`
3. You can use `**` in conjunction with fractions to calculate roots, since 9^1/2 is the same as the square root of 9 and 8^1/3 is the same as the cube root of 8: `pp 9 ** 0.5` => `3.0` and `pp 8 ** 1/3.0` => `2.0`

###### round

1. `Floats` can round themselves with the `.round` method: `pp (10.0 / 3).round(5)` => `3.33333` (rounded to 5 decimal places)

###### rand

1. The `rand` method from earlier can also be called with no arguments, in which case it returns a `Float` between 0 and 1: `pp rand` 
2. This is handy for things like probabilities 

### The Date class

#### Introduction

1. Ruby has a built-in class that makes it much easier to work with dates: `Date`

#### Creating a date

1. The `Date` class isn't loaded into every Ruby program by default, so to use it we need to first say: `require "date"`

#### Date.new

1. After `require "date"`, we can create a new instance as usual with `.new`: `new_date = Date.new`
2. The default value of `new_date` is `#<Date: -4712-01-01 ((0j,0s,0n),+0s,2299161j)>`, so January 1st of the year, 4712
3. You can pass `Date.new` arguments to initialize with a specific year, month, and day

#### Date Methods

###### Date.today

1. The `Date.today` method returns an object initialized to the current date: `pp Date.today`

###### year

1. Call the `year` method on a `Date` object to return just the year of the date as an integer: `pp Date.today.year`

###### month

1. Call the `month` method on a `Date` object to return just the month of the date as an Integer

###### day

1. Call the `day` method on a `Date` object to return just the day of the date as an `Integer`

###### Date.parse

1. The `Date.parse()` method accepts a `String` argument and tries to interpret it as a date, initializing a `Date` object:

    require "date"
    pp Date.parse("2001-02-03")
    pp Date.parse("20010203")
    pp Date.parse("3rd Feb 2001")

###### Subtraction

1. You can subtract two dates from one another, which will return the number of days between them
2. The return value class is `Rational`, which can be converted to a regular `Integer` with `.to_i`:

        require "date"

        number_of_days = Date.today - Date.parse("July 4, 1776")

        pp number_of_days   =>  (90785/1)
        pp number_of_days.class =>  Rational

        pp number_of_days.to_i  =>  90785

### Time

#### Introduction

1. Ruby has a `Time` class as well (pre-loaded like `String`, not need to `require` anything), that shares most of its methods with the `Date` class. Rather than `Date.today`, we write `Time.now`, which makes sense. By default, it will return the time in ***UTC***
2. `Time` methods:

        pp Time.now
        pp Time.now.class
        pp Time.now.year
        pp Time.now.day
        pp Time.now.hour

#### strftime

1. The `strftime` method is used on a `Date` or `Time` object. It requires a `String` argument that will be used to format the `Date` or `Time` in a particular way
2. You should **not** try to memorize what these patterns mean. Tools like **strftime.net** and **For a Good Strftime** exist to help compose the formatting string argument
3. Examples:

        # weekday
        pp Time.now.strftime("%A")

        # month
        pp Time.now.strftime("%B")

        # month abbreviated
        pp Time.now.strftime("%b")

        # weekday abbreviated, day of month, time and minutes with AM/PM
        pp Time.now.strftime("%a %e, %R %p")

### Array

#### Introduction

1. `Array` is a data type that helps us manage lists of things
2. This class, unlike the ones we've seen until now, is really just a *container* for other objects, and can hold however many objects we want

#### Creating arrays

1. The formal way to create a new object in Ruby is to use the `.new` method on the parent class:

        cities = Array.new
        pp cities.class    =>   Array
        pp cities   =>  []

###### push

1. Ruby represents an `Array` with square brackets, `[]`.
2. The brand new array is empty; let's add some **elements** to it with the `.push` method:

        snacks = Array.new

        snacks.push("bagel", "donut")

        pp snacks

###### Array literals

1. Much like `String`s, there's a shortcut to creating `Array`s
2. Rather than starting with `Array.new` and building it up from scratch one `.push` at a time, we can type an array "**literal**" directly into the code:

        cities = ["Chicago", "NYC", "LA"]

        pp cities

#### `Array`'s Methods

###### at

1. After adding **elements** to the list, the next most important thing we need to be able to do is retrieve an element back out from the list. Our first tool for doing that is `.at`
2. The `.at` method takes an `Integer` argument, which is interpreted as the position, or **index**, in the `Array` of the element that you want to retrieve:

        cities = ["Chicago", "NYC", "LA", "SF", "NOLA"]

        pp cities   =>  ["Chicago", "NYC", "LA", "SF", "NOLA"]
        pp cities.at(2)    =>   "LA"

3. The output is surprisingly `"LA"`!
    1. Pretty much every programming language indexes the elements in an array starting at *zero* (`0`), **not** at one.
    2. So, the first element, "Chicago", is retrieved with `cities.at(0)`
4. When you use an index greater than the length of the array, your output is `nil`
    1. `nil` is an object that represents **the absence of anything**
5. When you use negative numbers as the index, we can count backwards through the list of items starting with `-1` (the last item in the array): pp cities.at(-1)   =>  "NOLA"

###### at shorthand, []

1. The shorthand for `.at()` is very common, so it's important to remember. It's the `.[]` method: pp cities.[](2)  =>  "LA"
2. Syntactic sugar: When a class has a method named `.[]`, Ruby allows the dot to be dropped, but the method name has to then move immediately next to the object it's being called on (no space), and the argument moves *inside* the method name: `pp cities[2]`

###### first, last

1. Since retrieving the elements at positions `0` (the first one) and `-1` (the last one) is so common, there are handy shortcut methods for those: `.first` and `.last`:

        pp cities.first    =>   "Chicago"
        pp cities.last     =>   "NOLA"

###### index

1. The `.index` method is sort of the inverse of `.at`: given an object, `.index` searches within the array and returns the index where it resides: `pp cities.index("SF")   =>  3`

###### String#split

1. `.split` is a method for the `String` class
2. This method, when called on a `String`, will return an `Array` of substrings
3. If you provide no argument, the string is split upon whitespace, which is handy for e.g. turning a sentence into a list of words: `pp "alice bob carol".split    =>     ["alice", "bob", "carol"]`
4. If you do provide an argument to `.split`, then the string will be chopped up wherever that argument occurs instead of whitespace - for example, use `"4,8,15,16,23,42".split(",")` to split on commas
5. You can also `split` with the empty string `""`, as an argument in order to turn a string into an `Array` of its individual characters

        a = "Hello!".split("")

        pp a    =>    ["H", "e", "l", "l", "o", "!"]
        pp a.at(0)     =>     "H"
        pp a.at(-1)    =>     "!"

###### count

1. `.count` counts how many elements are in the list, if called with no arguments
2. If an argument is provided, it counts how many times that argument occurs in the list
3. Examples:

        a = [8, 3, 1, 19, 23, 3]

        pp a.count  =>  6

        pp a.count(3)   =>  2

###### sample

1. The method `.sample` will return an unpredictable item from the array

###### min, max, sum

1. Each of these methods is self explanatory.
    1. `.min` is to find the number with the lowest value in the `Array`
    2. `.max` is to find the number with the highest value in the `Array`
    3. `.sum` is to find the sum of the values in the `Array`
