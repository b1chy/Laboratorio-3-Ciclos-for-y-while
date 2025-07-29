# Laboratorio-3-Ciclos-for-y-while
Aprendiendo el uso de for y while
import random

while True:
    numero_secreto = random.randint(1, 10)
    intentos = 0
    max_intentos = 5

    print("\n--- ¡Nuevo Juego! ---")
    print("Adivina el número entre 1 y 10. ¡Tienes 5 intentos!")

    while intentos < max_intentos:
        try:
            guess = int(input("Tu número: "))
        except ValueError:
            print("Entrada inválida. Por favor, ingresa un número entero.")
            continue

        if guess == -1:
            print(f"Modo trampa activado: el número secreto es {numero_secreto}")
            continue

        intentos += 1

        if guess == numero_secreto:
            print("¡Correcto! Has adivinado el número.")
            break
        elif abs(guess - numero_secreto) == 1:
            print("¡Casi lo logras! Estás muy cerca.")
        elif guess < numero_secreto:
            print("Demasiado bajo.")
        else:
            print("Demasiado alto.")

    if guess != numero_secreto: # This condition might need adjustment if the game breaks from a correct guess
        # This print statement will only execute if the loop finished without a correct guess.
        # It's better to check if 'guess' is actually the secret number or if attempts ran out.
        if intentos >= max_intentos and guess != numero_secreto:
            print(f"Game Over. Se te acabaron los intentos. El número era {numero_secreto}.")
        # If the user guessed correctly, the previous 'print' for correct guess would have already run.
   
    jugar_otra_vez = input("¿Quieres jugar de nuevo? (s/n): ").lower()
    if jugar_otra_vez == 's':
        # The game loop will restart, re-initializing numero_secreto and intentos.
        print("¡Iniciando un nuevo juego!")
        continue
    else:
        print("¡Gracias por jugar!")
        break
