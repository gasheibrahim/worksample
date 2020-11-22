`Corresponding Sentence`

self points to the instance object itself. Use self when calling an instance object in a class or when calling that instance object.


## Revised

self is a special variable that points to the object that "owns" the currently executing code. Ruby uses self everwhere: For instance variables: @myvar. For method and constant lookup. When defining methods, classes and modules.

In many object-oriented programming languages, this (also called self) is a variable that is used in instance methods to refer to the object on which they are working. Some languages require it explicitly; others use lexical scoping to use it implicitly to make symbols within their class visible.

`Eg: class Cup`
```
  def coffee
    puts self
  end
end
Cup.new.coffee
```
 One practical use for self is to be able to tell the difference between a method & a local variable.
 It’s not a great idea to name a variable & a method the same. But if you have to work with that situation, then you’ll be able to call the method with   `self.method_name.`
 ```
 class Example
  def do_something
    coffee = "variable"
    puts coffee
    puts self.coffee
  end
  def coffee
    "method"
  end
end
```
`Example.new.do_something`
```
# "variable"  => puts coffee
# "method"    => puts self.coffee

## def self.method_name

class Fruits
  def self.buy_mango
    # ...
  end
end
Fruits.buy_mango
```

## Caution: If this explanation does not meet your expectations, needs, or desires , please feel free to ask again. Thank You
