import turtle
import time
import math

# Set up the screen
screen = turtle.Screen()
screen.bgcolor("black")

# Set up the turtles
loading_turtle = turtle.Turtle()
loading_turtle.shape("circle")
loading_turtle.speed(0)
loading_turtle.penup()

text_turtle = turtle.Turtle()
text_turtle.color("white")
text_turtle.penup()
text_turtle.hideturtle()

# Draw a circle at a specific position with RGB color
def draw_circle(x, y, r, g, b):
    loading_turtle.goto(x, y)
    loading_turtle.pendown()
    loading_turtle.color(r, g, b)
    loading_turtle.circle(10)
    loading_turtle.penup()

# Display the loading percentage
def display_text(percent):
    text_turtle.clear()
    text_turtle.goto(0, -70)
    text_turtle.write(f"Loading {percent}%", align="center", font=("Arial", 16, "normal"))

# Animation loop
def loading_animation():
    radius = 50
    for i, angle in enumerate(range(0, 360, 10)):
        x = radius * math.cos(math.radians(angle))
        y = radius * math.sin(math.radians(angle))
        r = (angle % 255) / 255.0
        g = ((angle + 85) % 255) / 255.0
        b = ((angle + 170) % 255) / 255.0
        draw_circle(x, y, r, g, b)
        percent = int((i + 1) / 36 * 100)
        display_text(percent)
        time.sleep(0.1)
        loading_turtle.clear()
        if percent >= 100:
            break

    # Display final message
    text_turtle.goto(0, -100)
    text_turtle.write("Loading Complete!", align="center", font=("Arial", 16, "normal"))

# Hide the turtle
loading_turtle.hideturtle()



# Run the loading animation
loading_animation()

# Keep the window open
screen.mainloop()
