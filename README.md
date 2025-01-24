import turtle
import random
import math

sentences = [
    "عشق تو ، تو قلبم ابدیه",
    "تو دنیای منی",
    "با تو زندگی زیباتره",
    "قلبم برای تو می‌تپه",
    "تو رویای شیرین منی",
    "تو بهترین اتفاق زندگی منی",
    "دوستت دارم بیشتر از همیشه"
]
colors = [
    "red", "pink", "purple", "blue", "cyan", "magenta", 
    "orange", "gold", "yellow", "green", "salmon", "violet", "lightcoral"
]

def draw_heart(color, x, y, sentence):
    turtle.penup()
    turtle.goto(x, y)
    turtle.pendown()
    turtle.color(color)
    turtle.begin_fill()
    for angle in range(0, 360, 5):
        t = math.radians(angle)
        x_heart = 16 * (math.sin(t) ** 3)
        y_heart = 13 * math.cos(t) - 5 * math.cos(2 * t) - 2 * math.cos(3 * t) - math.cos(4 * t)
        turtle.goto(x + x_heart * 10, y + y_heart * 10)

    turtle.end_fill()
    turtle.penup()
    turtle.goto(x, y - 20)
    turtle.color("black")
    turtle.write(sentence, align="center", font=("Courier", 14, "bold"))
    turtle.setheading(0)

# تنظیمات صفحه
screen = turtle.Screen()
screen.bgcolor("white")
turtle.speed(0)  
turtle.hideturtle()

# رسم 10 قلب
for _ in range(10):
    color = random.choice(colors)
    x = random.randint(-300, 300)
    y = random.randint(-300, 300)
    sentence = random.choice(sentences)
    draw_heart(color, x, y, sentence)

turtle.done()  # پایان برنامه
