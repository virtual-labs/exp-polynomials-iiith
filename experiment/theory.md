### The Array Data Structure

    In this framework, we now see the array as a data structure. The typical operations on this data structure are as follows:

    ♦ to create an array data structure, called create(name, size),
    ♦ to access the element at a given index i, called ElementAt(index, name),
    ♦ to find the size of the array, called size(name), and
    ♦ to print the contents of the array, called print(name).

    While we are used to writing A[i] to access element i of an array A, it can be seen as the way to access the ith element in a non-object oriented programming language. The other operations are also not explicity specified when one uses languages such as C. But, when one considers purely object oriented languages, such operations are required to be supported. Similarly, in C, array creation is done by malloc() or a compile time declaration as int A[10];. However, when one looks at a data structure in terms of its operations, a create() operation is required.
    Linked lists are useful to study for two reasons.
        Most obviously, linked lists are a data structure which you may want to use in real programs. Seeing the strengths and weaknesses of linked lists will give you an appreciation of the some of the time, space, and code issues which are useful to thinking about any data structures in general.

        Somewhat less obviously, linked lists are great way to learn about pointers. In fact, you may never use a linked list in a real program, but you are certain to use lots of pointers. Linked list problems are a nice combination of algorithms and pointer manipulation. Traditionally, linked lists have been the domain where beginning programmers get the practice to really understand pointers.

###    Application of linked lists is to polynomials
   
 We now use linked lists to perform operations on polynomials.

    Let f(x) = Σdi=0 aixi.
    The quantity d is called as the degree of the polynomial, with the assumption that ad not equal to 0. A polynomial of degree d may however have missing terms i.e., powers j such that 0 <= j < d and aj = 0.
    The standard operations on a polynomial are addition and multiplication. If we store the coefficient ofeach term of the polynomials in an array of size d + 1, then these operations can be supported in a straightforwardway. However, for sparse polynomails, i.e., polynomials where there are few non-zero coefficients, this is not efficient. One possible solution is to use linked lists to store degree, coefficient pairs for non-zero coefficients. With this representation, it makes it easier if we keep the list of such pairs in decreasing order of degrees. A polynomial is a sum of terms. Each term consists of a coefficient and a (common) variable raised to an exponent. We consider only integer exponents, for now.
    Example: 4x3 + 5x − 10.

    How to represent a polynomial? Issues in representation, should not waste space, should be easy to use it for operating on polynomials. Any case, we need to store the coefficient and the exponent.
    struct node
    {
    float coefficient;
    int exponent;
    struct node *next;
    }

    Can we use a linked list?. Each node of the linked list stores the coefficient and the exponent. Should also store in the sorted order of exponents.

    Let us now see how two polynomials can be added. Let P1 and P2 be two polynomials stored as linked lists in sorted (decreasing) order of exponents

    The addition operation is defined as follows. Add terms of like-exponents. We have P1 and P2 arranged in a linked list in decreasing order of exponents.

    We can scan these and add like terms. Need to store the resulting term only if it has non-zero coefficient. The number of terms in the result polynomial P1+P2 need not be known in advance. We'll use as much space as there are terms in P1+P2.

    Adding polynomials :
    (3x5 − 9x3 + 4x2) + (−8x5 + 8x3 + 2)
    = 3x5 − 8x5 − 9x3 + 8x3 + 4x2 + 2
    = −5x5 − x3 + 4x2 + 2

    Multiplying polynomials:
    (2x − 3)(2x2 + 3x − 2)
    = 2x(2x2 + 3x − 2) − 3(2x2 + 3x − 2)
    = 4x3 + 6x2 − 4x − 6x2 − 9x+ 6
    = 4x3 − 13x+ 6

#### Why Linked Lists?

    Linked lists and arrays are similar since they both store collections of data. The terminology is that arrays and linked lists store "elements" on behalf of "client" code. The specific type of element is not important since essentially the same structure works to store elements of any type. One way to think about linked lists is to look at how arrays work and think about alternate approaches.
    The disadvantages of arrays are...
            The size of the array is fixed to some elements. Most often this size is specified at compile time with a simple declaration such as in the example above . With a little extra effort, the size of the array can be deferred until the array is created at runtime, but after that it remains fixed. (extra for experts) You can go to the trouble of dynamically allocating an array in the heap and then dynamically resizing it with realloc(), but that requires some real programmer effort.
            Because of (1), the most convenient thing for programmers to do is to allocate arrays which seem "large enough". Although convenient, this strategy has two disadvantages:
            a)most of the time there are just 20 or 30 elements in the array and 70% of the space in the array really is wasted.
            b) If the program ever needs to process more than fixed size, the code breaks. A surprising amount of commercial code has this sort of naive array allocation which wastes space most of the time and crashes for special occasions. (Extra for experts) For relatively large arrays (larger than 8k bytes), the virtual memory system may partially compensate for this problem, since the "wasted" elements are never touched.
            Inserting new elements at the front is potentially expensive because existing elements need to be shifted over to make room.


