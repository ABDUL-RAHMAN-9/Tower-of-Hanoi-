# Tower-of-Hanoi

Tower of Hanoi is mathematical puzzle in which we have 3 rods and n disks. First, all the disks are arranged in first rod from larger disk to smaller disk. We have to move all the disk from the first disk to last disk in same arrangement from larger to smaller.

## Rules of Tower of Hanoi
There are following rules in Tower of Hanoi:

- Only one disk can be moved at one point of time.
- Smaller disk can be placed above larger disk, but larger disk cannot be placed above smaller disk.

<div align='center'>
   <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240603113914/tower-of-hanoi-in-cpp.gif">
</div>


In this article, we will learn how to implement the Tower of Hanoi algorithm in C++.

## Tower of Hanoi Implementation in C++
In C++, we can solve the tower of Hanoi puzzle by both recursivley or iteratively. Below is the algorithm for recursive solution of tower of hanoi. For iterative solution, refer to the article Iterative Tower of Hanoi.


## Algorithm
Create a recursive function that takes the four arguments:

- Number of Disks (n)
- Source Rod (s_rod)
- Destination Rod (d_rod)
- Auxiliary Rod (a_rod)

In this function,

- If there's only one disk:
  - Print the move for the single disk.
  - Return from the function.
- If there are more than one disks:
  - Call the towerOfHanoi function to move n-1 disks from the source rod to the auxiliary rod 
   using the destination rod.
  - Print the move for the nth disk from the source rod to the destination rod.
  - Call the towerOfHanoi function to move n-1 disks from the auxiliary rod to the destination rod using the source rod.
 
# Code:

```
// C++ program to illustrate how to implement the tower of
// hanoi algorithm
#include <iostream>

using namespace std;

// Create a recursive function for Tower of Hanoi
void towerOfHanoi(int n, char s_rod, char d_rod, char a_rod)
{
    // If there's only one disk
    if (n == 1) {
        // Print the move for the single disk
        cout << "Move disk 1 from rod " << s_rod
             << " to rod " << d_rod << endl;
        return;
    }

    // If there are more than one disks
    // Call the towerOfHanoi function to move n-1 disks from
    // the source rod to the auxiliary rod using the
    // destination rod
    towerOfHanoi(n - 1, s_rod, a_rod, d_rod);

    // Print the move for the nth disk from the source rod
    // to the destination rod
    cout << "Move disk " << n << " from rod " << s_rod
         << " to rod " << d_rod << endl;

    // Call the towerOfHanoi function to move n-1 disks from
    // the auxiliary rod to the destination rod using the
    // source rod
    towerOfHanoi(n - 1, a_rod, d_rod, s_rod);
}

int main()
{
    // Number of disks
    int n = 3;

    // Call the Tower of Hanoi function
    towerOfHanoi(n, 'A', 'C', 'B');

    return 0;
}
```
## Output: 

```
Move disk 1 from rod A to rod C
Move disk 2 from rod A to rod B
Move disk 1 from rod C to rod B
Move disk 3 from rod A to rod C
Move disk 1 from rod B to rod A
Move disk 2 from rod B to rod C
Move disk 1 from rod A to rod C
```

## Complexity:

```
Time Complexity: O(2n)
Space Complexity: O(n)
```
