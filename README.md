# Ruby Hashes - Introduction

## Objectives

Students will learn about Ruby hashes.

## SWBATS

+ HASHES - create
+ HASHES - populate
+ HASHES - access by key
+ HASHES - iterate over keys and values


## Introducing Hashes

So far, we have explored how arrays enable us as programmers to store data and perform complex operations on groups of data. Along with arrays, **hashes** are another core data structure in programming.

A `hash` is easiest described as working the same as a dictionary. Imagine looking up a definition for a word in a dictionary. When you look up a definition, you aren't looking up the _word_ itself, you already know it (i.e. the word is 'flabbergast', and you can easily find out which page it's on). Instead, it is the definition of the word, which you don't know, that you really want:
  - You find the page with the word itself
  - You then look at the definition for the word itself, and have your answer

A Ruby **hash** works just like this. It holds many **keys** (words, in our dictionary example), and associates **values** (definitions) with them. In fact, they work so much like dictionaries that some languages explicitly call them 'dictionaries'.

Let's take a look at how we might create, and begin working with, a hash. Going forward we will build on our Amazon cart example:

## Creating a Hash

Our best client, the Amazon Client Experience Team, needs our services again. It's the mid-1990's, and Amazon's business is a-boomin'. You have joined the team full time and they need to improve their web interface. Now, they want to make sure prices are associated with the item's name. You have a solution which implements a hash:

```Ruby
items = {} # this creates a new empty hash

items["Dazzling Coat"] = 15.0

# Now, we have a hash that looks like the following:
items
# => {"Dazzling Coat" => 15.0}
# The rocket, or '=>' is saying "the key on the left is associated with the value on the right"
# We can also instantiate our hash using the rocket syntax, i.e.:
# items = {"Dazzling Coat" => 15.0}
```

We can also get values extracted directly by using the key. Using the above example, we can now programmatically answer the question: "What is the price of the 'Dazzling Coat'":

```ruby
items["Dazzling Coat"]
# => 15.0
```

To reiterate, we are providing the **hash** `items` with a **key** of `"Dazzling Coat"`, and it is returning the **value** of `15.0`, (which we print with `puts`). We can also pass variables that are associated with values into either the key or the value when adding items:

```ruby
new_item = "Aubergine Gloves"
item_price = 200.0
items[new_item] = item_price

items
# => {"Dazzling Coat" => 15.0, "Aubergine Gloves" => 200.0}
```

## Growing a Hash

**NOTE:** now is a great time to tie back in what we recently learned with the `array.each` method and do a live code-along with the students.

Let's imagine the Amazon team needs to consolidate data that is currently split up into one hash. Propose you have two arrays, one filled with prices and filled with item names. Assuming that the prices and item names line up by index, how would you grow the hash associating **keys** of item names with **values** of prices? Following is a potential solution using `.each`:

```Ruby
prices = [20.0, 15.99, 2.50]
item_names = ["Outrageous Shoes", "Beguiling Socks", "Chrome Laces"]

items = {}

idx = 0
item_names.each do |name|
  items[name] = prices[idx]
  idx += 1
end

# => {"Outrageous Shoes"=>20.0, "Beguiling Socks"=>15.99, "Chrome Laces"=>2.5}
```

**MINI LAB WITH HASHES. CREATING, GROWING, ACCESSING**

## Iterating with Hashes

In programming, iteration (or going through a collection of elements one by one) is an extremely common task. We need to do it with many different data structures, and luckily it isn't limited to only arrays! We can also iterate over a Ruby hash, which has several methods designed specifically to make it easier for us to do just that.

#### Keys and Values

Our Amazon Team has approached us with another deliverable: "Excellent work consolidating the user's item names and prices into a single hash. Going forward, we need to make sure we can still send our different teams the information they require":

  - The marketing team wants a list of the items a user purchases. They don't care about the prices
  - The accounting team needs a record of the total purchase amounts, and they don't care about the names of the items

We have a straightforward solution that will satisfy everyone:

```Ruby
items = {
  "Dazzling Coat" => 15.0,
  "Outrageous Shoes" => 20.0,
  "Beguiling Socks" => 15.99,
  "Chrome Laces" => 2.50,
  "Aubergine Gloves" => 200.0
}

item_names = items.keys # returns an array of all item names
# => ["Dazzling Coat", "Outrageous Shoes", "Beguiling Socks", "Chrome Laces", "Aubergine Gloves"]

prices = items.values # returns an array of all item prices
# => [15.0, 20.0, 15.99, 2.50, 200.0]
```

#### Iterating Over Keys and Values Simultaneously

It's time to provide the final deliverable to the Amazon Team: the ability to iterate over both keys and values at the same time so users can get a 'whole picture' view of their cart:

```Ruby
items.each do |item_name, price|
  puts "Item: #{item_name}"
  puts "Price: #{price}"
  puts ""
end

# Item: Dazzling Coat
# Price: 15.0
#
# Item: Outrageous Shoes
# Price: 20.0
#
# Item: Beguiling Socks
# Price: 15.99
#
# Item: Chrome Laces
# Price: 2.5
#
# Item: Aubergine Gloves
# Price: 200.0
```

**LAB ON HASHES**
