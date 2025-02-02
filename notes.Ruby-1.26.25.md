# Ruby

### String interpolation and printing

#### String interpolation, alternative to `.to_s`

1. **String interpolation** is an alternative to `.to_s`.
2. Basically, inside the string, you place `#{}` where you eventually want your value to go. Inside the curly braces, you can write any Ruby expression without worrying about whether it is a string or not. The expression will be evaluated, converted to a string, and added to the string right in that spot.
3. You can interpolate as many expressions as you want into a single string
4. Example:

        number = 6
        another_number = 6.6
        a_string = "my numbers are"
        message = "today #{a_string}: #{number} and #{another_number}."
        pp message  =>  "today my numbers are: 6 and 6.6."
5. In Ruby, single quotes ('') won't interpolate your variables, only double quotes

#### Date format with string interpolation

1. Practice example:

        require "date"

        first = Date.new(2020,7,1)
        first_year = first.year
        first_month = first.month
        first_day = first.day

        pp "The year is: #{first_year}, the calendar day is: #{first_day}, and the month is: #{first_month}."

        second = Date.new(2020, 6, 29)
        second_year = second.year
        second_month = second.month
        second_day = second.day

        pp "The year is: #{second_year}, the calendar day is: #{second_day}, and the month is: #{second_month}."

#### The many ways of printing

###### Put string (`puts`)

1. The `pp` methods shows an object in all of its gory, technical detail because we're usually printing in order to debug our code 
    1. Behind the scenes, `pp` calls a method `.inspect` on whatever object you give it. 
    2. `.inspect` can be called on any object, and returns a `String` with additional information about the object
    3. Then `pp` displays tha string
2. Sometimes you want the output to look nice and clean for the end user.
    1. For those times, use the method, `puts` (pronounced "put string" or "put S")
    2. Behind the scenes, `puts` calls a method `.to_s` on whatever object you give it. `.to_s` can be called on any object, and returns a *user-friendly, formatted* `String` representing the object. Then , `puts` displays that string
3. `puts` uses `.to_s` in order to get a string that's nicely formatted for an end user, and `pp` uses `.inspect` in order to get a string that contains the fory technical details for a developer

#### Escape characters

1. When you come across `String`s in this class and online, you may begin to see frequent backslash `\` characters within them.
    1. A very common one is the so called "newline" character: `"\n"`
2. The combination `\n` represents a new paragraph or a line break
    1. Backslashes are **escape characters** that invoke an *alternative interpretation* of the following character in a sequence
    2. So, in the case of our `\n` combination, we are saying, "This is not the letter n, this is a newline"

            my_string = "RaghuBetina\nthe instructor"
            puts my_string

###### Quotes within quotes

1. Escape characters can be used anywhere to invoke an alternative interpretation of a character that follows it
2. `\s` adds a space

        my_string = "Raghu\sBetina\nthe instructor"
        puts my_string
3. One way to include a string within a string is to use single quotes within double quotes: `my_string = "'RaghuBetina'"`
    1. Another way to include a quote within a quote is to put a `\` before the `"`, so that the quotation is treated as a character instead of a `String` literal syntactic sugar: `my_string = "\"RaghuBetina\""`

#### Multi-line strings

1. Building a **multi-line string** is perfectly valid as long as there is one opening quote and one closing

    ms = "
        Some string \"with a quote in it\"
        with some more text continued below
        "
    puts ms
2. The `\` escape character is particularly impotant in situations like this to place strings within strings on multiple lines

### If statements (conditionals)

#### Introduction

1. To add conditions based on user input, we need to add a new grammar to our toolbox: the `if/end` **keywords**:

        lucky_number = rand(100)

        pp "Your lucky number is " + lucky_number.to_s + "."

        if lucky_number.odd?
        pp "The number is odd."
        end

        if lucky_number.even?
            puts "The number is even"
        end

2. These expressions which *conditionally* run some code based on the truth or falseness of some condition, are known as **conditonals** or **if statements**

#### The basic anatomy of if statements

1. The anatomy of an `if` statement is:

        if condition
        # code that runs if the condition is true
        end
    1. First comes the `if` keyword
    2. After the `if`, on the same line, comes any Ruby expression, which is evaluated until only one piece of data is left
    3. If that final return value of `condition` is "truthy", then the code on the lines between the `if` and `end` keywords is executed
    4. If the final return value of `condition` is "falsy", then the code on the lines between the `if` and `end` keywords is ignored
    5. Either way, the programm picks up execution on the next line after the `end` keyword and continues on

###### Don't forget the end

1. Every `if` requires a matching `end`
2. It's wise to type the `end` *immediately* after typing the `if` so you don't forget it; *then* worry about typing the condition, and the code that comes on the lines between the `if` and the `end`
3. Indent the code on the lines btween by pressing `tab` so that it's visually clear what's inside the `if` statement

#### Multibranch if statements

1. We can also have **multibranch** `if` statements, where we specify fallback conditions to check and code to execute if the first condition is falsy
2. There's no space in the `elsif` keyword and that there is **no `e` in the middle** of the `elsif` keyword.
3. The conditions are checked in top-down priority, so even if more than one is true, whichever one is first has its branch exceuted,a dn the rest are ignored
4. If none are true, the final `else` fallback branch is executed, but you don't have to have one if you don't want one
5. Inside a branch of an `if` statement, you can have as many lines of code as you want - and you can even have whole other multi-branch if statements, if that's what you need
6. Try to indent the code within each branch with `tab`, especially if you have multiple nested `if` statements within one another 

#### truthiness and falsiness

1. We say "truthy" and "falsy" instead of just `true` and `false` because most Ruby expressions return values other than `true` or `false`.
2. *Any* expression can appear next to an `if`, and some will cause the code inside the `if` statement to execute (these values are known as "truthy") and some will not (these are "falsy")

#### Comparisons

1. It turns out that **only `false` and `nil` are falsy**. *All* other objects in Ruby are truthy - even `0`, `""`, and `[]`

#### Equivalence vs assignment

1. The **equivalence operator** (`==`) is two equal signs - and the variable assignment operator (`=`) is one equal sign

#### Combining conditions with AND and OR

1. The **logical operators `&&` (AND) and `||` (OR)** allow you to combine expressions

        pp 3.odd? && 4.even?    =>  true
        pp 3.odd? && 4.odd?     =>  false
        pp 3.even? && 4.odd?    =>  false
        pp 3.odd? || 4.even?    =>  true
        pp 3.odd? || 4.odd?     =>  true
        pp 3.even? || 4.odd?    =>  false
2. Both camparisons have to be true in order for the whole statement to be true when combined with `&&`; either one being true is sufficient for `||`