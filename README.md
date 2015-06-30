# Sorting

Sorting collections of data is a very common task in programming. As a developer, you can imagine being confronted with the need to sort items by price, or emails by their position in the alphabet, for example. There are a number of ways to execute sorting in Ruby. Here's we'll discuss one basic example and learn how to sort a list of words. 

## Dinner Party Example

You are a famous chef hired to cater a dinner party for the President of Programlandia. Mr. President has his quirks and he'd like for you to print the dinner menu by listing the dishes in alphabetical order. Unfortunately, you weren't prepared for this request and you already have a list of dishes that are *not* alphabetized.  

So, we have a program that contains a variable, `dishes`, that points to an array of your delicious dishes: 

```ruby
dishes = ["steak", "apple pie", "vegetable soup"]
```

### Comparing Strings

We need sort the dishes in this array into alphabetical order. We've already learned about comparison operators like `>` and `<` and used them on numbers. These operators work on strings too. If we compare strings using these operators, the comparison operator will look at the first letter of each string and compare their locations in the alphabet. Letters later in the alphabet are considered greater than letters earlier in the aplhabet. For example: 

`"zoo" > "apple"`

Will return 

`true`

## The `.sort` method

In order to sort our list of dishes, we will have to iterate over the array and compare every set of items. So far, when we've iterated with methods like `.each` or `.collect`, we iterate over *one element of the collection* at a time. Now, in order to compare the elements in our array to one another, we need an enumerator that allows us to yield two elements at once. That's where the `.sort` method comes in. 

Let's take a look at a basic example using an array of numbers:

```ruby
array = [7, 3, 1, 2, 6, 5]

array.sort do |a, b|
	a <=> b
end
```

Other enumerator methods like `.each` we call like this: 

```ruby
array.each do |num|
	puts num 
end
```

`.each` starts at the beginning of the array and passes each item, *one at a time*, to the code in the block (code in between `do`, `end`). We see `.each` passing each element of the array to the block here: `|num|`, by placing a placeholder for each element in between these pipes. 

`.sort` is different. It passes elements *two at a time* into the block, and compares those two elements inside the block, via this line `a <=> b`. If `a` is greater than `b`, it will move `b` to the spot in the array *after* `b`. 

Therefore, when we call: 

```ruby
array = [7, 3, 1, 2, 6, 5]

array.sort do |a, b|
	a <=> b
end
```

The first time through the collection, `.sort` passes `7` and `3` into the block and compares them, since 7 is greater than 3, it switches the location of those two elements. If we were to look at the array after going through just one iteration of `.sort`, it would look like this: 

`[3, 7, 1, 2, 6, 5]`

On the second pass through the array, `.sort` yields the next two items to the block, in this case `7` and `1`. It compares them in the same way, makes any necessary changes to the location of the items in the array, and then moves on to the next pair. 

## Sorting our dinner party menu 

Now that we have a better understanding of how the `.sort` method works, let's sort our dinner party menu from the earlier example:

```ruby
dishes = ["steak", "apple pie", "vegetable soup"]

dishes.sort do |a, b|
	a <=> b
end

  => ["apple pie", "steak", "vegetable soup"]
```

We did it! The menu is alphabetized. Now, let's take it a step further. Drop into IRB and copy and paste the following code: 

```ruby
dishes = ["steak", "apple pie", "vegetable soup"]

dishes.sort
```

It should return : `["apple pie", "steak", "vegetable soup"]`. 

Simply calling `.sort` has the desired effect. It implicity executes the code we used in the block in the above example. But now we understand *how* sort works, not just *what* it does. 

**Bonus:** Think about customizing a sorting method. Since `.sort` takes a block, can we tell `.sort` to sort in revers alphabetical order? In other words, can we sort a collection of data from greatest to least? 

## Resources

* [Dot Net Pearls - Sort Ruby](http://www.dotnetperls.com/sort-ruby)
* [Ruby Docs - Array - sort](http://ruby-doc.org/core-2.2.0/Array.html#method-i-sort)










