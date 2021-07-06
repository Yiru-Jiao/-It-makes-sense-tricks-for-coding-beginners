# "It-makes-sense" tricks for coding beginners like me

This is a notepad to record my (perhaps) strange coding needs and tricks that meet the needs with "ah yes, it makes sense".

## 1. How to generate a batch of regular variables in python?
__Q.__ I need to define a series of variables like a_1=[], a_2=[], a_3=[], ... , a_n=[] and they have various length and index.

__A.__ Use `exec()` which executes strings as executable code

    # Let's define 5 empty lists and name them a_1, a_2, a_3, a_4, a_5
    for i in range(1,6):
        exec('a_'+str(i)+'=[]')

## 2. How to create an array to record a huge amount of true values (True/1 and False/0)?
__Q.__ I need to create an array of size 25000\*700\*700 to record true values; `np.zeros((25000, 700, 700))` is warned with the memory error of `Unable to allocate 91.3 GiB for an array with shape (25000, 700, 700) and data type float64`.
__A.__ Change the data type to bool will save the memory significantly
    
    np.zeros((25000, 700, 700), dtype=bool)
    # the memory size now is around 12.25 GB -- still large but at least accessable


## 3. How to save a large array of 0/False and 1/True with numpy (where the True values are sparse)?
__Q.__ I have a large array of true values (the one created in question 2 and processed further), for example, of size 25000\*700\*700, which cannot be reshaped into 2d and saved as a csv file because the required memory size is soooo large and the the required time is sooooo long.
__A.__ Save the indices of True values (it only occupies 120 bytes in my case!)

    indices = np.argwhere(true_or_false_array)
    # When you need to recover the original true_or_false_array
    recovered_array = np.zeros((25000, 700, 700), dtype=bool)
    recovered_array[indices[:,0], indices[:,1], indices[:,2]] = True

--to be continued--
