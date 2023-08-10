![Logo](https://i.ytimg.com/vi/UC-CBUSQXAo/maxresdefault.jpg)

# Uniform Distribution 
Modify the empty list, p, so that it becomes a UNIFORM probability distribution over five grid cells, as expressed in a list of five probabilities.

```bash
p = [0.2, 0.2, 0.2, 0.2, 0.2]

print(p)
```

## Code output: 

![image](https://github.com/cavadibrahimli1/intro_to_self_driving_cars/assets/76445357/6ed0450e-58ab-441b-a8d4-1b0f886c3174)


# Generalised Uniform Distribution 

```bash
p = [1/n] * n
print(p)
```
![image](https://github.com/cavadibrahimli1/intro_to_self_driving_cars/assets/76445357/945e288f-8d3b-4f1a-96b9-5271af192045)


![image](https://github.com/cavadibrahimli1/intro_to_self_driving_cars/assets/76445357/cb72c696-318b-4a15-b09f-54961db5d034)



Write code that outputs p after multiplying each entry by pHit or pMiss at the appropriate places. Remember that the red cells 1 and 2 are hits and the other green cells are misses.

```bash
p = [0.2, 0.2, 0.2, 0.2, 0.2]
pHit = 0.6
pMiss = 0.2

for i in range(len(p)):
    if i == 0 or i == 1:  # Cells 1 and 2 are hits
        p[i] *= pHit
    else:  # Cells 3, 4, and 5 are misses
        p[i] *= pMiss

print(p)
```
Modify the program to find and print the sum of all the entries in the list p.

```bash
p=[0.2, 0.2, 0.2, 0.2, 0.2]
pHit = 0.6
pMiss = 0.2

p[0]=p[0]*pMiss
p[1]=p[1]*pHit
p[2]=p[2]*pHit
p[3]=p[3]*pMiss
p[4]=p[4]*pMiss

sum_p = sum(p)

print("Modified probabilities:", p)
print("Sum of all entries in p:", sum_p)
```


Modify the code below so that the function sense, which takes p and Z as inputs, will output the NON-normalized  probability distribution, q, after multiplying the entries  in p by pHit or pMiss according to the color in the corresponding cell in world.

```bash
p = [0.2, 0.2, 0.2, 0.2, 0.2]
world = ['green', 'red', 'red', 'green', 'green']
Z = 'red'
pHit = 0.6
pMiss = 0.2

def sense(p, Z):
    q = []  # Initialize the non-normalized probability distribution q
    for i in range(len(p)):
        if world[i] == Z:  # Check if the cell color matches the measurement
            q.append(p[i] * pHit)
        else:
            q.append(p[i] * pMiss)
    return q

result = sense(p, Z)
print(result)
```

Modify your code so that it normalizes the output for the function sense. This means that the entries in q should sum to one.
```bash
p = [0.2, 0.2, 0.2, 0.2, 0.2]
world = ['green', 'red', 'red', 'green', 'green']
Z = 'red'
pHit = 0.6
pMiss = 0.2

def sense(p, Z):
    q = []
    for i in range(len(p)):
        hit = (Z == world[i])
        q.append(p[i] * (hit * pHit + (1 - hit) * pMiss))
    
    # Normalize the probabilities in q
    sum_q = sum(q)
    q = [prob / sum_q for prob in q]
    
    return q

result = sense(p, Z)
print(result)
```

![image](https://github.com/cavadibrahimli1/intro_to_self_driving_cars/assets/76445357/4102c0bf-b76b-460c-a43c-0b224afb1ec1)
