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

The first multi-shadow rendering below shows a mesh manually converted to Curves, to simulate the effect early. It's perphaps not the most interesting result of the random selection of 'choreographed positions and angles'. 

Something like this silhouette:  
![something like this](https://cloud.githubusercontent.com/assets/619340/5722644/3bc3dde0-9b3e-11e4-8670-9dbc61d58823.png) 

with 3 duplications and offsets can become: 

![image](https://cloud.githubusercontent.com/assets/619340/5731085/081b9446-9b80-11e4-8a70-a5dae595a184.png)


all shadows rendered with geometry hidden to the camera, the line thickness is direct output of the render onto the background.

I would like to pick a different set of random values while still following the word of the brief as far as possible. It is possible through parametericism to iterate through versions and track their seeds, untill I find a couple of versions that stand out. Then pick one.

With the Sverchok Curve Node now written the most tentative BETA code makes it possible to generate a renderable curve from a sequence of vectors. Now iteration is much quicer and I can focus on aesthetics. This gif shows only the geometry before shadow rendering.
![totes images!](https://cloud.githubusercontent.com/assets/619340/5740560/d579cfd2-9c04-11e4-9add-ad973d5d8eea.gif)

