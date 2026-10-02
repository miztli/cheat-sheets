Collections API: List, Queue, Stack, Set, Map, Comparator.

### ArrayList
- Array-based data structure
- Supports index-based operations like searching, updating, and accessing elements O(1)
- Slow at element manipulation. For instance, adding an element to the start of the list
- Maintains insertion order
- When the internal array becomes full, a new larger array is created and elements are copied
- Best for frequent access and rare modifications

### LinkedList
- Nodes and addresses pointing to other Nodes
- Allows efficient insertion and deletion of elements from both ends O(1)
- Maintains insertion order
- Best for frequent insertions and deletions

### HashSet
- Unique elements
- Order is not guaranteed
- Operations like add, remove, contains are fast (O(1) on average
- Allows one null
- Backed by hash table for storage
- Best for fast access and no sorting required 

### TreeSet
- Unique elements
- Sorted in natural order or Comparator
- Backed by red-black tree (self-balancing binary search tree)
- Null elements not allowed
- Operations like add, remove, contains take O(log n) due to tree traversal.
- Best when sorting required

### HashMap
- ONE null key is allowed and many null values. 
- Not synchronized. Thus, very performant.
- Java 1.2

### HashTable
- Null is not allowed for both key and value. Otherwise, we will get a null pointer exception.
- Every method is synchronized. Thus, low performance.
  - Java 1.0