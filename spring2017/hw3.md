---
layout: homework
title: Homework 3 - Pet Store
---

# Homework 3 - Pet Store

## Introduction

In this homework you will practice

- csv reading
- class dunder functions
- using instance variables
- class specific funtions
- writing a main function

## General Instructions

**This is an individual assignment.**

Collaboration at a reasonable level will not result in substantially similar code. Students may only collaborate with fellow students currently taking CS 2316, the TAs and the lecturer. Collaboration means talking through problems, assisting with debugging, explaining a concept, etc. You should not exchange code or write code for others.

Notes:

- Include a comment with your name and GTID at the top of all Python files.
- *Do not wait until the last minute* to do this assignment in case you run into problems.
- Pay close attention to whether problems require you to print or return the results! Printing instead of returning or vice versa will result in a point deduction.
- Name all functions as specified in the instructions.
- Unless otherwise stated, you can assume inputs will be valid in this assignment (i.e. error checking is not required).
- In a Python module you must define a value (such as a function) before referencing it. So if you call function A from function B, the definition of function A must come before the definition of function B in the file.

## Problem Description

You have decided to open a Pet Store!  However you quickly realize that in order to have a well run pet store you are going to need some sort of inventory system to keep track of all the pets you have for sale and how much money the pet store has. You will create a Pet class that defines the properties of a Pet, then create a Pet Store class that will manage an inventory of Pet objects.  You will also need to be able to populate the Pet Store based on a csv file with information on pets.  

## Solution Description

In this homework you will be writing 2 classes, a method to read in data from a csv file, and a main method to call all of the methods that you write. 

## Doctest

The specifications for each function is given as a [docstring](https://www.python.org/dev/peps/pep-0257/) -- which you should include in your code -- and the types of arguments and return values are given using type hints documented in [PEP 484 -- Type Hints](https://www.python.org/dev/peps/pep-0484/).

Because each function will have a docstring that includes usage examples formatted as Python interactive sessions, you can use [doctest](https://docs.python.org/3/library/doctest.html) to test your code using this command line invocation:


```sh
python -m doctest -v reading-level.py
```

**IMPORTANT**: Do not modify the provided docstrings!

## Code

Create a python file with the following classes

### `Pet`

```Python
class Pet:
    """An object of Pet will have a species, name, age, color, and price.  The
    Pet object should also be able to be printed in an informative manner.
    """
    
    def __init__(self, species, name, age, color, price):
        """Creates a new pet object with the instance attributes of its species,
         name, age, color, and price.

         Parameters:
            self
            species: String
            name: String
            age: Int -- in years
            color: String -- color of the Pet
            price: Int -- price in dollars for someone to buy the pet from your
                store
        """

    def __repr__(self):
        """Create a string representation for each pet created.  This will
        mostly be used when printing out the objects in main, so you may
        write this in any way that conveys all relevant information about the
        Pet

        Parameters:
            self
        """

    def __eq__(self, other):
        """Compares two Pets to test equality.  Pets are equal if their species,
        name, and age are the same.  When checking names, species, and age,
        the code should be case insensitive, so "bill" and "Bill" are the same
        name

        Parameters:
            self
            other: Pet Object -- the second Pet you are comparing to the first

        Usage Examples:
        >>> a = Pet("Dog", "Alex", 6, "Gold", 150)
        >>> b = Pet("Dog", "alex", 6, "gold", 400)
        >>> a == b
        True
        """

    def __gt__(self, other):
        """Comparison function to allow sorting of Pets.  The order for Pets
        is by age, oldest to youngest.  If two Pets have the same age, sort by
        name alphabetically.

        Parameters:
            self
            other: Pet Object -- the second Pet you are comparing to the first

        Usage Examples:
        >>> a = Pet("Dog", "Alex", 8, "Gold", 150)
        >>> b = Pet("Dog", "Todd", 6, "gold", 400)
        >>> a > b
        True

        >>> a = Pet("Dog", "Alex", 6, "Gold", 150)
        >>> b = Pet("Dog", "Todd", 6, "gold", 400)
        >>> a > b
        True
        """
```
### `Pet Store`
```Python
class PetStore:
    """Here you will write the inventory management system for your Pet Store.
    The Pet Store will let you as the owner sell your cheapest pet of a specific
    species, sell all of a specific species, cut the price of a specific species
    in half, or breed two Pets of the same, specified, species.
    """

    def __init__(self):
        """ Initializes a Pet Store object with two instance variables: money
        and inventory.  When the Pet Store first opens, you should start with
        $1000 and a dictionary with the keys "Cat", "Bird", "Dog", and "Snake"
        with the values of each key being an empty list.  This dictionary will
        hold the Pet Store's inventory. As you add Pet's to the Pet Store,
        they will be added to the list that is the value of the key
        corresponding to the Pet's species.  FYI, the test cases will not work
        correctly until this method is complete.  For the test cases to work you
        must name the instance variables money and inventory.

        IF YOU USE DIFFERENT KEYS IN YOUR INVENTORY YOU MAY LOSE POINTS

        Parameters:
            self
        """

    def add_pet(self, pet):
        """Adds a pet to the pet store.  Be sure to add the pet to the correct
        part of the inventory dictionary.

        Parameters:
            self
            pet: Pet Object -- pet to add to your pet store

        Usage Examples:
            >>> ps = PetStore()
            >>> cat = Pet("Cat", "Meowth", 17, "White", 400)
            >>> ps.add_pet(cat)
            >>> ps.inventory["Cat"][0] == cat
            True
        """


    def sell_cheapest(self, species):
        """Sells the cheapest pet of the specified species, increasing the
        Pet Store's money by the price of the pet and removing the pet you just
        sold from the inventory. If there are two pets that are the same price
        and that price is the cheapest of those species, sell the one who's name
        comes first alphabetically.
        If there are no Pets of the specified species in inventory, please
        print a message to the user to let them know.
        Hint: This is not the same sorting as Pet's comparator function

        Parameters:
            self
            species: String -- the species you want to sell

        Usage Examples:
            >>> ps = PetStore()
            >>> cat = Pet("Cat", "Meowth", 17, "White", 400)
            >>> cat2 = Pet("Cat", "James", 10, "Blue", 100)
            >>> ps.add_pet(cat)
            >>> ps.add_pet(cat2)
            >>> ps.sell_cheapest("Cat")
            >>> ps.inventory["Cat"][0] == cat
            True
        """

    def sell_all(self, species):
        """Sells all pets of the specified species. The PetStore's money should
        increase by the price of all the Pets sold.  The PetStore's inventory
        should reflect you no longer own any of that species.
        If there are no Pets of the specified species in inventory, please
        print a message to the user to let them know.

        Parameters:
            self
            species: String -- the species you want to sell

        Usage Examples:
            >>> ps = PetStore()
            >>> cat = Pet("Cat", "Meowth", 17, "White", 400)
            >>> cat2 = Pet("Cat", "James", 10, "Blue", 100)
            >>> ps.add_pet(cat)
            >>> ps.add_pet(cat2)
            >>> ps.sell_all("Cat")
            >>> ps.money == 1500
            True
        """



    def discount(self, species):
        """Cuts the price of all of the specified animals in half.  If the
        resulting price is a float, floor the result so that it is an integer
        If there are no Pets of the specified species in inventory, please
        print a message to the user to let them know.

        Parameters:
            self
            species: String -- the species you want to discount

        Usage Examples:
            >>> ps = PetStore()
            >>> cat = Pet("Cat", "Meowth", 17, "White", 400)
            >>> ps.add_pet(cat)
            >>> ps.discount("Cat")
            >>> ps.inventory["Cat"][0].price == 200
            True
        """

    def breed(self, species, name):
        """Breeds the two oldest animals of the given species.  If there are
        more than two animals that qualify as oldest, sort next by name
        Alphabetically (if you have the following Dogs and their ages: (Bill,7),
        (Marie,8), and (Max, 7), then Marie and Bill would breed, since Bill
        comes before Max alphabetically).  Set the age of the baby as 1, price
        as 500, and the name as specified in the parameter.  The color of the
        baby is the same as the oldest parent, and if both have the same age,
        the color of the parent with the first name alphabetically. Remember to
        add the new baby pet to your inventory.
        If there are less than 2 Pets of the specified species in inventory,
        please print a message to the user to let them know.
        Hint: This is the same sorting as Pet's comparator function

        Parameters:
            self
            species: String -- the species you want to breed
            name: String -- the name of the new baby Pet

        Usage Examples:
            >>> ps = PetStore()
            >>> cat = Pet("Cat", "Meowth", 9, "White", 400)
            >>> cat2 = Pet("Cat", "James", 10, "Blue", 100)
            >>> cat3 = Pet("Cat", "Jessie", 10, "Red", 200)
            >>> ps.add_pet(cat)
            >>> ps.add_pet(cat2)
            >>> ps.add_pet(cat3)
            >>> first_pet_list = ps.inventory["Cat"]
            >>> ps.breed("Cat", "Ash")
            >>> second_pet_list = ps.inventory["Cat"]
            >>> baby = Pet("Cat","Ash", 1, "Blue", 500 )
            >>> first_pet_list.append(baby)
            >>> first_pet_list.sort()
            >>> second_pet_list.sort()
            >>> first_pet_list == second_pet_list
            True
        """
```
### `Populate`
```Python
def populate(self, starting_inventory, store):
    """Initializes the pet store with all the animals in the provided
    CSV file.  The CSV file has a column for every parameter in the Pet
    class.  Use each line in the file to create a Pet and then add it to
    the PetStore class's inventory dictionary.

     Parameters:
         self
         starting_inventory: String -- name of a csv file to get data from
         store: PetStore Object -- the pet store to add the inventory to
    """
```
This function should be outside of any class, and will be called in your main method.  