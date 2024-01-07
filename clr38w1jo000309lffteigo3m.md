---
title: "Python Functions & Logic via Adventure Game - Beginner's Guide"
seoTitle: "Python Functions & Logic via Adventure Game - Beginner's Guide"
seoDescription: "Learn Python basics through a fun text-based game! This guide makes functions and logic easy and engaging for beginners."
datePublished: Sun Jan 07 2024 08:41:39 GMT+0000 (Coordinated Universal Time)
cuid: clr38w1jo000309lffteigo3m
slug: python-functions-logic-via-adventure-game-beginners-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704607472139/002c8ae7-5d81-4284-9c59-20303810eaef.jpeg
tags: tutorial, functions, programming-blogs, python, projects, fundamentals, beginner, learning, game-development, tutorial-hell, control-flow, text-based-adventure-game

---

Have you ever found yourself frustrated with the endless tutorial videos and boring textbooks while learning Python. You might be stuck in a rut known as tutorial hell. But don't give up just yet! There is a unique and fun way to learn these vital Python concepts. Your best bet would be to build projects. And what better way to learn Python functions and logic than to make a text-adventure game.

functions and logic?

Before we dive into the code, let's learn some theories. Specifically, the importance of functions and logic. Without understanding these concepts, you can't build the structure of your game."

but first we need to know some stuff.

# The Theories

I know it's scary, but you can't deny that theory is important. You have to at least know what a function is and what logic means before jumping into it. So, let me give you a brief overview.

## Function

Have you ever seen a popcorn machine? A Function is like a Popcorn Machine. The mechanism is really simple. You put in raw corn (inputs), the machine does its magic (processing), and then out comes popcorn (output). Similarly, in programming:

1. **Input**: This is the data you provide to the function. In Python, these are known as arguments or parameters. They are the data you 'feed' into your function. For example, if you have a function that adds two numbers, the numbers you want to add are the inputs.
    
2. **Processing**: This is where the magic happens. This is the set of instructions that the function performs on the input. In our popcorn machine example, this would be the heating and popping of the corn.
    
3. **Output**: Just as our popcorn machine gives us popcorn, a function gives back data, be it a number, text, list, or something else. It's the 'result' of your function's processing.
    

Let's see a simple example in Python:

```python
def function_name(parameter1, parameter2):
    result = parameter1 + parameter2
    return result

# Using the function
sum = add_numbers(5, 3)
print("The sum is:", sum)
```

In this example:

* `function_name` is the name of the function. we initialize it by adding `def` in the start.
    
* `parameter1` and `parameter2` are the inputs (parameters).
    
* The processing part is `result = parameter1 + parameter2`.
    
* `return result` is the output of the function.
    

When you call `function_name(5, 3)`, you're providing 5 and 3 as inputs. The function processes these numbers (adds them) and returns the result, which is 8 in this case. We will understand it better when we actually make the game.

Remember, functions are essential because they help you organize your code by splitting it into different sections. This makes your code more readable and maintainable. You can call the same function multiple times with different inputs, just like how a popcorn machine can be used to pop different batches of corn.

## Logic

*Let me tell you a story.*

> *On a seemingly ordinary morning, I found a suspicious-looking piece of cake beside my bed.* *I faced a decision: should I throw it away or take a risky bite? I decided to indulge my curiosity and ended up with a terrible stomachache. If only I had chosen differently and tossed that cake in the trash, I could have avoided the suffering and those hefty medical bills.*

The point of this little story? Life is full of choices, and our world often revolves around the decisions we make. Interestingly, the world of programming is no different. In the realm of code, we find ourselves constantly making choices that determine the flow of our programs.

Logic is a fundamental concept in programming that enables us to make decisions and execute specific code blocks based on certain conditions. Just like my choice with the mysterious cake, in Python, we use logic to make choices within our code.

**The Decision-Making Tools**

*In Python, we have several tools at our disposal for controlling the flow of our code:*

**Conditional Statements (if, elif, else)**:

* `If` block allows us to set a condition. If the condition is True, the code executes and `elif` let us put an alternate condition. `else` block runs when all other conditions return false.
    
* Much like choosing to eat or discard the cake, conditional statements allow us to evaluate conditions. *For example:*
    

```python
if cake_is_suspicious:
    throw_away_cake()
else:
    take_a_bite()
```

As we embark on creating our text adventure game, logic will be our trusty guide through the twists and turns of the story. We'll use conditional statements to determine the outcome of choices the player makes.

## Making the Game

We are going to make the game as basic and small as possible. So that you can make the rest yourself. The basic premise is like this -&gt;

> You are an Adventurer. And in one of your adventures, you face a choice there is one door where a tiger is behind it or a door that is lit on fire. The story will progress based on your choice.

**That's it**. I intentionally didn't put any big story or a full-fledged game. So that you can make it yourself.

1. **Create a New Python File**:  
    Open your text editor or IDE (like PyCharm, or VSCode) and create a new file. Save it as `simple_adventure_`[`game.py`](http://game.py).
    
2. **Define the Starting Room**:  
    This is where your game will begin. We'll create a function for this room.  
    we will do it by using the `def` key. Let's name it start\_room.
    
    ```python
    def start_room():
        print("You find yourself in a compact room with two distinct doors. 
    To the north, there's a door with a lion behind it, and another door that is ablaze, its flames stirring a sense of fear in you.")
        choice = input("Do you choose the 'lion' door or the 'fire' door? (lion/fire) ")
    ```
    
    This function prints a text `You find yourself in a compact room with two distinct doors. To the north, there's a door with a lion behind it, and another door that is ablaze, its flames stirring a sense of fear in you.` Then asking asks user for an Input with the `input()` keyword. Then value of the input is then stored inside a variable named choice.
    
3. **Using logic to evaluate the choice.**
    
    ```python
    if choice == 'lion':
        lion_room()
    elif choice == 'fire':
        fire_room()
    else:
        print("Not a valid choice. Try again.")
        start_room()
    ```
    
    If the choice is **lion,** we start the `lion_room()` function and if the choice is **fire,** we start the `fire_room()` function or else we start the `start_room()` function again.
    
4. **Create the Lion Room Function**:
    
    ```python
    def lion_room(): 
        print("As you open the door, you see a lion. Luckily, it's just a friendly cat. You win!") # Game ends here, or you can add more choices or paths
    ```
    
5. **Create the Fire Room Function**:
    
    ```python
    def fire_room():
        print("You bravely open the fiery door, only to realize it's a harmless hologram. You win!")
    # Game ends here, or you can add more choices or paths
    ```
    
6. **Initiate the Game**:  
    At the end of the file, call the `start_room` function to start the game:
    
    ```python
    start_room()
    ```
    
7. **Run Your Game**: Save your file and execute it in your Python environment. The game will start in the starting room, prompting you to make a choice between the lion and the fire door.
    

Here is the entire code.

```python
def start_room(): 
    print("You find yourself in a compact room with two distinct doors. To the north, there's a door with a lion behind it, and another door that is ablaze, its flames stirring a sense of fear in you.") 
choice = input("Do you choose the 'lion' door or the 'fire' door? (lion/fire) ") 
    if choice == 'lion': 
        lion_room() 
    elif choice == 'fire': 
        fire_room() 
    else: 
        print("Not a valid choice. Try again.") 
        start_room() 

# Define the lion room function def lion_room(): 
def lion_room():
    print("As you open the door, you see a lion. Luckily, it's just a friendly cat. You win!") 
    # Game ends here, or you can add more choices or paths 

# Define the fire room function 
def fire_room(): 
    print("You bravely open the fiery door, only to realize it's a harmless hologram. You win!")
    # Game ends here, or you can add more choices or paths 

# Start the game 
start_room()
```

I won't be giving you any more instructions. If you understand this much. You will be able to build the rest yourself.