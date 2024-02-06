2024/02/05 20:36
Status: #idea
Tags:

# Bubble Sort

Math way to say that an array is sorted

for any array where i is the index of an array this should be true

$X_i <= X_{i+1}$

![[Pasted image 20240205204505.png]]

bubble sort will iterate through an array and check if the current index it is on it greater than the next index in the array and if it is it will swap their positions. This also means that the largest number in the array will always be placed in the back of the array. meaning on the next iteration of the array you can exclude the final element in the array.

The time complexity of this algorithm is a bit confusing to me and I should look into it more but it is: 

$O(n^2)$

![[Pasted image 20240205204813.png]]

here is primeagen's example

---
# References
