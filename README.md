# sp24-lab9
Materials for week 9 lab in CS-370, which includes Ch. 16 "Object Persistence" adapted from [Software Design by Example](https://third-bit.com/sdxpy/) by Greg Wilson.

_March 26, 2024_

Organization:
* SDX-ch16: The code files for the _SDX Ch. 16_ activity (as downloaded directly from the book website, unmodified) 

## Team Members for Part 1
Molly Halverson

## Team Roles for Part 1
Who will start out as
* DRIVER: Molly
* NAVIGATOR: Navigator's name

You will switch halfway through this activity.

## Part 1 Documentation

Write your answers to the questions below.

* What were the main ideas from SDX chapter 16?
Implementing version control using a framework or a built-in module. 

* What questions did you have about the material in the chapters? What did you find confusing?
I found the section about aliasing to be confusing. 

### Exercise 0: Running the tests

Run the tests in all three test modules. (I've added some code to make this feasible.) Verify that all tests pass.

### Exercise 1: Testing objects.py

There is a glaring omission in the given code:a
There is no test module for `objects.py`! 

Copy `test_builtins.py` to a new file named `test_objects.py`. 
Then modify it to test `objects.py` instead ofa` builtins.py`. 
(Make sure you add the new file to your git repositiory.)

I thought of two strategies. Implement whichever you prefer:

1. Adapt each of the given tests to use the object-oriented interface presented by `objects.py`. 
2. Add convenience methods save and load to `objects.py`. 

After doing this exercise, explain the strategy you chose, and why.

### Exercise 2: Refactoring `SaveObjects.save`

In `objects.py`. find the implementation of the save method.
Refactor for understandability by renaming a variable and introducing an explaining variable. 
Run the corresponding test module to verify that your refactorings didn't break anything.

After doing this exercise, briefly explain what you changed.
I changed the "thing" parameter to "object". I also added the explanatory variable and called it "save_method" so it's easier to tell which method is being used to save the object.

### Exercise 3: Understanding code

Answer the following questions:

1.  When we create an alias marker, why is there a colon at the end of the line 

        alias:12345678:

    (Hint: Look at the implementation of `LoadObjects.load`.) 
    It looks like the ':' at the end makes sure that the value portion is still included as an empty string in the 'fields' list if it is empty. The consistency of the colon helps with parsing since it indicates where everything starts and ends.

2.  Why doesn’t `LoadAlias.load` calculate object IDs? 
    Why does it use the IDs saved in the archive instead?
    By using the IDs saved in the archive, you ensure the objects are loaded with the same IDs they were saved with. Recalculating an ID may present issues if the calculation method is different than the way it was calculated when saving. The ID sounds like it may contain important information, so it's best to use the same ID name for each object instead of possibly changing it during calculation.

### Exercise 4: Strings

Modify the framework so that strings are stored using escape characters
like `\n` instead of being split across several lines.

I suggest doing this in `objects.py`. 
Use test-driven development:
Start by changing the tests in `test_objects.py` to use the new string format. 
The tests should now fail.  You will know you have correctly implemented this change when the tests pass again.

### Exercise 5: Versioning

We now have several versions of our data storage format. 
Early versions of our code can’t read the archives created by later ones, 
and later ones can’t read the archives created early on 
(which used two fields per line rather than three). 
This problem comes up all the time in long-lived libraries and applications, 
and the usual solution is to include some sort of version marker 
at the start of each archive to indicate what version of the software 
created it (and therefore how it should be read). 
Modify the code we have written so far to do this.

