[&lt; Previous chapter](./INTRO_1.md)

## More about native functions

With all we know so far let's translate few Python snippets:

```python
name = "Jim"
print(name)
```

In rye this becomes code below. Notice the set-word instead of equals and lack of parenthesis after function call.

```factor
name: "Jim"
print name
```

Here we make a list, join items of it with a separator and print the result.

```python
names = [ "Jim", "Jane" ]
print(", ".join(names))
```

In rye, we make a _block_ (notice the lack of commas) then we join and print the result.

```factor
names: { "Jim" "Jane" }
print join names ", "
```

If you were a lisper, second line would look like this:

```factor
(print (join names ", "))
```

If you were in ptyhon or javascript it would be written like this:

```factor
print(join(names, ", "))
```
As we see Rye doesn't use parenhesis for function calls. Each word that is a function evaluates and "consumes" as much values 
to the right as it needs. That's why in Rye all functions must accept a fixed numbers of arguments.

## _Do_ those blocks again

We used an list above and called it a block. As a python list, rye block can hold different types of values. Any types of values:

```python
some_list = [ "Jim", "Jane", 33, 12.5 ]
```

```factor
some-block: { "Jim" "Jane" 33 12.5 }
```

But remember, rye has 29 types of values, one of them, absolutely equal to the other values are words.

```factor
a-block: { print join names ", " }
```
So we have a _list_ that looks like code. So what good is this now? Well, we have this __do__ native function that _does_ a block.

```factor
do a-block
Jim, Jane
```
This looks similar to python's or Javascript's __eval__ function. There is a major difference though, those two evaluate a __string__
that looks like javascript. Here we _do_ the already parsed, loaded and "alive" __rye values__.

In fact, there is no difference in evaluation of the code we wrote so far and the code inside _a-block_. And the _do_ we called is no
differnt that the _do_ that does all our code.

```factor
do {
  do {
    names: { "Jim" "Jane" }
    do {
      do a-block
      Jim, Jane
    }
  }
} // .....
```

> It's like you would have a python's lists and your code is also just a python's list.

That quote from the first chapter about all Rye here being the _Do dialect_ makes a little more sense now, but more still later.

[&lt; Previous chapter](./INTRO_1.md) - [Next chapter&gt;](./INTRO_3.md)