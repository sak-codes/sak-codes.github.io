# My Google Summer of Code Journey – Extending Data Structures, Algorithms, and the C++ Backend

## Introduction: A Summer of Growth, Code, and Algorithms

Hello, world! 👋  
I’m Sakshi Oza, a Master's student passionate about data-science, open-source software, and algorithms. This summer, I had the incredible privilege to work with Google Summer of Code (GSoC) 2023 on a project titled: "Extending the data structures, algorithms, and providing C++ backend".

If you’ve ever wondered how Python libraries can achieve C++-level performance while implementing advanced algorithms, this blog is for you. I’ll share my GSoC journey, including challenges, solutions, and learnings.


## About the Project

The project focused on enhancing a Python-based data structures library, `pydatastructs` by:  
1. Extending existing data structures and algorithms.  
2. Implementing optimized algorithms for better functionality.  
3. Introducing a C++ backend to improve performance-critical operations.

This combination bridges the gap between Python’s developer-friendliness and C++’s computational efficiency.


## Breaking It Down: My GSoC Timeline

### 🔹 Community Bonding Period
Before coding began, I focused on:  
- Understanding the existing codebase and architecture.  
- Discussing goals and roadmaps with my mentors:  
  - Gagandeep Singh  
  - Smit Lunagariya  
  - Ivan Ogasawara

I explored the gaps in the current implementation and set milestones for my contributions.


### 🔹 Phase 1: Extending Existing Algorithms and Structures

1. Network Flow Algorithms  
   - Implemented Edmond-Karp and Dinic’s algorithms to solve maximum flow problems.  
   - These algorithms are critical for network routing, resource allocation, and optimization problems.

2. Binary Search Tree (BST) Enhancements  
   - Added lower_bound and upper_bound methods for range-based queries.  
   - These methods mimic the functionality of C++ STL, offering faster lookups.  

   Example Code:
   ```python
   from pydatastructs import BinarySearchTree

   bst = BinarySearchTree()
   bst.insert(10)
   bst.insert(20)
   bst.insert(30)
   print(bst.lower_bound(15))  # Output: 20
   ```

### 🔹 Phase 2: Bringing the C++ Backend to Life

In Phase 2, I focused on backend optimization by implementing a C++ backend for performance-critical algorithms. Why? Python is fantastic for development, but when it comes to heavy computation, C++ shines. By combining the two, we achieve the best of both worlds.


### Key Contributions in this Phase

#### 1. Sorting Algorithms  
- Added bubble_sort, selection_sort, and insertion_sort with C++ backend support.  
- This dramatically improved the speed of sorting operations.

    Example Code:
    ```python
    from pydatastructs import OneDimensionalArray, Backend, bubble_sort

    arr = OneDimensionalArray(int, [5, 3, 8, 1])
    bubble_sort(arr, backend=Backend.CPP)
    print(arr)  # Output: [1, 3, 5, 8]
    ```

### 2. Search Algorithms 
Implemented efficient linear_search, binary_search, and jump_search algorithms using C++.  
These methods are fundamental and heavily used across various applications.


### 3. Lazy Segment Tree
Introduced a lazy segment tree to handle range-based queries and updates efficiently.  
Segment trees are invaluable for applications like interval management and range sum/count queries.


## Challenges and Learnings

### 1. Network Flow Complexity  
Implementing Edmond-Karp and Dinic’s algorithms required a deep understanding of graph theory, BFS, and DFS.  
I spent significant time dissecting these algorithms before achieving clean implementations.

### 2. Python-C++ Integration 
Integrating C++ code into a Python library was a new challenge.  
I explored Cython and other backend options to ensure seamless interoperability without compromising performance.

### 3. Writing Clean, Optimized Code
- Ensured my code followed best practices: modularity, readability, and speed.  
- Wrote comprehensive test cases for every addition to ensure robustness.


## Memes from the Journey

1. When Network Flow Started Making Sense  
*“When theory meets implementation, and it finally clicks.”*

2. Debugging My C++ Backend  
*“C++ segmentation fault: Where is the bug? Not here, not there... oh wait, everywhere!”*

3. Submitting My Final PR  
*“Months of hard work, countless commits, and it all comes down to one button: Merge PR.”*


## Impact: Why This Matters

The contributions I made during GSoC 2023 will:  
1. Enhance library performance through optimized algorithms.  
2. Expand library utility with new data structures and methods.  
3. Improve scalability with a C++ backend for heavy computations.


## Gratitude

I’m incredibly grateful to my mentors:  
- Gagandeep Singh  
- Smit Lunagariya  
- Ivan Ogasawara  

Their guidance, patience, and feedback were invaluable throughout this project. I also want to thank the GSoC community for fostering such a collaborative and supportive environment.


## Conclusion: A Summer to Remember

GSoC 2023 was a transformative experience. From grappling with network flows to integrating C++ backends, I grew as a developer and problem solver. This project has not only strengthened my technical skills but also deepened my appreciation for open-source contributions.

I’m excited to continue my open-source journey, contribute more, and keep growing as a developer.

Thank you for reading!  
“Keep coding, keep learning, and let’s build something amazing together!” 
