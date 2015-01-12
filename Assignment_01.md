## Assignment 1

### Reading List 

The reading list has titles, i'll focus on what can be read for free and legit :). Youtube and pdfs. 

- #### Experiencing Architecture
  The excerpt from this book is how I wish all books on abstract material were. Comfortable and pleasurable to read. 

  - **Aage Rafn** 
  According to chapter 6 from the google books preview of this book, the core is about creating and breaking a rhythm. A contemporary example is the [Federal Courthouse in Austin Texas](http://en.wikipedia.org/wiki/Austin,_Texas#mediaviewer/File:Federal_Courthouse,_Austin,_TX_IMG_6339.JPG). When everything has rhythm the un-rhythmic stands out, when everything is without rhythm, then the rhythmic highlights itself.

  - **Alvar Aalto**
  Neat buildings, reminds me of Sant'Elia

  - **Gunmar Asplund**
  Ratios and Scale, thin and wide

  - **Ib Lunding** cement, walls textured by the grain of the planks of wood used to form their shape when poured. Rather than sanding it down the texture is preserved and acts as a reminder about how it was constructed. I first noticed this kind of detail in a hospital stairwell, it felt a little out of place even unfinished.

  A question arrises about how structurally sound something is perceived by the finish on its surface, a pilar that looks fluffy or sandy (velvet) may appear less strong than a tight smooth fine surface (marble polished)

- #### Rhythm of Venice
  In relation to the rhythm of venice I found [this sourced jan 9 2014](http://ocw.mit.edu/courses/architecture/4-111-introduction-to-architecture-environmental-design-spring-2014/readings/) to be interesting, it shows A A B A A | A B A patterns. I've never looked at facades that way before, but now it's pointed out -- sure, 

- #### Powers of Ten
  yeah, that's a brilliant video, `music + visual + narration`. 
  https://www.youtube.com/watch?v=0fKBhvDjuy0

- #### Typology
  `moneo_on_tipology.pdf` is a bit difficult to process, it's written in some tail recursive way that never seems to really reach a conclusion and then finally does resolve to an answer. It's serious and abstract, and i'm not sure I understood it. 

- #### Design QA with Eames
  https://www.youtube.com/watch?v=z8qs5-BDXNU - delightful.  
  Also https://www.youtube.com/watch?v=hv7ipQdUrYk (House) is pleasant

### Exercise 1.1 PDF

#### 1

[MIT4_111S14_Assignment_1.1.pdf](http://ocw.mit.edu/courses/architecture/4-111-introduction-to-architecture-environmental-design-spring-2014/assignments/MIT4_111S14_Assignment_1.1.pdf)

check it out, entry 10 is Distal Phalange on pinky finger. 1 is Ossa Tarsi. Measurements are all distances to the next bone. Smaller measurements tend to be more exact because it becomes easier to decide the extremes.

step 1.

```text

01: 18.1 cm | 90
02: 51.0 cm | 130
03: 56.0 cm | 30
04: 58.0 cm | 100
05: 32.0 cm | 180
06: 32.0 cm | 130
07:  8.0 cm | 180
08:  4.7 cm | 120
09:  2.8 cm | 70
10:  2.3 cm | 60
```

step 2. scale down a tenth

Because it will be rendered in a unitless scenario scaling may be useless. But I will pick angles at random from the selection. Here's a python representation of that. Seed added just in case.

```python
from random import random, seed

measurements = [
    [18.1, 90],
    [51.0, 130],
    [56.0, 30],
    [58.0, 100],
    [32.0, 180],
    [32.0, 130],
    [8.0, 180],
    [4.7, 120],
    [2.8, 70],
    [2.3, 60]
]

seed(20)

for length, angle in measurements:
    print(length, round(random()*angle, 2))

```

#### 2

starting with a vertical line up then take consecutive lines clockwise, off the tangent of the previous line.
Time to hit Sverchok, it's more work than drawing - hopefully with interesting results - Else I will coerce it.

In sverchok the ScriptNode MK1 script might look like this

```Python
from random import random, seed

def obtain_values(scale, seed_val):
    measurements = [
        [18.1, 90],
        [51.0, 130],
        [56.0, 30],
        [58.0, 100],
        [32.0, 180],
        [32.0, 130],
        [8.0, 180],
        [4.7, 120],
        [2.8, 70],
        [2.3, 60]
    ]

    seed(seed_val)
    convertor = lambda l, a: (l/scale, round(random()*a, 2))
    return [convertor(*vals) for vals in measurements]


def sv_main(scale=1.0, seed_val=20):
    lengths_out = []
    angles_out = []

    in_sockets = [
        ['s', 'scale', scale],
        ['s', 'seed', seed_val]
    ]

    out_sockets = [
        ['s', 'lengths', lengths_out],
        ['s', 'angles', angles_out]
    ]
    
    measures = obtain_values(scale, seed_val)
    for l, a in measures:
        lengths_out.append(l)
        angles_out.append(a)
    
    return in_sockets, out_sockets

```
this outputs two lists, one of lengts the other of an angle.







