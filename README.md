from turtle import *
import colorsys
import math

speed(0)  # Cambiado a la máxima velocidad para evitar un valor impráctico
bgcolor("black")

def draw_stem():
    # Dibuja el contorno del tallo
    penup()
    goto(0, -400)  # Comienza en la base de la flor
    pendown()
    color("darkgreen")  # Color del contorno
    width(50)  # Grosor del contorno
    
    # Dibuja el contorno del tallo
    setheading(90)  # Apunta hacia arriba
    forward(400)  # Dibuja una línea hacia arriba

    # Dibuja el relleno del tallo
    penup()
    goto(0, -400)  # Vuelve a la base
    pendown()
    color("green")  # Color del relleno
    width(40)  # Grosor del relleno (más delgado que el contorno)
    
    setheading(90)  # Apunta hacia arriba
    forward(400)  # Dibuja una línea hacia arriba

def draw_single_petal():
    penup()
    goto(20, -380)  # Posiciona la tortuga en el punto de inicio del pétalo
    pendown()
    
    # Dibuja el contorno del pétalo
    color("darkgreen")  # Color del contorno
    width(5)  # Grosor del contorno
    begin_fill()
    
    # Dibuja un solo pétalo
    rt(90)
    circle(100, 90)  # Dibuja un cuarto de elipse
    lt(90)
    circle(100, 90)  # Dibuja el otro cuarto de elipse
    rt(180)

    end_fill()  # Termina el relleno
    
    # Dibuja una línea divisoria en el pétalo
    penup()
    goto(20, -380)  # Regresa al punto inicial
    pendown()
    color("black")  # Color de la línea divisoria
    width(2)  # Grosor de la línea divisoria
    setheading(45)  # Orienta hacia arriba
    forward(900)  # Dibuja la línea divisoria a través del pétalo

# Llama a las funciones para dibujar el tallo y el pétalo
draw_stem()
draw_single_petal()

# Genera los pétalos de la flor
goto(30,-30)
h = 0

for i in range(15):
    for j in range(18):
        c = colorsys.hsv_to_rgb(0.125, 1, 1)
        color(c)
        rt(90)
        circle(200 - j * 6, 90)
        lt(90)
        circle(200 - j * 6, 90)
        rt(180)
    circle(40, 24)

# Genera la parte central de la flor
color("black")
shape("turtle")
turtlesize(1, 1, 2)
fillcolor("brown")
phi = 137.508 * (math.pi / 180.0)

for i in range(200):
    r = 4 * math.sqrt(i)
    theta = i * phi
    x = r * math.cos(theta)
    y = r * math.sin(theta)
    penup()
    goto(x, y)
    setheading(i * 137.508)
    pendown()
    stamp()

# Colocar el primer texto
penup()
goto(0, 300)
color("red")
write("Mientras yo esté, no vas a ser espectadora", align="center", font=("Arial", 10, "bold"))

# Colocar el segundo texto en una ubicación diferente
goto(0, -350)  # Ajusta las coordenadas según lo necesites
write("Te amo Steysi", align="center", font=("Arial", 12, "bold"))

pendown()

done()
