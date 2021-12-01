### Chaos game - square

Let's see what type of pattern we get for 4 vertices.

```python
import random
import matplotlib.pyplot as plt

def move_point(point,vertex):
    x=(point[0]+vertex[0])/2
    y=(point[1]+vertex[1])/2
    return (x,y)

# vertex={'A':(0.5,1), 'B':(0,0), 'C':(1,0)}
vertex=[(0,0),(1,0),(0,1),(1,1)]
x=[]
y=[]

point=[0.5,0.5]
for i in range(10000):
    random_index = random.randrange(0, 4)
    point=move_point(point,vertex[random_index])
    x.append(point[0])
    y.append(point[1])
    
plt.figure(figsize=(12,12))
plt.scatter(x,y,s=1)
plt.show()
```

## Generic approach

When we introduced the concept, the point was said to move halfway. But the amount of movement can be different than half. So let's rewrite the code so that the point moves a certain ratio `r`. 

Then, let's see what type of pattern we get for a ratio other than half (the example below uses ratio of **0.4**)

```python
import random
import matplotlib.pyplot as plt

def move_point_gen(point,vertex,r):
    x=point[0]+(vertex[0]-point[0])*(1-r)
    y=point[1]+(vertex[1]-point[1])*(1-r)
    return (x,y)

# vertex={'A':(0.5,1), 'B':(0,0), 'C':(1,0)}
vertex=[(0,0),(1,0),(0,1),(1,1)]
x=[]
y=[]

point=[0.5,0.5]
for i in range(10000):
    random_index = random.randrange(0, 4)
    point=move_point_gen(point,vertex[random_index],0.4)
    x.append(point[0])
    y.append(point[1])
    
plt.figure(figsize=(12,12))
plt.scatter(x,y,s=1)
plt.show()
```


Please check if results match with [Wolfram website](http://mathworld.wolfram.com/ChaosGame.html).
