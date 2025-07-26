
### arrays
- two pointers
- sliding window
- max subarray sum (kadame algo)
- leetcode -- sort an array of 0's 1's 2's
- subsets(recursion)
- transpose
- 90 degree of the matrix
- spiral order traversal
### stack
- valid parenthesis
- monotonic stack (next greater element , next smaller element)
- clumsy factorial
- 

### bit manipulation
- count number of set bits
- set/unset bit
- XOR
- negative numbers on bits

### binary search
- on rotated array
- on answer space( koko eating bananas, min days to make m bouquets)
- implementing upper/lower bound

### sorting algo
- insertion
- bubble
- selection
- merge

### trees
- all traversals
- height ( diameter, depth, max path sum)
- Lowest common ancestor
- build tree from inorder/ preorder or other traversals
- ~~morris~~ traversals

### graphs
- BFS/DFS on grids as well
- cycle detection
- no of connected islands
- topological sorting
- Shortest path algo (djikstra )
- MST : prime

### DP
 - 0/1 knapsack
 - DP on subseq
 - DP on stocks
 - Dp on subsets
 - DP on grids
### tries
- dictionary
- dial pad
- creation , insertion

### linkedlist
- creation , deletion, insertion
- reverse linkedlist
- cycle linkedlist
- intersection of two linkedlist

### BST
- Insertion, deletion 
- insert or delete kth node
- LCA in BST

### Strings
- longest increasing/decreasing 
- palindromes
- anagrams
- roman to integer
- integer to roman
- patter matching

### heap(using priority queue)
- 




























# leetcode 

## 2001. Number of Pairs of Interchangeable Rectangles

### not optimized
```java
class Solution {
public long interchangeableRectangles(int[][] rec) {
long k=0;
long row=rec.length;
for(int i=0;i<row;i++){
float b=(((float)rec[i][0])/((float)rec[i][1]));
for(int j=i+1;j<row;j++){
if(b==(((float)rec[j][0])/((float)rec[j][1]))){
k+=1;
}
}
}
return k;
}
}
```

## 493. Reverse pairs

```java
class Solution {
public int reversePairs(int[] nums) {
int k=0;
for(int i=0;i<nums.length;i++){
for(int j=i+1;j<nums.length;j++){
if(nums[i]/2.0>nums[j]){
k++;
}
}
}
return k;
}
}```

[whenever there is multiplication concept applied try to apply division to it ]



##  496. Next Greater Element I




## 503. Next Greater Element II

```java
 class Solution {
public int[] nextGreaterElements(int[] nums) {
int ar[]=new int[nums.length];
boolean b;
for(int i=0;i<nums.length;i++){
b=true
ar[i]=-1;
for(int j=i+1;j<nums.length;j++){
if(nums[j]>nums[i]){
ar[i]=nums[j];
b=false;
break;
}
}
if(b){
for(int j=0;j<i;j++){
if(nums[j]>nums[i]){
ar[i]=nums[j];
break;
}
}
}
}
return ar;
}
}
```


### can also use doubling of array 

[1,2,3,4] ==> [1,2,3,4,1,2,3,4]

## 


## 796 Rotate String
```c++
bool rotateString (char* s1,char* s2){
if(strlen(s1) != strlen(s2))return 0;
char temp[strlen(s1)*2+1];
return !!strlen(strcat(strcpy(temp,s1),s1),s2);
}
```

## most asked qn
```c
int ar[3][4]={{4,14,24,34},{6,16,26,36},{9,19,29,39}}
```
		print the 2D array using only one loop and woithout using if




# Find minimum in rotated and sorted array





# 875. koko eating banana





# Find length of string without using extra variable and printf in C;
```c
int length(char*s){
if(*s=='\0'){return 0;}
return 1+length(s+1);
}
```

# count nodes in a tree
```c
int nn(Node * root){
if(root==null){
return 0;
}
int l=nn(root->left);
int r=nn(root->right);
return 1+l+r;
}
```