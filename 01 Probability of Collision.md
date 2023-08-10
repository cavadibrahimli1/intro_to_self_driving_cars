
![Logo](https://media.springernature.com/lw685/springer-static/image/chp%3A10.1007%2F978-981-10-2963-9_5/MediaObjects/370756_1_En_5_Fig1_HTML.gif)

# Probability of Collision




```bash
   \Car1|
    \   |
     \  |
 Car2 \ |  LEFT  | STRAIGHT | RIGHT
___________________________________
  LEFT  |  0.5   |  0.25    | 0.1
STRAIGHT|  0.25  |  0.02    | 0.1
 RIGHT  |  0.1   |  0.1     | 0.01
```

The truth table shown above represents the probability of two cars colliding at an intersection if they both attempt a maneuver at the same time. If Car 1 goes straight and car two goes left, for example, there is a probability of collision of 0.25.

My code: 

```bash
def probability_of_collision(car_1, car_2):
    # car_1 and car_2 will each be strings whose value will either be 
    # "L" for left, "S" for straight, or "R" for right.
    probability = 0.0 # you should change this value based on the directions.
    
    if car_1 == "L":
        if car_2 == "L":
            probability = 0.5
        elif car_2 == "R":
            probability = 0.1
        else:  # car_2 == "S"
            probability = 0.25
    elif car_1 == "S":
        if car_2 == "R":
            probability = 0.1
    else:  # car_1 == "R"
        if car_2 == "L":
            probability = 0.1
    
    return probability

# This function is used to test the correctness of your code. You shouldn't
# touch any of the code below here (but feel free to look through it to
# understand what "correct" looks like).
def test():
    num_correct = 0
    
    p1 = probability_of_collision("L", "L")
    if p1 == 0.5:
        num_correct += 1
    
    p2 = probability_of_collision("L", "R")
    if p2 == 0.1:
        num_correct += 1
    
    p3 = probability_of_collision("L", "S")
    if p3 == 0.25:
        num_correct += 1
    
    p4 = probability_of_collision("S", "R")
    if p4 == 0.1:
        num_correct += 1
    
    print("You got", num_correct, "out of 4 correct")
    
test()
```
