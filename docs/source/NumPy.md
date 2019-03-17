

```python
import numpy as np
x = np.array([1,2,3,4])
```


```python
x
```




    array([1, 2, 3, 4])




```python
print(x)
print(type(x))
```

    [1 2 3 4]
    <class 'numpy.ndarray'>
    


```python
np.zeros((2,3))
```




    array([[0., 0., 0.],
           [0., 0., 0.]])




```python
np.ones((3,3))
```




    array([[1., 1., 1.],
           [1., 1., 1.],
           [1., 1., 1.]])




```python
np.full((1,4), 5)
```




    array([[5, 5, 5, 5]])




```python
np.arange(10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



np.eye(4)


```python
np.eye(4)
```




    array([[1., 0., 0., 0.],
           [0., 1., 0., 0.],
           [0., 0., 1., 0.],
           [0., 0., 0., 1.]])




```python
np.diag([1,2,3,4])
```




    array([[1, 0, 0, 0],
           [0, 2, 0, 0],
           [0, 0, 3, 0],
           [0, 0, 0, 4]])




```python
np.arange(3,10)
```




    array([3, 4, 5, 6, 7, 8, 9])




```python
np.arange(2,9,3)
```




    array([2, 5, 8])




```python
np.arange(20).reshape(4, 5)
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19]])




```python
np.linspace(0,50,10, endpoint=False).reshape(5,2)
```




    array([[ 0.,  5.],
           [10., 15.],
           [20., 25.],
           [30., 35.],
           [40., 45.]])




```python
np.random.randint(4,15,size=(3,2))
```




    array([[ 6,  9],
           [ 8,  4],
           [13,  6]])




```python
Y = np.array([[1,2,3],[4,5,6],[7,8,9], [10,11,12]])
```


```python
# We print Y
print()
print('Y = \n', Y)
print()

# We print information about Y
print('Y has dimensions:', Y.shape)
print('Y has a total of', Y.size, 'elements')
print('Y is an object of type:', type(Y))
print('The elements in Y are of type:', Y.dtype)
```

    
    Y = 
     [[ 1  2  3]
     [ 4  5  6]
     [ 7  8  9]
     [10 11 12]]
    
    Y has dimensions: (4, 3)
    Y has a total of 12 elements
    Y is an object of type: <class 'numpy.ndarray'>
    The elements in Y are of type: int32
    


```python
# We create a rank 1 ndarray 
x = np.array([1, 2, 3, 4, 5])

# We create a rank 2 ndarray
Y = np.array([[1,2,3],[4,5,6],[7,8,9]])

# We print x
print()
print('Original x = ', x)

# We delete the first and last element of x
x = np.delete(x, [0,4])

# We print x with the first and last element deleted
print()
print('Modified x = ', x)

# We print Y
print()
print('Original Y = \n', Y)

# We delete the first row of y
w = np.delete(Y, 0, axis=0)

# We delete the first and last column of y
v = np.delete(Y, [0,2], axis=1)

# We print w
print()
print('w = \n', w)

# We print v
print()
print('v = \n', v)
```

    
    Original x =  [1 2 3 4 5]
    
    Modified x =  [2 3 4]
    
    Original Y = 
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    
    w = 
     [[4 5 6]
     [7 8 9]]
    
    v = 
     [[2]
     [5]
     [8]]
    


```python
# We create a rank 1 ndarray 
x = np.array([1, 2, 5, 6, 7])

# We create a rank 2 ndarray 
Y = np.array([[1,2,3],[7,8,9]])

# We print x
print()
print('Original x = ', x)

# We insert the integer 3 and 4 between 2 and 5 in x. 
x = np.insert(x,2,[3,4])

# We print x with the inserted elements
print()
print('x = ', x)

# We print Y
print()
print('Original Y = \n', Y)

# We insert a row between the first and last row of y
w = np.insert(Y,1,[4,5,6],axis=0)

# We insert a column full of 5s between the first and second column of y
v = np.insert(Y,1,5, axis=1)

# We print w
print()
print('w = \n', w)

# We print v
print()
print('v = \n', v)# We create a rank 1 ndarray 
x = np.array([1, 2, 3, 4, 5])

# We create a rank 2 ndarray 
Y = np.array([[1,2,3],[4,5,6]])

# We print x
print()
print('Original x = ', x)

# We append the integer 6 to x
x = np.append(x, 6)

# We print x
print()
print('x = ', x)

# We append the integer 7 and 8 to x
x = np.append(x, [7,8])

# We print x
print()
print('x = ', x)

# We print Y
print()
print('Original Y = \n', Y)

# We append a new row containing 7,8,9 to y
v = np.append(Y, [[7,8,9]], axis=0)

# We append a new column containing 9 and 10 to y
q = np.append(Y,[[9],[10]], axis=1)

# We print v
print()
print('v = \n', v)

# We print q
print()
print('q = \n', q)
```

    
    Original x =  [1 2 5 6 7]
    
    x =  [1 2 3 4 5 6 7]
    
    Original Y = 
     [[1 2 3]
     [7 8 9]]
    
    w = 
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    
    v = 
     [[1 5 2 3]
     [7 5 8 9]]
    
    Original x =  [1 2 3 4 5]
    
    x =  [1 2 3 4 5 6]
    
    x =  [1 2 3 4 5 6 7 8]
    
    Original Y = 
     [[1 2 3]
     [4 5 6]]
    
    v = 
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    
    q = 
     [[ 1  2  3  9]
     [ 4  5  6 10]]
    


```python
# We create a rank 1 ndarray 
x = np.array([1,2])

# We create a rank 2 ndarray 
Y = np.array([[3,4],[5,6]])

# We print x
print()
print('x = ', x)

# We print Y
print()
print('Y = \n', Y)

# We stack x on top of Y
z = np.vstack((x,Y))

# We stack x on the right of Y. We need to reshape x in order to stack it on the right of Y. 
w = np.hstack((Y,x.reshape(2,1)))

# We print z
print()
print('z = \n', z)

# We print w
print()
print('w = \n', w)
```

    
    x =  [1 2]
    
    Y = 
     [[3 4]
     [5 6]]
    
    z = 
     [[1 2]
     [3 4]
     [5 6]]
    
    w = 
     [[3 4 1]
     [5 6 2]]
    


```python
# We create a 4 x 5 ndarray that contains integers from 0 to 19
X = np.arange(20).reshape(4, 5)

# We print X
print()
print('X = \n', X)
print()

# We select all the elements that are in the 2nd through 4th rows and in the 3rd to 5th columns
Z = X[1:4,2:5]

# We print Z
print('Z = \n', Z)

# We can select the same elements as above using method 2
W = X[1:,2:5]

# We print W
print()
print('W = \n', W)

# We select all the elements that are in the 1st through 3rd rows and in the 3rd to 4th columns
Y = X[:3,2:5]

# We print Y
print()
print('Y = \n', Y)

# We select all the elements in the 3rd row
v = X[2,:]

# We print v
print()
print('v = ', v)

# We select all the elements in the 3rd column
q = X[:,2]

# We print q
print()
print('q = ', q)

# We select all the elements in the 3rd column but return a rank 2 ndarray
R = X[:,2:3]

# We print R
print()
print('R = \n', R)
```

    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]]
    
    Z = 
     [[ 7  8  9]
     [12 13 14]
     [17 18 19]]
    
    W = 
     [[ 7  8  9]
     [12 13 14]
     [17 18 19]]
    
    Y = 
     [[ 2  3  4]
     [ 7  8  9]
     [12 13 14]]
    
    v =  [10 11 12 13 14]
    
    q =  [ 2  7 12 17]
    
    R = 
     [[ 2]
     [ 7]
     [12]
     [17]]
    


```python
# We create a 4 x 5 ndarray that contains integers from 0 to 19
X = np.arange(20).reshape(4, 5)

# We print X
print()
print('X = \n', X)
print()

# create a copy of the slice using the np.copy() function
Z = np.copy(X[1:4,2:5])

#  create a copy of the slice using the copy as a method
W = X[1:4,2:5].copy()

# We change the last element in Z to 555
Z[2,2] = 555

# We change the last element in W to 444
W[2,2] = 444

# We print X
print()
print('X = \n', X)

# We print Z
print()
print('Z = \n', Z)

# We print W
print()
print('W = \n', W)
```

    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]]
    
    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]]
    
    Z = 
     [[  7   8   9]
     [ 12  13  14]
     [ 17  18 555]]
    
    W = 
     [[  7   8   9]
     [ 12  13  14]
     [ 17  18 444]]
    


```python
# We create a 4 x 5 ndarray that contains integers from 0 to 19
X = np.arange(20).reshape(4, 5)

# We create a rank 1 ndarray that will serve as indices to select elements from X
indices = np.array([1,3])

# We print X
print()
print('X = \n', X)
print()

# We print indices
print('indices = ', indices)
print()

# We use the indices ndarray to select the 2nd and 4th row of X
Y = X[indices,:]

# We use the indices ndarray to select the 2nd and 4th column of X
Z = X[:, indices]

# We print Y
print()
print('Y = \n', Y)

# We print Z
print()
print('Z = \n', Z)
```

    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]]
    
    indices =  [1 3]
    
    
    Y = 
     [[ 5  6  7  8  9]
     [15 16 17 18 19]]
    
    Z = 
     [[ 1  3]
     [ 6  8]
     [11 13]
     [16 18]]
    


```python
# We create a 4 x 5 ndarray that contains integers from 0 to 19
X = np.arange(25).reshape(5, 5)

# We print X
print()
print('X = \n', X)
print()

# We print the elements in the main diagonal of X
print('z =', np.diag(X))
print()

# We print the elements above the main diagonal of X
print('y =', np.diag(X, k=1))
print()

# We print the elements below the main diagonal of X
print('w = ', np.diag(X, k=-1))
```

    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]
     [20 21 22 23 24]]
    
    z = [ 0  6 12 18 24]
    
    y = [ 1  7 13 19]
    
    w =  [ 5 11 17 23]
    


```python
# Create 3 x 3 ndarray with repeated values
X = np.array([[1,2,3],[5,2,8],[1,2,3]])

# We print X
print()
print('X = \n', X)
print()

# We print the unique elements of X 
print('The unique elements in X are:',np.unique(X))
```

    
    X = 
     [[1 2 3]
     [5 2 8]
     [1 2 3]]
    
    The unique elements in X are: [1 2 3 5 8]
    


```python
# We create a 5 x 5 ndarray that contains integers from 0 to 24
X = np.arange(25).reshape(5, 5)

# We print X
print()
print('Original X = \n', X)
print()

# We use Boolean indexing to select elements in X:
print('The elements in X that are greater than 10:', X[X > 10])
print('The elements in X that less than or equal to 7:', X[X <= 7])
print('The elements in X that are between 10 and 17:', X[(X > 10) & (X < 17)])

# We use Boolean indexing to assign the elements that are between 10 and 17 the value of -1
X[(X > 10) & (X < 17)] = -1

# We print X
print()
print('X = \n', X)
print()
```

    
    Original X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]
     [15 16 17 18 19]
     [20 21 22 23 24]]
    
    The elements in X that are greater than 10: [11 12 13 14 15 16 17 18 19 20 21 22 23 24]
    The elements in X that less than or equal to 7: [0 1 2 3 4 5 6 7]
    The elements in X that are between 10 and 17: [11 12 13 14 15 16]
    
    X = 
     [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 -1 -1 -1 -1]
     [-1 -1 17 18 19]
     [20 21 22 23 24]]
    
    


```python
# We create a rank 1 ndarray
x = np.array([1,2,3,4,5])

# We create a rank 1 ndarray
y = np.array([6,7,2,8,4])

# We print x
print()
print('x = ', x)

# We print y
print()
print('y = ', y)

# We use set operations to compare x and y:
print()
print('The elements that are both in x and y:', np.intersect1d(x,y))
print('The elements that are in x that are not in y:', np.setdiff1d(x,y))
print('All the elements of x and y:',np.union1d(x,y))
```

    
    x =  [1 2 3 4 5]
    
    y =  [6 7 2 8 4]
    
    The elements that are both in x and y: [2 4]
    The elements that are in x that are not in y: [1 3 5]
    All the elements of x and y: [1 2 3 4 5 6 7 8]
    


```python
# We create an unsorted rank 1 ndarray
x = np.random.randint(1,11,size=(10,))

# We print x
print()
print('Original x = ', x)

# We sort x and print the sorted array using sort as a function.
print()
print('Sorted x (out of place):', np.sort(x))

# When we sort out of place the original array remains intact. To see this we print x again
print()
print('x after sorting:', x)
```

    
    Original x =  [ 4 10  6  1  2  3  6  7  3  5]
    
    Sorted x (out of place): [ 1  2  3  3  4  5  6  6  7 10]
    
    x after sorting: [ 4 10  6  1  2  3  6  7  3  5]
    


```python
# We create an unsorted rank 1 ndarray
x = np.random.randint(1,11,size=(10,))

# We print x
print()
print('Original x = ', x)

# We sort x and print the sorted array using sort as a method.
x.sort()

# When we sort in place the original array is changed to the sorted array. To see this we print x again
print()
print('x after sorting:', x)
```

    
    Original x =  [1 2 4 1 9 9 7 8 2 1]
    
    x after sorting: [1 1 1 2 2 4 7 8 9 9]
    


```python
# We create an unsorted rank 2 ndarray
X = np.random.randint(1,11,size=(5,5))

# We print X
print()
print('Original X = \n', X)
print()

# We sort the columns of X and print the sorted array
print()
print('X with sorted columns :\n', np.sort(X, axis = 0))

# We sort the rows of X and print the sorted array
print()
print('X with sorted rows :\n', np.sort(X, axis = 1))
```

    
    Original X = 
     [[ 4  2  4 10  5]
     [ 9  6 10  6  4]
     [ 2  1  8  9  8]
     [ 5  9  3  4  1]
     [ 7  8  7  6  8]]
    
    
    X with sorted columns :
     [[ 2  1  3  4  1]
     [ 4  2  4  6  4]
     [ 5  6  7  6  5]
     [ 7  8  8  9  8]
     [ 9  9 10 10  8]]
    
    X with sorted rows :
     [[ 2  4  4  5 10]
     [ 4  6  6  9 10]
     [ 1  2  8  8  9]
     [ 1  3  4  5  9]
     [ 6  7  7  8  8]]
    


```python
y = x[x%2!=0]
print(y)
```

    [ 1  3  5  7  9 11 13 15 17 19 21 23 25]
    


```python
# We create two rank 1 ndarrays
x = np.array([1,2,3,4])
y = np.array([5.5,6.5,7.5,8.5])

# We print x
print()
print('x = ', x)

# We print y
print()
print('y = ', y)
print()

# We perfrom basic element-wise operations using arithmetic symbols and functions
print('x + y = ', x + y)
print('add(x,y) = ', np.add(x,y))
print()
print('x - y = ', x - y)
print('subtract(x,y) = ', np.subtract(x,y))
print()
print('x * y = ', x * y)
print('multiply(x,y) = ', np.multiply(x,y))
print()
print('x / y = ', x / y)
print('divide(x,y) = ', np.divide(x,y))
```

    
    x =  [1 2 3 4]
    
    y =  [5.5 6.5 7.5 8.5]
    
    x + y =  [ 6.5  8.5 10.5 12.5]
    add(x,y) =  [ 6.5  8.5 10.5 12.5]
    
    x - y =  [-4.5 -4.5 -4.5 -4.5]
    subtract(x,y) =  [-4.5 -4.5 -4.5 -4.5]
    
    x * y =  [ 5.5 13.  22.5 34. ]
    multiply(x,y) =  [ 5.5 13.  22.5 34. ]
    
    x / y =  [0.18181818 0.30769231 0.4        0.47058824]
    divide(x,y) =  [0.18181818 0.30769231 0.4        0.47058824]
    


```python
# We create two rank 2 ndarrays
X = np.array([1,2,3,4]).reshape(2,2)
Y = np.array([5.5,6.5,7.5,8.5]).reshape(2,2)

# We print X
print()
print('X = \n', X)

# We print Y
print()
print('Y = \n', Y)
print()

# We perform basic element-wise operations using arithmetic symbols and functions
print('X + Y = \n', X + Y)
print()
print('add(X,Y) = \n', np.add(X,Y))
print()
print('X - Y = \n', X - Y)
print()
print('subtract(X,Y) = \n', np.subtract(X,Y))
print()
print('X * Y = \n', X * Y)
print()
print('multiply(X,Y) = \n', np.multiply(X,Y))
print()
print('X / Y = \n', X / Y)
print()
print('divide(X,Y) = \n', np.divide(X,Y))
```

    
    X = 
     [[1 2]
     [3 4]]
    
    Y = 
     [[5.5 6.5]
     [7.5 8.5]]
    
    X + Y = 
     [[ 6.5  8.5]
     [10.5 12.5]]
    
    add(X,Y) = 
     [[ 6.5  8.5]
     [10.5 12.5]]
    
    X - Y = 
     [[-4.5 -4.5]
     [-4.5 -4.5]]
    
    subtract(X,Y) = 
     [[-4.5 -4.5]
     [-4.5 -4.5]]
    
    X * Y = 
     [[ 5.5 13. ]
     [22.5 34. ]]
    
    multiply(X,Y) = 
     [[ 5.5 13. ]
     [22.5 34. ]]
    
    X / Y = 
     [[0.18181818 0.30769231]
     [0.4        0.47058824]]
    
    divide(X,Y) = 
     [[0.18181818 0.30769231]
     [0.4        0.47058824]]
    


```python
# We create a rank 1 ndarray
x = np.array([1,2,3,4])

# We print x
print()
print('x = ', x)

# We apply different mathematical functions to all elements of x
print()
print('EXP(x) =', np.exp(x))
print()
print('SQRT(x) =',np.sqrt(x))
print()
print('POW(x,2) =',np.power(x,2)) # We raise all elements to the power of 2
```

    
    x =  [1 2 3 4]
    
    EXP(x) = [ 2.71828183  7.3890561  20.08553692 54.59815003]
    
    SQRT(x) = [1.         1.41421356 1.73205081 2.        ]
    
    POW(x,2) = [ 1  4  9 16]
    


```python
# We create a 2 x 2 ndarray
X = np.array([[1,2], [3,4]])

# We print x
print()
print('X = \n', X)
print()

print('Average of all elements in X:', X.mean())
print('Average of all elements in the columns of X:', X.mean(axis=0))
print('Average of all elements in the rows of X:', X.mean(axis=1))
print()
print('Sum of all elements in X:', X.sum())
print('Sum of all elements in the columns of X:', X.sum(axis=0))
print('Sum of all elements in the rows of X:', X.sum(axis=1))
print()
print('Standard Deviation of all elements in X:', X.std())
print('Standard Deviation of all elements in the columns of X:', X.std(axis=0))
print('Standard Deviation of all elements in the rows of X:', X.std(axis=1))
print()
print('Median of all elements in X:', np.median(X))
print('Median of all elements in the columns of X:', np.median(X,axis=0))
print('Median of all elements in the rows of X:', np.median(X,axis=1))
print()
print('Maximum value of all elements in X:', X.max())
print('Maximum value of all elements in the columns of X:', X.max(axis=0))
print('Maximum value of all elements in the rows of X:', X.max(axis=1))
print()
print('Minimum value of all elements in X:', X.min())
print('Minimum value of all elements in the columns of X:', X.min(axis=0))
print('Minimum value of all elements in the rows of X:', X.min(axis=1))
```

    
    X = 
     [[1 2]
     [3 4]]
    
    Average of all elements in X: 2.5
    Average of all elements in the columns of X: [2. 3.]
    Average of all elements in the rows of X: [1.5 3.5]
    
    Sum of all elements in X: 10
    Sum of all elements in the columns of X: [4 6]
    Sum of all elements in the rows of X: [3 7]
    
    Standard Deviation of all elements in X: 1.118033988749895
    Standard Deviation of all elements in the columns of X: [1. 1.]
    Standard Deviation of all elements in the rows of X: [0.5 0.5]
    
    Median of all elements in X: 2.5
    Median of all elements in the columns of X: [2. 3.]
    Median of all elements in the rows of X: [1.5 3.5]
    
    Maximum value of all elements in X: 4
    Maximum value of all elements in the columns of X: [3 4]
    Maximum value of all elements in the rows of X: [2 4]
    
    Minimum value of all elements in X: 1
    Minimum value of all elements in the columns of X: [1 2]
    Minimum value of all elements in the rows of X: [1 3]
    


```python
# We create a 2 x 2 ndarray
X = np.array([[1,2], [3,4]])

# We print x
print()
print('X = \n', X)
print()

print('3 * X = \n', 3 * X)
print()
print('3 + X = \n', 3 + X)
print()
print('X - 3 = \n', X - 3)
print()
print('X / 3 = \n', X / 3)
```

    
    X = 
     [[1 2]
     [3 4]]
    
    3 * X = 
     [[ 3  6]
     [ 9 12]]
    
    3 + X = 
     [[4 5]
     [6 7]]
    
    X - 3 = 
     [[-2 -1]
     [ 0  1]]
    
    X / 3 = 
     [[0.33333333 0.66666667]
     [1.         1.33333333]]
    


```python
# We create a rank 1 ndarray
x = np.array([1,2,3])

# We create a 3 x 3 ndarray
Y = np.array([[1,2,3],[4,5,6],[7,8,9]])

# We create a 3 x 1 ndarray
Z = np.array([1,2,3]).reshape(3,1)

# We print x
print()
print('x = ', x)
print()

# We print Y
print()
print('Y = \n', Y)
print()

# We print Z
print()
print('Z = \n', Z)
print()

print('x + Y = \n', x + Y)
print()
print('Z + Y = \n',Z + Y)
```

    
    x =  [1 2 3]
    
    
    Y = 
     [[1 2 3]
     [4 5 6]
     [7 8 9]]
    
    
    Z = 
     [[1]
     [2]
     [3]]
    
    x + Y = 
     [[ 2  4  6]
     [ 5  7  9]
     [ 8 10 12]]
    
    Z + Y = 
     [[ 2  3  4]
     [ 6  7  8]
     [10 11 12]]
    


```python

```
