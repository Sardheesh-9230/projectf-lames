 Description of the FLAMES Game

FLAMES is a popular game played by many to find out the nature of the relationship between two people based on their names. The acronym FLAMES stands for:
- *F*riendship
- *L*ove
- *A*ffectionate
- *M*arriage
- *E*nemies
- *S*iblings

The game involves eliminating common letters between the two names and counting the remaining letters. This count is then used to iteratively remove letters from the acronym "FLAMES" until one letter is left, which determines the relationship.

 Code Explanation

Here's a detailed explanation of the provided code:

1. Importing Turtle Graphics:
   python
   import turtle
   

2. Function to Remove Matching Letters:
   This function takes two names, converts them to lowercase, and removes the common characters between them.
   python
   def remove_matching_letters(name1, name2):
       name1 = name1.lower()
       name2 = name2.lower()
       for char in name1[:]:
           if char in name2:
               name1 = name1.replace(char, '', 1)
               name2 = name2.replace(char, '', 1)
       return name1, name2
   

3. Function to Calculate FLAMES Result:
   This function calculates the FLAMES result by removing letters from "FLAMES" based on the remaining count of letters from the names.
   python
   def flames_result(name1, name2):
       relation = "FLAMES"
       result_map = {
           'F': "Friendship 🤝",
           'L': "Love ❤",
           'A': "Affectionate 😊",
           'M': "Marriage 💍",
           'E': "Enemies 😡",
           'S': "Siblings 👨‍👩‍👧‍👦"
       }
       name1, name2 = remove_matching_letters(name1, name2)
       count = len(name1) + len(name2)
       if count == 0:
           return "Names are identical. Please enter different names."
       flames_index = 0
       while len(relation) > 1:
           flames_index = (flames_index + count - 1) % len(relation)
           relation = relation[:flames_index] + relation[flames_index + 1:]
       return result_map[relation]
   

4. Function to Display Result with Turtle Graphics:
   This function uses Turtle graphics to display the relationship result.
   python
   def display_result_with_turtle(name1, name2, relationship):
       screen = turtle.Screen()
       screen.setup(width=800, height=600)
       screen.bgcolor("white")
       
       pen = turtle.Turtle()
       pen.hideturtle()
       pen.penup()
       
       # Clear previous drawings
       pen.clear()
       
       # Display emoji
       emoji = relationship.split()[1]
       pen.goto(0, 0)
       pen.write(emoji, align="center", font=("Arial", 250, "normal"))
       # Display the relationship name
       pen.goto(0, -250)
       pen.write(relationship, align="center", font=("Arial", 18, "normal"))
       
       # Display the names
       pen.goto(0, -300)
       pen.write(f"{name1} ❤ {name2}", align="center", font=("Arial", 18, "normal"))
       
       turtle.done()
   

5. Main Execution Block:
   This is the entry point of the script. It prompts the user to enter two names, calculates the relationship, and displays the result using Turtle graphics.
   python
   if __name__ == "__main__":
       print("Welcome to the FLAMES game!")
       name1 = input("Enter the first name: ")
       name2 = input("Enter the second name: ")
       
       

Step-by-Step Breakdown

1. User Input:
   - The user is prompted to enter two names.
   
2. Removing Matching Letters:
   - The remove_matching_letters function removes common characters from both names.
   
3. Calculating FLAMES Result:
   - The flames_result function calculates the result by iteratively removing letters from "FLAMES" based on the count of remaining letters from the names.
   
4. Displaying Result with Turtle:
   - The display_result_with_turtle function uses Turtle graphics to display the relationship emoji and text on the screen.

This code effectively combines the logic of the FLAMES game with a graphical display using Turtle, making it both functional and visually appealing.
