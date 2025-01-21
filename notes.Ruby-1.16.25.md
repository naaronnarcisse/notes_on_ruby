# Ruby

## Time tracking

- 8 days left till deadline

### What, Why, How

#### What is our goal?

1. With informational (**static**) web sites, when someone visits a URL (**sends an HTTP request**), we respond with the same, unchanging HTML file - no matter who they are or when they sent the request
2. With an interactive web application, when someone sends us an **HTTP request**, we respond **dynamically**.
    1. We might look up some information about the user and use that to calculate something interesting for them; we might use an **API** to get the current weather or send a text message or generate an image with AI; an *application* can do anything
    2. Crucially, the HTML that we respond with will be unique to *that particular request*, at that *particular moment in time*. 
        - So, if a user send a request for the same URL a minute later, the HTML that we respond with might be quite different
    3. If the HTML that we're responding with is unique from user to user and moment to moment, then we clearly can'ts handwrite it in real-time. Instead, we have to ***automate the writing of unique HTML responses***
    4. In order to automate anything with a computer, we have to learn to **program**

#### Ruby and Programming

1. The creator of Ruby is Yukihiro Matsumoto
2. Ruby is a beginner friendly programming language

#### Ruby on Rails and other libraries

1. Any programming language can do anything that any other programming language can
    1. Though, it's important to consider which language has the largest **community** of developers doing Task X. (Task X might be web apps, data analysis, game programming, etc.)
    2. More community means that other people have already solved many of the problems you'll face, so there might be code out there that you can borrow instead of having to write it all yourself
    3. Pre-written code that you borrow is known as a **library** or **package**. In Ruby, we call them **gems**
2. The **most important condsideration** is: what language are other developers already using for that job?
3. For the **rapid development of web applications**, Ruby has a huge and thriving community
4. **Ruby on Rails** is a framework for building web applications created by David Heinemeier Hansson
    1. The goal of Ruby on Rails is to make it possible for a single person, a full-stack developer, to create powerful, industrial-grade applications
    2. Most frameworks don't make it their primary ambition to be useful to solo developers.
5. The **editor** is the pane where you write your code and the **output window** is the pane where your output is displayed

### The fundamentals of Ruby

#### The fundamental syntax of Ruby

1. The fundamental syntax of Ruby looks like this: `2.add(3)`
    1. The thing on the left side of the dot (`.`), in this example `2`, is called the **object**
    2. The things on the right side of the dot, in this example `.add(3)`, is called the **method**
    3. The **method** has two parts:
        - `add` is called the **name** of the method
        - `(3)` is called the **argument** to the method
    4. More formally: What comes on the left side of the dot is known as the *receiver* and what comes on the right side of the dot is known as the *message*
    5. All together, the object, the method, and the argument is called an **expression**
    6. The `add` method increases the number that it was called upon (the number on the left side of the dot, the receiver) by the number provided as its argument (the number within the parentheses, the message side of the dot), and returns the result
        1. When **evaluated**, the method **returns** another object. The **expression** is then replaced by, or "substituted with", the return value
        2. So, the expression `2.add(3)` returns the object, `5`
2. In this example, `5.multiply(2)`, the `multiply` method takes the number it was called upon, the object (5), multiplies it by the number provided as its argument and returns the result
3. When evaluating multiple expressions within the same line, for example: `3.add(4.multiply(2))`, Ruby starts on the left and then proceeds to the right, searching for the first *complete, self-contained* expression
4. The `divided_by` method takes the number it was called upon, divides it by the number provide as its argument, and returns the result
5. We have to use special methods to explicitly instruct Ruby to print expressions that we want to see, for example: `self.pp(2.add(3))`
    1. `self` is a special object. The short version: as the program is being executed, `self` represents different objects at different times - whichever object Ruby is currently operating on
        - In this example, `self` represents the program itself, also known as the **the main object**.
    2. `pp` (pronounced "pretty print") is a method that we are allowed to execute, or "call", on the main object. `pp` takes its argument and displays it, or "prints" it, in the output window

###### Syntactic sugar

6. Ruby includes many handy shortcuts, known as "syntactic sugar", to make writing and reading Ruby more enjoyable. Two examples include:
    1. **`self` as the implicit receiver**
        - If you're calling a method on `self`, you can leave out the `self` and the `.`; Ruby will figure out what you mean. 
        - So `self.pp(4.add(6.divided_by(2)))` can also be written as `pp(4.add(6.divided_by(2)))`
        - You can ***only*** use this shortcut when calling methods on `self`
        - `self` is known as the "implicit receiver" of all method calls that are not explicitly attached to an object with a dot (`.`)
    2. **Dropping the parentheses around arguments**
        - You're allowed to leave out the parentheses around arguments
        - So, `pp(4.add(6.divided_by(2)))` can also be written as `pp 4.add(6.divided_by(2))` and also `pp 4.add 6.divided_by 2`, but this is **not** recommended because it can get confusing very quick
    3. Together these two shortcuts help us go from `self.pp(2.add(3))` to pp 2.add(3)
    4. All we have to do to see what a line of Ruby is doing is pop a `pp` at the start of the line and this is good because our rule of thumb is: **Make the invisible visble**

#### A deeper look

1. **Objects** (the "receiver") are on the left side of the dot and **methods** (the "message") are on the right side of the dot
    1. Objects are like *nouns* and methods are like *verbs*. An object is some *information* that represents a thing while methods are *actions* that the thing is able to perform
    2. Together, the object, dot, and method are called one **expression**
    3. The expression is **evaluated**, meaning the method is executed on the object. The result is a new object, which replaces the orginal expression. This object is called the **return value** of the method

###### Ruby's vocabulary

1. Ruby can work with many more kinds of data than just numbers. Ruby has: 
    - Numbers
    - Text
    - Dates
    - Times
    - True/False
    - Lists containing multiple pieces of data
    - etc
2. Each kind, or **class**, of data has its own set of **methods** that it can perform. For example:
    1. Numbers can do the usual things - add, subtract, multiply, etc.
    2. Two dates can tell you how far apart they are from one another
    3. Lists can tell you how long they are, or sort themselves
3. We can even *make up our own nouns and verbs* and add them to the language. For example, we can create a data type `Venue`, give it a method that calculates the average rating from its reviews, and then use that method whenever we want

###### Ruby's primary syntax

1. To access the powerful set of **data** and **methods** Ruby comes with, the **primary syntax** is straightforward. It looks like this: `some_object.some_method`.
2. The primary way to write an expression in Ruby is: `object.method`. We ask the *thing*, or noun, on the left side of the dot to perform the *action*, or the verb, on the right side of the dot
3. The computer then evaluates the expression; `pp "Hello, world!".upcase`, and **returns** a new piece of data in its place, which in this case would be `"HELLO, WORLD!` 
4. A **string** is Ruby's name for the datatype that holds a piece of text, and refers to a string of **characters**

###### Every class has different methods

1. Different **classes** (`String` being one) can perform different **methods**
2. Almost everything in Ruby is an **object**. That's the idea behind **object-oriented programming**. Text like `"Hello, world!"` is an object - specifically a `String` **object**
3. The `length` string method tells you how many characters are in a string
4. **Always read your error messages**
5. **Always use the methods available to each specific class** because a number method won't on a string method

#### Arguments are inputs

1. The **primary syntax** in Ruby, `object.method`, is straightforward. However, some methods require additional inputs.
    1. For example, there's a method called `gsub` which we can call on a `String`, which will substitute one set of characters with another set of characters
    2. `gsub` is short for "globally substitute" because it will replace *all* occurrences of one *substring* with another *substring*
    3. The `gsub` method needs to know what *substring* to get rid of and what to replace it with, so we give it inputs, or **arguments**
2. **Arguments** must come in parentheses *immediately* following the method. If the method takes multiple arguments, as `gsub` does, then they are seperated by commas. For example, `pp "Java is such a joy!".gsub("Java", "Ruby")` will return the value, `"Ruby is such a joy!"`
3. In reality, `gsub` is more often used to do things like removing invalid characters from usernames before saving, for example: `pp "Naaron@Narc@isse".gsub("@", "")`
    1. `""` is an empty string, so all the `@`s will be replaces with nothing, essentially removed. And it will return, `"NaaronNarcisse"`

#### Whitespace

1. Ruby, unlike other programming languages, is very flexible when it comes to indentation and spacing 
2. One of the only times whitespace matters is when you put a space between the method and the opening parentheses that holds the arguments like this `pp "Naaron@Narci@sse".gsub ("@", "")`

#### Code comments

1. The pound symbol (`#`) is used in Ruby to comment.
2. The Ruby interpreter, when it sees the `#`, will ignore it and everything that comes after it; allowing us to leave notes to ourselves and to each other.
3. **Use comments liberally**
4. Every programming language has its own syntax for leaving comments in the code, but comments in Ruby are done with one `#` at the start of the line
5. In most text editors, the keyboard shortcut `ctrl + /` (for Windows) and `cmd + /` (for Mac) will automatically detect the languaeg you're writing and comment the line for you

#### Variables

1. **Variables** allow us to store our return values for future reference instead of forgetting them
2. The single equal sign, `=`, is called the **variable assignment operator**
    1. When you read `reversed = "hello, world!".reverse` out loud, you would say "hello world dot reverse is *assigned* to the variable reversed" because **Ruby read it from the right side first**
    2. Ruby first evaluates the expression on the right side of the assignment operator, `=`, and *then* stores the resulting value in the variable named on the left
3. Most Ruby methods **don't modify the orginal object** that they are called upon; they just **return a modified copy**
4. So, the **variable assignment operator** (`=`) can have the same variable on the left and right side and is used to store objects (data) in variables. 

###### Variable syntax

1. First, the expression on the right side of the assignment operator will be evaluated until there are no methods left and there's jsut a piece of data remaining
2. Then, that value will be placed in the variable named on the left side of the assignment operator, which will be created if it doesn't exist, or will have its value replaced if it does exist

#### Variable naming rules

1. Variable names can only contain **lowercase** letters (`a...z`), numbers (`0...9`), and underscores (`_`) --- they **can't** contain spaces
2. Variable names can't **begin** with a number
3. Rubyists strive to choose **descriptive** variable names, no matter how long they are, so that it's obvious to teammates what the contents are at a glance
4. Use underscores (`_`) to seperate words in multi-word variable names, since we can't use spaces
5. **Avoid** naming your variables `x`, `y`, and `z`
