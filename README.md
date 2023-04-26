# worldwide-racing
a racing game for anyone to use
import random
import time

# Define the game settings
track_length = 1000
num_cars = 5

# Define the class for the cars
class Car:
    def __init__(self, name):
        self.name = name
        self.position = 0

    def move(self):
        self.position += random.randint(1, 6)

# Create a list of cars
cars = [Car("Car " + str(i)) for i in range(1, num_cars + 1)]

# Define the function to print the track
def print_track():
    print("-" * 40)
    for car in cars:
        print("{:<10}{}".format(car.name + ":", "-" * (car.position // (track_length // 40)) + ">"))
    print("-" * 40)

# Define the function to check if a car has won
def check_win():
    for car in cars:
        if car.position >= track_length:
            print("{} has won the race!".format(car.name))
            return True
    return False

# Start the game loop
print("Welcome to the worldwide car racing game!")
print("The race is {} meters long, and there are {} cars.".format(track_length, num_cars))
print("Get ready...")
time.sleep(3)

while True:
    # Move all the cars
    for car in cars:
        car.move()

    # Print the current position of all the cars
    print_track()

    # Check if any car has won
    if check_win():
        break

    # Wait for a short time before moving the cars again
    time.sleep(1)
