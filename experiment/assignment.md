### Basic Problems

1. In a standard linked list, you can only traverse the list in one direction. Using doubly linke list it may be useful however, to be able to go both forwards and backwards.The only difference here compared to the Node class we used for a standard linked list is an extra reference prev.  

2. The variations from the standard linked list is Circular linked list. The only difference between here and a standard linked list is that the next component of the last node in the list references the first node in the list. One of the main issues to keep track of here is making sure that you don't iterate through the list forever, (since no next reference in the entire list will ever be null.)  

3. A stack and a queue can be implemented using an array. However,the fact that one has to specify upfront the maximum number of elements that the stack can contain, is a limitation. To overcome that problem, one can use a linked list to implement a stack.Recall that a stack is a last-in-first-out based data structure. When using a linked list to support a stack, we should know how to translate push() and pop() of stack to linked list operations.We now would be seeing an implementation of an ADT using another ADT. The head of the list can be thought of pointing to the top of the stack. The Push operation adds an element to the list at the head.The Pop operation deletes the element at the head of the list.The push() operation can simply be translated to an insert at the beginning of the list. This suggests that pop would simply be translated to a remove operation at the front of the list.Does this keep the LIFO order ? Check it.  

4. For a queue however, we need both the front and the rear. For this purpose, one can think of maintaining both the head and the tail of the list. The front of the queue can be the tail and the rear of the queue can be the head of the list.Which kind of linked list to use?A doubly linked list may help.It has a head and a rear identical to the front and rear of a queue.Can then translate queue operations Insert and Delete into insert and remove operations on a doubly linked list.  

### Easy Problems  

1. Write a program to reverse the contents of a singly linked list. Your program cannot use any additional space beyond O(1) space.  

2. Implement the following set operations using linked lists. A set S is represented using a linked list by having one element of the set in each node. For instance, S = {12, 17, 9, 22} is represented as head->12->17->9->22. The universe is the set of positive integers. Now, write programs to :  
   (a) compute the union of two sets S1 and S2. The output is a new list S that contains elements in S1 U S2.  
   (b) compute the intersection of two sets S1 and S2. The output is a new list that contains the elements in S1 interesect S2.  
   (c) the difference of sets S1 and S2.  

3. Given a linked list L with n nodes and a permutation P of the first n integers. Write a program to output a linked list L' so that the i^th element in L is at position P(i) in L'. An example is given below. Let L be 1->3->8->5. Let P be (4,1,2,3). Then L' should be 3->8->5->1. Print output (L') for each test case on seperate lines.  

### Difficult Problems

1. A sparse matrix is matrix where each row has very few nonzero elements. Therefore, it is not worthwhile to store a sparse matrix in a two -dimensional array as most of the array would be unused. There are several ways to represent sparse matrices. One of them is to use the Compressed Sparse Row (CSR) format where there are 3 arrays, say data, cols, and ptr. The data array contains all the values of the nonzero elements. The cols array contains the indices of the columns that contain nonzero elements. Indices of a row are kept in contiguous positions and in sorted order of column indices. In the ptr array of size n, ptr[i] contains the index of the first element of nonzero elements of row i. Further, elements of row i are stored in the cols array before elements of row i+1. With the above representation, write a program to add two sparse matrices and multiply two sparse matrices. The output should also be written in the same format as the input.  

2. Read Problem 4 for bakcground on sparse matrices. There are several ways to represent sparse matrices. One way is to store the nonzero elements of each row in a linked list. Each element of the list contains a column index and the value of the corresponding nonzero element. Use the above representation to write programs to add and multiply two sparse matrices. The output matrix should be represented in the same format. You are also not allowed to convert from this representation to other representations.  

