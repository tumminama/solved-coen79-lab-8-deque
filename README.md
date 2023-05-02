Download Link: https://assignmentchef.com/product/solved-coen79-lab-8-deque
<br>
In this project you implement a template deque class, similar to the STL’s deque. Although a deque could be easily implemented using a linked list, as we mentioned before, using arrays enables the storage of data in contiguous memory locations, which results in higher performance due to efficient utilization of cache memory. In this project you also implement an iterator class for deque.




The deque data structure has two main components:

<ul>

 <li><strong>Data blocks</strong>: Each block is an array of data values. Data blocks are added and removed when items are added or removed. Please note that all the data blocks have the same size.</li>

 <li><strong>An array of block pointers</strong>: All the entries of this array are initially NULL. When a data block is added, an entry of this array points to the new data block. In order to avoid frequent resizing of the array of block pointers, the pointer to the first block is allocated in the middle of this array. The reserve() function is provided for you in the given files.</li>

</ul>




<strong>Please note that the size of data blocks never changes.</strong> However, by allocating a larger array of data pointers, more data blocks can be allocated to store more elements.




The initial size of the two arrays are:




<ol>

 <li><strong>Static</strong> <strong>const</strong> size_t BLOCK_SIZE = 5; // Number of data items per data block</li>

 <li><strong>static</strong> <strong>const</strong> size_t BLOCKPOINTER_ARRAY_SIZE = 5; // Number of entries in the array of block pointers. The minimum acceptable value is 2.</li>

</ol>




<strong>Before implementing the functions, you should completely understand the pointers used. </strong>




Two pointer variables point to the array of block pointers:




<ol>

 <li>// A pointer to the dynamic array of block pointers 2. value_type** block_pointers; 3.</li>

 <li>// A pointer to the final entry of the array of block pointers</li>

 <li>value_type** block_pointers_end;</li>

</ol>




The first pointer points to the beginning of the array, and the second one points to the last entry of the array.




Two other pointer variables point to the first and last used entry of the array of block pointers:




<ol>

 <li>// A pointer to the first block pointer that is being used (i.e., points to a data block)</li>

 <li>value_type** first_bp;</li>

 <li></li>

 <li>// A pointer to the last block pointer that is being used</li>

</ol>










For example, assume the array of block pointers has 5 entries. Entry 2 of this array points to the first data block and entry 4 points to the last data block. In this case, first_bp and last_bp point to entry 2 and 4, respectively.







There are two pointers to point to the first and last element of the deque, which are stored in data blocks:




<ol>

 <li>value_type * front_ptr; // A pointer to the front element of the deque</li>

 <li>value_type * back_ptr; // A pointer to the back element of the deque</li>

</ol>







<strong>In addition to the deque class, we implement a forward iterator.</strong> The forward iterator supports these operators: prefix ++, postfix ++, dereferencing *, equality ==, not equal !=

The set of pointer variables of the iterator class is similar to the deque class. However, in addition to those, the iterator class needs a cursor that moves towards the end of the deque. We also need to keep track of the current data block as well as the last entry of the data block. These three pointers enable us to move the cursor and jump from one data block to another when necessary.




<strong>The provided files include comments to simplify the implementation of functions. Please read these comments carefully. </strong>







As mentioned in the lectures, the implementation file of template classes should be included in the header file. However, in this project, we implement functions in header files. Therefore, we have one file for the deque class and one file for the deque iterator.


