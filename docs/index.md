# Assignment07 Error Handling & Pickling, 12/1/2020
**Dev:** *Chris Messmann*  
## Introduction
Assignment 07 are some simple examples of the ‘try-except’ block and pickling works.   The program presents the user with a menu of 3 options: (1.) Run Error Handling Demo; (2.) Run Pickling Demo (3.) Exit Program.  The ‘try-except’ demo shows how shows the user an example of a custom ‘try-except’ and another example of a built-in IO ‘try-except’ block.  The program itself utilizes a similar structure of classes and functions as was done in Assignment06.
```
# ---------------------------------------------------------------------------- #
# Title: Assignment 07
# Description: This program demonstrates the concepts of error
#              handling and pickling.  The user will be presented
#              a menu with 3 options: (1) Error Handling Demo;
#              (2) Pickling Demo; (3) Exit Program.
# ChangeLog (Who,When,What):
# Chris Messmann,11/29/20,Created started script
# Chris Messmann,12/1/20, Finished error handling and pickling demo
# ---------------------------------------------------------------------------- #

# Data ---------------------------------------------------------------------- #
# Declare variables and constants
strChoice = ""  # Captures the user option selection
strerror_handling_selection = ""  # Captures the user error_handling_selection data
strPriority = ""  # Captures the user priority data
strStatus = ""  # Captures the status of an processing functions
Strvalue = "" # Captures users value in error handling demo 1
StrFile = "" # Placeholder for user entered file name in error handling demo 2
Strdata = "" # Placeholder for data sent to pickle processing functions
Strnumberdata = "" # Placeholder for the number of items being loaded into pickle dump
item = "" # Used in the counter in the pickle dump demo


# Processing  --------------------------------------------------------------- #
class Processor:
    """  Performs Processing error_handling_selections """

    @staticmethod
    def error_processing_demo1(value):
        try:
            quotient = value / 0
            print(quotient)
        except:
            print("You can't divide by 0")

    @staticmethod
    def error_processing_demo2(unavailable_file):
        try:
            open(unavailable_file)
        except IOError as e:
            print(e, e.__doc__, sep='\n')

# Presentation (Input/Output)  -------------------------------------------- #
class IO:
    """ Performs Input and Output error_handling_selections """

    @staticmethod
    def print_menu_error_handling_selections():
        """  Display a menu of choices to the user

        :return: nothing
        """
        print('''
        Menu of Options
        1) Run Error Handling Demo
        2) Run Pickling Demo
        3) Exit Program
        ''')
        print()  # Add an extra line for looks

    @staticmethod
    def input_menu_choice():
        """ Gets the menu choice from a user

        :return: string
        """
        try:
            choice = str(input("Which option would you like to perform? [1 to 3] - ")).strip()
            print()  # Add an extra line for looks
        except Exception as e:
            print("That choice is out of range")
        return choice

    @staticmethod
    def input_press_to_continue(optional_message=''):
        """ Pause program and show a message before continuing

        :param optional_message:  An optional message you want to display
        :return: nothing
        """
        print(optional_message)
        input('Press the [Enter] key to continue.')

    @staticmethod
    def error_handling_demo1():
        print("We're going to demo how structured error handling works.")
        print("Python has a variety of ways it responds to errors by utilizing 'try-except' blocks.")
        print("The first example will demo a custom 'user friendly' try-except response. ")
        value = input("Enter a number and I will try and divide it by 0: ")
        return value


    @staticmethod
    def error_handling_demo2():
        print("Python has pre-built in try-except blocks for commonly occurring errors")
        print("This second example will demo an already built in try-except response to an IO Error.")
        print()
        unavailable_file = input("Type in any file name and I will try to open it: ")
        return unavailable_file

    @staticmethod
    def pickle_dump_demo():
        print("Data can be saved in binary format instead of just 'plain' text. In Python, this")
        print("technique is called pickling. Storing data in a binary format can obscure the file's")
        print("content and may reduce the file's size.")
        print("This demo will explore how pickling works as an alternative to saving a text doc.")

        import pickle

        # take user input to take the amount of data
        number_data = int(input('Enter the number of data : '))
        data = []


        #take input of the data
        for i in range(number_data):
            raw = input('Enter data ' + str(i) + ' : ')
            data.append(raw)

        # open a file and dump the data
        file = open('pickle_file', 'wb')
        pickle.dump(data, file)
        file.close()

        # open a file, and load the data
        file = open('pickle_file', 'rb')
        data = pickle.load(file)
        file.close()
        
        print('Showing the pickled data:')

        cnt = 0
        for item in data:
            print('The data ', cnt, ' is : ', item)
        cnt += 1

# Main Body of Script  ------------------------------------------------------ #

while (True):
    # Step 1 - Display a menu of choices to the user
    IO.print_menu_error_handling_selections()  # Shows menu
    strChoice = IO.input_menu_choice()  # Get menu option

    # Step 2 - Process user's menu choice
    if strChoice.strip() == '1':  # Run error handling demo
        Strvalue = IO.error_handling_demo1()
        Processor.error_processing_demo1(Strvalue)
        IO.input_press_to_continue(strStatus)
        StrFile = IO.error_handling_demo2()
        Processor.error_processing_demo2(StrFile)
        IO.input_press_to_continue(strStatus)
        continue  # to show the menu

    elif strChoice == '2':  # Run pickling demo
        Strdata = IO.pickle_dump_demo()
        IO.input_press_to_continue(strStatus)
        continue  # to show the menu

    elif strChoice == '3':  # Exit Program
        print("Goodbye!")
        input("Enter to Exit", )
        break  # and Exit
        
#### Listing 1a
![Results of Listing 1a](https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig1a-ErrorHandling1.png "Results of Listing 1a")
#### Listing 1a. The results of Listing 1a

#### Listing 1b
https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig1b-ErrorHandling2.png
#### Listing 1b. The results of Listing 1b

#### Listing 1c
https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig1c-Pickling.png
#### Listing 1c. The results of Listing 1c

#### Listing 2
https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig2-CommandWindow.png
#### Listing 2. The results of Listing 2

#### Listing 3
https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig3-ShellWindow.png
#### Listing 3. The results of Listing 3

#### Listing 4
https://github.com/Chessmann/ITFnd100-Mod07/blob/main/docs/Fig4-PickleFile.png?raw=true
#### Listing 4. The results of Listing 4
