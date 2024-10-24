<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/screenshot_1.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name       | value          |
   | ----------              | ---------- | -------------- |
   | built-in primitive type | dimmed          |  True             |
   | built-in composite type | WHITE      | 255, 255, 255  |
   | user-defined type       | Smiley          |  _             |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type                    |
   | ------------             | ----------------------- |
   | self.pixels              | list|
   | A member of self.pixels  | tuple                       |
   | self                     | instance of the class                       |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File       | First line  | Line range  |
   | ------------ | ---------- | ----------- | ----------- |
   |  sequence    |smiley.py   | 15           | 2           |
   |  selection   | sad.py     | 26           | 4           |
   |  iteration   | happy.py   | 21           | 2           |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example |
   | ----------------------- | ----- | --------|
   | int                     | true     | sad.py 15  `mouth = [49, 54, 42, 43, 44, 45]` *we use list of *ints* here to define the coordinates of the mouth*|
   | float                   | true     | happy.py 33 - `delay=0.25` |
   | str                     | false    | `my_string = "lol string"`          
   | bool                    | true     | smiley.py 28 - `dimmed=True`|

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> class variable: *WHITE = (255, 255, 255)*. Class vars are shared by all instances because it represents the color of the smiley(every smile should have its color).

> instance variable: *self.pixels = [O, Y, Y, ...*. These are unique to each instance of the class.

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > The purpose of a constructor is to initialize an object's attributes when it is created.
   > In this case 4 attributes are being initialized.


   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > In `happy.py`, `super()` is used to get the parent class object. Calling `super().__init__()` then runs the constructor of the parent class.

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:
   
> PEP 8.
> SenseHat likely follow the same code style, as deviating from the official standard can make code harder to read.

2. List three aspects of this convention you see applied in the code.

> - snake case for methods and variables
> - 4 spaces for indentation
> - Constants use an uppercase single letter, word

3. Give two examples of organizational documentation in the code.

>  *"""
>  Draws the mouth feature on a smiley
>  """*
>
>  ```# We have encapsulated the SenseHat object```

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s) |
| ---------- | ------------- | ---------------- |
| Smiley   | Super           | -    |
|   Sad      |   Sub         |      Smiley         |
|   Happy      |   Sub         |      Smiley         |
|   Blinkable      |   Super         |      ABC       |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction hides complex implementation details and exposes only the necessary functionalities to the user. The class Blinkable is an abstraction. It provides a method blink, but without implementation. The class Happy, which inherits from both Smiley and Blinkable, can use the blink method without needing to know its internal workings, focusing only on its behavior.

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> The process of deriving from base classes is called *inheritance*.
> In this project, inheritance allows the Happy class to extend the functionality of both the Smiley class (which defines the smiley face representation) and the Blinkable abstract class (which provides the blinking behavior). This promotes code reuse, simplifies the design, and allows Happy to exhibit both smiley and blinking characteristics without needing to duplicate code.

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > `Happy` is blinkable, so `happy` inherits from both `Smiley` and `Blinkable`.
   > Moreover, they have different pattern of mouth (list `mouth`).
   
2. What are the key similarities?
   > Both of them use *draw_mouth* and *draw_eyes* methods.
   > Both of them have the same method *draw_eyes*.
3. What difference stands out the most to you and why?
   > list `mouth` in *draw_mouth* has another patter of mouth.
   > `happy` inherits from both `Smiley`, whereas `Blinkable` inherits just from `Smiley`. 
4. How does this difference affect the functionality of these classes
   > Classes have different lists of `mouth` in the draw_mouth method, so the method draws different mouths accordingly. 
   >

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > `Smiley`, `Sad`, `Happy`
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > `Smiley`
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > Encapsulation hides the internal working of a class to protect data and simplify it’s usage. In `sense_hat.py`, encapsulation hides the details of how the SenseHAT LED matrix work, including methods and properties like `_set_pixels` and `_low_light`. The user only need to use simple methods, such as `set_pixels`, without knowing all internal details. For example, `set_pixels` uses a queue to change pixel colors without expose how it works. Similarly, low_light is managed by a property method, letting users to turn on dimming without handling complex implementation. This encapsulation make the SenseHAT class safer and more easy to use.
   >

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> No. Otherwise, he would put blink in the base(parent) class.

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> No `blink` is an abstract method, so it will be implemented in any class that inherits from Blinkable. This allows each class to implement blink in its own way.
>

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> In this case, polymorphism means that the blink method can be called on both `Happy` and `Sad` classes, even though they are different classes.
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> As `Blinkable` class has `blink` method, it allows any subclass that inherits from it to access this method. Declaring the method in the abstract class is crucial, as it empowers each derived class to implement its own version of the blink method.
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

   ```python
   def blink(self, delay=0.25):
       pass  # Replace 'pass' with your implementation
   ```

2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![Sad Smiley Blinking](screenshots/sad_blinking.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > Apart from modifying `main.py`, I had to import `time` in `sad,py` to implement a delay in the blink method. Aslo I changed the delay to 0.5 sec in the method `blink`.

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > `Blinkable` is an abstract class as it inherits from ABC. An abstract class is designed to be implemented by other classes. 

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > `Abstract Class`

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Polymorphism is achieved by implementing abstract methods within subclasses.

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > I can give the `Sad` a blinking feature similar to `Happy` without using `Blinkable` by implementing a `blink` method directly in the `Sad` class. This approach allows `Sad` to have its own blinking behavior, mimicking `Happy` without relying on inheritance from `Blinkable`.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  >  [Duck Typing](https://en.wikipedia.org/wiki/Duck_typing) This approach means that the specific type or class of an object doesn’t matter; only the properties and methods the object has are important. In other words, when working with an object, its type is not checked. Instead, its properties and methods are examined. Python is a dynamically typed language, where an object doesn’t need to explicitly declare its type. In a statically typed language, passing an unrelated type would result in a compiler error.


  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > In `smiley.py` lines 5 - 9. `WHITE`, `GREEN`, `RED`, `YELLOW`, `BLANK`
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > Tuples with 3 integers. No they are not expected to change because they are `constants`.
     3. Add the color blue to the appropriate class using the appropriate format and values.
         > BLUE = (0, 0, 255)

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > In `Smiley`, `Sad` and `Happy`

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > In `smiley.py` line 15 -> by changing variable `Y` -> `Y = self.YELLOW` to `Y = self.GREEN`

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](screenshots/bulk_rename.png)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
