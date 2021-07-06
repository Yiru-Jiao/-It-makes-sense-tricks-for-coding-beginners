# "It-makes-sense" tricks for coding beginners like me

This is a notepad to record my (perhaps) strange coding needs and tricks that meet the needs with "ah yes, it makes sense".

## 1. How to generate a batch of regular variables in python
When I need to define a series of variables like a_1=[], a_2=[], a_3=[], ... , a_n=[] and they have various length and index, a 2d array doesn't work.

Use `exec()` which executes strings as executable code

``# Let's define 5 empty lists and name them a_1, a_2, a_3, a_4, a_5
    for i in range(1,6):
        exec('a_'+str(i)+'=[]')
``

3. 
