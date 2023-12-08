# Weather-modeling-in-python.
import math

# Function to calculate temperature using the quadratic formula
def calculate_temperature(a, b, c):
  root1 = (-b + math.sqrt(b**2 - 4 * a * c)) / (2 * a)
  root2 = (-b - math.sqrt(b**2 - 4 * a * c)) / (2 * a)
  return root1, root2

# Stage 1: Hard-coded variables
a = 0.005
b = -0.25
c = 30

# Calculate and print results
root1, root2 = calculate_temperature(a, b, c)
print("Temperature (root1):", root1)
print("Temperature (root2):", root2)


# Stage 2: Keyboard input
print("\nEnter values for coefficients:")
a = float(input("a: "))
b = float(input("b: "))
c = float(input("c: "))

# Calculate and print results
root1, root2 = calculate_temperature(a, b, c)
print("Temperature (root1):", root1)
print("Temperature (root2):", root2)


# Stage 3: Read from file
try:
  with open("weather_data.txt", "r") as file:
    a, b, c = map(float, file.readline().split())
except FileNotFoundError:
  print("Error: File 'weather_data.txt' not found.")
else:
  # Calculate and print results
  root1, root2 = calculate_temperature(a, b, c)
  print("Temperature (root1):", root1)
  print("Temperature (root2):", root2)


# Stage 4: Single set of input (using keyboard)
print("\nEnter values for multiple sets of coefficients:")
sets = int(input("Number of sets: "))

for i in range(sets):
  print(f"\nSet {i + 1}")
  a = float(input("a: "))
  b = float(input("b: "))
  c = float(input("c: "))
  root1, root2 = calculate_temperature(a, b, c)
  print("Temperature (root1):", root1)
  print("Temperature (root2):", root2)


# Stage 5: Multiple sets of input (from file)
try:
  with open("weather_data.txt", "r") as file:
    for line in file:
      a, b, c = map(float, line.split())
      root1, root2 = calculate_temperature(a, b, c)
      print("\nSet:")
      print("a:", a)
      print("b:", b)
      print("c:", c)
      print("Temperature (root1):", root1)
      print("Temperature (root2):", root2)
except FileNotFoundError:
  print("Error: File 'weather_data.txt' not found.")

