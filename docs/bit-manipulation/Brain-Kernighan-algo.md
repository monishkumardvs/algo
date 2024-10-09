---
id: Brain kernighan algo
title: Bit Manipulation Technique
sidebar_label: Brain kernighan Algorithm
sidebar_position: 2
Description: Brian Kernighan’s Algorithm is an efficient method used to count the number of set bits (1s) in the binary representation of a number. It leverages the property of subtracting 1 from a number, which flips all the bits after the rightmost set bit (including the set bit itself). By performing a bitwise AND between n and n - 1, the rightmost set bit is cleared. This process is repeated until the number becomes zero.
tags: [DSA, Bit Manipulation, Technique]
---


 ### Brian Kernighan's Algorithm:
Brian Kernighan’s Algorithm is an efficient technique for counting the number of set bits (1s) in the binary representation of a number. This is commonly referred to as the Hamming Weight or population count.

### Key Concept:
When you subtract 1 from a number n, all the bits to the right of the rightmost set bit (including the rightmost set bit itself) are inverted. By performing a bitwise AND operation between n and n - 1, the rightmost set bit is cleared. You can repeat this process until the number becomes zero, and each operation effectively reduces the number of set bits by one.
Example:
For n = 13 (binary 1101):

n & (n - 1) = 1101 & 1100 → 1100 (1 set bit cleared)
n & (n - 1) = 1100 & 1011 → 1000 (1 set bit cleared)
n & (n - 1) = 1000 & 0111 → 0000 (1 set bit cleared)
The process terminates when all set bits have been cleared. In this case, 13 has 3 set bits.

### Algorithm Implementation in C++:
```cpp

int countSetBits(int n) {
    int count = 0;
    while (n) {
        n = n & (n - 1);  // Clear the rightmost set bit
        count++;
    }
    return count;
}
```

### Explanation:
Initialization: Set count to 0. This will store the number of set bits.
Loop: As long as n is not 0, perform the n = n & (n - 1) operation to clear the rightmost set bit, and increment count.
Termination: When n becomes 0, the loop stops, and count contains the number of set bits.
### Time Complexity:
The time complexity of Brian Kernighan's Algorithm is O(number of set bits), making it more efficient than looping through all bits for large numbers with fewer set bits.
Applications of Brian Kernighan’s Algorithm:
### Hamming Weight Calculation: 
Used in cryptography, data compression, and error detection codes to calculate the number of 1s in binary data.

## Efficient Bit Manipulation: 
This algorithm is more efficient than a brute-force approach that checks each bit individually.
Network Masking: Used in networking to count the number of set bits in IP address masks, crucial for subnetting and address allocation.

## Problem:
Given an integer n, count how many numbers between 1 and n (inclusive) have an odd number of set bits.

### Solution Outline:

Iterate through all numbers from 1 to n.
Use Brian Kernighan’s Algorithm to count the number of set bits for each number.
Check if the count is odd and keep track of how many numbers satisfy this condition.

## Code:
```cpp

int countOddSetBits(int n) {
    int oddCount = 0;
    for (int i = 1; i <= n; i++) {
        int setBits = countSetBits(i);
        if (setBits % 2 != 0) {
            oddCount++;
        }
    }
    return oddCount;
}
```
## Summary of Brian Kernighan’s Algorithm:
Efficient: Reduces the problem of counting set bits to just the number of 1s in the binary representation, not the total number of bits.

Practical: Widely used in various domains such as networking, cryptography, and performance-critical applications like game development.

Mastering Brian Kernighan's Algorithm is essential for developers dealing with performance-critical tasks involving bit manipulation.