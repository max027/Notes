Competitive programming combines two topics: (1) the design of algorithms and (2) the implementation of algorithms.
* The design of algorithms consists of problem solving and mathematical thinking. 
* The implementation of algorithms requires good programming skills.

# Time complexity
The time complexity of an algorithm estimates how much time the algorithm will use for some input.
## Calculation rules
The time complexity of an algorithm is denoted O(· · · ) where the three dots represent some function. Usually, the variable n denotes the input size

### Loops
A common reason why an algorithm is slow is that it contains many loops that go through the input.  The more nested loops the algorithm contains, the slower it is.
* If there are k nested loops, the time complexity is O(nk)

### Phases
If the algorithm consists of consecutive phases, the total time complexity is the largest time complexity of a single phase.
The reason for this is that the slowest phase is usually the bottleneck of the code.
For example, the following code consists of three phases with time complexities
O(n), O(n2) and O(n). Thus, the total time complexity is O(n2)

* An algorithm is polynomial if its time complexity is at most O(nk) where k is a constant.


