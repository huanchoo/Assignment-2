#Brito, Juan, 22102796

#Problem 1
def sum5(n):
    if n <= 0:
        return 0
    
    k = (n - 1) // 5
    
    total_sum = 5 * k * (k + 1) // 2
    
    return total_sum


#Problem 2

def cap(s):
    vowels = 'aeiouy'
    
    result = ''
    
    for char in s:
        if char in vowels:
            result += char.upper()
        else:
            result += char
    
    return result


#Problem 3

def MeanRemove(numbers):
    if len(numbers) == 0:
        raise ValueError("The list should not be empty.")
    
    total_sum = sum(numbers)
    count = len(numbers)
    mean = total_sum / count
    
    result = []
    for num in numbers:
        result.append(num - mean)
    
    return result

#Problem 4

import math

def LongestEdge(ver1, ver2, ver3):
    def distance(p1, p2):
        return math.sqrt((p2[0] - p1[0]) ** 2 + 
                         (p2[1] - p1[1]) ** 2 + 
                         (p2[2] - p1[2]) ** 2)
    
    edge1 = distance(ver1, ver2)
    edge2 = distance(ver2, ver3)
    edge3 = distance(ver1, ver3)
    
    return max(edge1, edge2, edge3)


#Problem 5

def CheeseHunt(start_location):
    x, y = 2, 2

    def get_distance(p1, p2):
        return abs(p1[0] - p2[0]) + abs(p1[1] - p2[1])
    
    
    current_distance = get_distance((x, y), start_location)
    
    while (x, y) != start_location:
        print(f"({x},{y}) Please move: ", end="")
        
        move = input().strip().lower()
        
    if move == "left":
            x -= 1
        elif move == "right":
            x += 1
        elif move == "up":
            y -= 1
        elif move == "down":
            y += 1
        else:
            print("Invalid move. Please use 'left', 'right', 'up', or 'down'.")
            continue
        
        if x < 0 or x > 4 or y < 0 or y > 4:
            print("Move out of bounds. Please stay within the 5x5 grid.")
            if move == "left":
                x += 1
            elif move == "right":
                x -= 1
            elif move == "up":
                y += 1
            elif move == "down":
                y -= 1
            continue
        
        new_distance = get_distance((x, y), start_location)
        
        if new_distance < current_distance:
            print("Closer to cheese")
        elif new_distance > current_distance:
            print("Farther from cheese")
        else:
            print("Distance unchanged")
        
        current_distance = new_distance
    
    print(f"Congratulations! You found the cheese at ({x},{y}).")
