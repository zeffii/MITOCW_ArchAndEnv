## Assignment 1.2

### Reading List 

todo

## Exercise 1.2 PDF

I'm going to improvise here and write code that will let me render geometry when all i give are vertices and edges. From thi set individual edges will be derived. For example if I have a continous set of edges
```python
x---x---x---x---x---x---x---x---x
```
this can become
```python
x---x  x---x  x---x  x---x  x---x  x---x  x---x  x---x
```
it might be important to note that their locations will be unchanges, the change depicted here serves only to indicate that they are no longer joined, and no vertex will be shared by two edges. Each edge will be represented by a Curve because curves can be rendered with thickness and subdivision.

I went ahead and did a rendering of what it might look like once I have a node that outputs curves directly into the scene. As one you can tell it's perphaps not the most interesting result of the random selection of 'choreographed positions and angles'. 

Something like this, can become through shadows (all rendered with geometry hidden to the camera)
![something like this](https://cloud.githubusercontent.com/assets/619340/5722644/3bc3dde0-9b3e-11e4-8670-9dbc61d58823.png) turns into this:
![image](https://cloud.githubusercontent.com/assets/619340/5731085/081b9446-9b80-11e4-8a70-a5dae595a184.png)

I would like to pick a different set of random values while still following the word of the brief as far as possible. It is possible through parametericism to iterate through versions and track their seeds, untill I find a couple of versions that stand out. Then pick one.

