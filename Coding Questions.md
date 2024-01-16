### Coding Interview Questions:

Certainly! Here are the implementations along with written explanations for each of the coding and problem-solving questions:

### 1. Implement a function to check if a binary tree is a binary search tree:

```python
class TreeNode:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def is_binary_search_tree(node, min_val=float('-inf'), max_val=float('inf')):
    if not node:
        return True
    
    if not min_val < node.value < max_val:
        return False
    
    return (is_binary_search_tree(node.left, min_val, node.value) and
            is_binary_search_tree(node.right, node.value, max_val))
```

**Explanation:**
This function checks if a binary tree is a binary search tree by recursively traversing the tree and ensuring that each node's value is within the specified range (min_val to max_val).

---

### 2. Solve the "Reverse a Linked List" problem:

```python
class ListNode:
    def __init__(self, value):
        self.value = value
        self.next = None

def reverse_linked_list(head):
    prev = None
    current = head

    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node

    return prev
```

**Explanation:**
This function reverses a linked list by iteratively traversing it and reversing the direction of pointers. It uses three pointers (prev, current, next_node) to reverse the links between nodes.

---

### 3. Implement a stack using arrays or linked lists:

```python
# Using list as a stack
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.is_empty():
            return self.items.pop()

    def is_empty(self):
        return len(self.items) == 0

# Using linked list as a stack
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class StackLinkedList:
    def __init__(self):
        self.top = None

    def push(self, item):
        new_node = Node(item)
        new_node.next = self.top
        self.top = new_node

    def pop(self):
        if not self.is_empty():
            popped_item = self.top.value
            self.top = self.top.next
            return popped_item

    def is_empty(self):
        return self.top is None
```

**Explanation:**
These implementations demonstrate how to create a stack using either a list or a linked list. The stack follows the Last In, First Out (LIFO) principle, where elements are added and removed from the same end.

---

### 4. Write a function to find the intersection of two arrays:

```python
def intersection(nums1, nums2):
    set1 = set(nums1)
    set2 = set(nums2)
    return list(set1.intersection(set2))
```

**Explanation:**
This function finds the intersection of two arrays using Python sets. It converts the arrays to sets and then uses the intersection method to find common elements.

---

### 5. Implement a basic regular expression matcher:

```python
def is_match(s, p):
    import re
    return bool(re.fullmatch(p, s))
```

**Explanation:**
This function checks if a given string `s` matches a pattern `p` using Python's regular expression library (`re`). It returns `True` if there is a full match and `False` otherwise.

---

### 6. Solve the "Maximum Subarray" problem using Kadane's algorithm:

```python
def max_subarray(nums):
    max_sum = current_sum = nums[0]

    for num in nums[1:]:
        current_sum = max(num, current_sum + num)
        max_sum = max(max_sum, current_sum)

    return max_sum
```

**Explanation:**
This function solves the "Maximum Subarray" problem using Kadane's algorithm. It iterates through the array, keeping track of the current sum and the maximum sum encountered so far.

---

### 7. Implement a thread-safe singleton pattern:

```python
import threading

class Singleton:
    _instance = None
    _lock = threading.Lock()

    def __new__(cls):
        with cls._lock:
            if not cls._instance:
                cls._instance = super().__new__(cls)
            return cls._instance
```

**Explanation:**
This implementation demonstrates a thread-safe singleton pattern. The `_lock` ensures that only one thread can create an instance of the class at a time, preventing multiple instances from being created in a multi-threaded environment.

---

### 8. Write a function to detect a cycle in a directed graph:

```python
from collections import defaultdict

def has_cycle(graph):
    visited = set()
    stack = set()

    def dfs(node):
        visited.add(node)
        stack.add(node)

        for neighbor in graph[node]:
            if neighbor not in visited:
                if dfs(neighbor):
                    return True
            elif neighbor in stack:
                return True

        stack.remove(node)
        return False

    for node in graph:
        if node not in visited:
            if dfs(node):
                return True

    return False
```

**Explanation:**
This function detects a cycle in a directed graph using depth-first search (DFS). It maintains two sets (`visited` and `stack`) to keep track of visited nodes and the current path. If a node is encountered that is already in the stack, a cycle is detected.

---

### 9. Implement an LRU (Least Recently Used) cache:

```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.capacity = capacity
        self.cache = OrderedDict()

    def get(self, key):
        if key in self.cache:
            # Move the accessed key to the end
            self.cache.move_to_end(key)
            return self.cache[key]
        else:
            return -1

    def put(self, key, value):
        if len(self.cache) >= self.capacity:
            # Remove the least recently used key
            self.cache.popitem(last=False)
        self.cache[key] = value
        # Move the new key to the end
        self.cache.move_to_end(key)
```

**Explanation:**
This implementation demonstrates an LRU cache using Python's `OrderedDict`. It maintains a fixed-size cache and uses the `OrderedDict` to keep track of the order of key insertions. When the cache reaches its capacity, it removes the least recently used item.

---

### 10. Solve the "String Compression" problem:

```python
def compress_string(s):
    result = []
    count = 1

    for i in range(1, len(s)):
        if s[i] == s[i - 1]:
            count += 1
        else:
            result.append(s[i - 1] + str(count))
            count = 1

    result.append(s[-1] + str(count))

    compressed = ''.join(result)
    return compressed if len(compressed) < len(s) else s
```

**Explanation:**
This function compresses a string by counting consecutive occurrences of characters. It iterates through the string