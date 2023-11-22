#Write a python program that accepts the length of three sides of a triangle as inputs. The program 
#should indicate whether or not the triangle is a right-angled triangle. (Use Pythagorean theorem) Also 
#find out its area using Heron’s formula.
def is_right_angle_triangle(side1, side2, side3):
    sides = [side1, side2, side3]
    sides.sort()

    # Pythagorean theorem: a^2 + b^2 = c^2
    if sides[0]**2 + sides[1]**2 == sides[2]**2:
        return True
    else:
        return False

def calculate_area(side1, side2, side3):
    # Heron's formula: area = sqrt(s * (s - a) * (s - b) * (s - c))
    s = (side1 + side2 + side3) / 2
    area = (s * (s - side1) * (s - side2) * (s - side3)) ** 0.5
    return area

def main():
    try:
        side1 = float(input("Enter the length of side 1: "))
        side2 = float(input("Enter the length of side 2: "))
        side3 = float(input("Enter the length of side 3: "))
    except ValueError:
        print("Invalid input. Please enter numeric values for the side lengths.")
        return

    if side1 <= 0 or side2 <= 0 or side3 <= 0:
        print("Invalid input. Side lengths must be positive.")
        return

    if is_right_angle_triangle(side1, side2, side3):
        print("It's a right-angled triangle.")
    else:
        print("It's not a right-angled triangle.")

    area = calculate_area(side1, side2, side3)
    print(f"The area of the triangle is: {area:.2f}")

# Example usage:
main()
