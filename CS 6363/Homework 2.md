# Homework 2
## Frequent Items
```python
def find3(A):  
	if len(A) < 3:  
		return A  
	  
	mid = len(A)//2  
	one = A[:mid] # first half of the list  
	two = A[mid:] # second half of the list  
	l = []  
	l += find3(one) # all the solutions to the first half of the list 
	l += find3(two)  # add the solutions to the second half of the list
	
	collection = []  
	  
	for i in l:  
		count = 0  
		if i in collection: # we want to keep these two for loops O(n) we eliminate duplicates  
			continue  
		for t in A:  
			if i == t:  
				count += 1  
		if count > len(A)//3:  
			collection.append(i)  
	return collection
```
- Base case: If the length of the array is less than 3 return the array. In this case every element in the array appears more than $\frac{n}{3}$ times. 
- Inductive step: if a number appears more than $\frac{n}{3}$ times in an array, it must appear more than $\frac{n}{6}$ times in one of the halves of the array. 
- Runtime analysis: this implementation is just like Mergesort. For even more efficiency, we would use indices rather list comprehension. To show that the conquer part of our algorithm is correct and $O(n)$ we use pigeon hole principle. Recognizing that our list l and list collection can have at most 2 items in them. If there were to have 3 or more, we would have $3\left( \frac{n}{3}+1 \right)=n+3$ and this is not possible. Therefore, even though we have two for loops, we are funning through a list of $n$ at most twice, i.e. $O(n)$. Our algorithm's recurrence is $T(N)=2T\left( \frac{n}{2} \right)+n$ which solves to $\Theta(n\log n)$. 
## Boxes
```python
def boxes(A):  
	if len(A) == 1:  
		l, r, h = A[0]  
		return[(l, h), (r, 0)]  
	  
	mid = len(A)//2  
	x = boxes(A[:mid])  
	y = boxes(A[mid:])  
	return merge(x, y)  

def merge(A, B):  
	l = []  
	i, j = 0, 0  
	  
	while i < len(A) and j < len(B):  
		l1, h1 = A[i]  
		l2, h2 = B[j]  
		if l1 < l2:  
			l.append((l1, max(h1, h2)))  
			i += 1  
		if l2 < l1:  
			l.append((l1, max(h1, h2)))  
			j += 1  
		else:  
			l.append((l1, max(h1, h2)))  
			i += 1  
			j += 1  
	  
	l.extend(A[i:])  
	l.extend(B[i:])  
	  
	return l  
  

```
- I was not able to make this work perfectly well.  I attempted to treat it like a mergesort, splitting the array in half, and the base case being a list having only one element. For the merge operation I attempted to merge using the three possible cases: The right box is is completely inside the left box, the right box is partially inside the left box, and the left and right box do not overlap. 

## Inversions
```
1: procedure MergeSort(A[1 . . . n] 
	2: if n > 1 then 
		3: m = ⌊n/2⌋ 
		4: MergeSort(A[1 . . . m], count) 
		5: MergeSort(A[m + 1 . . . n], count) 
		6: Merge(A[1 . . . n], m)
```

```
1: procedure Merge(A[1 . . . n], m, count) 
	2: Init B[1 . . . n] 
	3: i = 1 ; j = m + 1 
	4: for b = 1 to n do 
		5: if j > n then 
			6: B[b] = A[i]; i = i + 1 
	7: else if i > m then 
		8: B[b] = A[j]; j = j + 1 
	9: else if A[i] ≤ A[j] then 
		10: B[b] = A[i]; i = i + 1 
	11: else 
		12: B[b] = A[j]; j = j + 1 
		13: count = count + (m - i + 1)
	13: A[1 . . . n] = B[1 . . . n]
```
- We increase the count when we move an element from the second half of the list first. The number of inversions is $(m-i+1)$ because the element is smaller than the elements from $i$ to the end of the list. 
## Selection in sorted Arrays
```python
def findk(A, B, k):  
	if k == 1:  
		return min(A[0], B[0])  
	  
	mida = len(A)//2  
	midb = len(B)//2  
	  
	if k < mida + midb+2:  
		if A[mida]>B[midb]:  
			A = A[:mida]  
		else:  
			B = B[:midb]  
	  
	if k > mida + midb+2:  
		if A[mida]<B[midb]:  
			A = A[mida:]  
			k = k - (mida+1)  
		else:  
			B = B[midb:]  
			k = k - (midb+1) 
			 
	if k == mida + midb+2:  
		return max(A[mida], B[midb])  
	  
	  
	return findk(A, B, k)
```
- Base Case: If k = 1, we know both lists are sorted so it must be that the first smallest element is the minimum of the first elements in both arrays. 
- If we check the middle element of both arrays, we have have three cases: (1) k is less than the number of elements in the first two halves of both arrays. In this case we can eliminate the top half of the array with the higher middle number because k can not appear in this half. (2) k is greater than the number of elements in the first two halves. In this case we can eliminate the bottom half of the array with the smaller middle number because k can not be in this half. (3) k is equal to the elements in the halves of both arrays, in this case the k smallest number is the max of the two middle numbers. 
- Notice that at every operation we are eliminating half of one of the lists, though we can not be too certain which list. This makes our algorithm $O(\log m+n)$.