# Recursion


## Linear Print

This program prints integers from 1 to 'n' using a linear print function implemented with recursion.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to print integers from 'cnt' to 'n' recursively
void linearprint(int cnt, int n) {
    // Base case: if 'cnt' exceeds 'n', return
    if (cnt > n)
        return;
    
    // Print the current integer 'cnt'
    cout << cnt << endl;
    
    // Increment 'cnt' and recursively call the function
    cnt++;
    linearprint(cnt, n);
}

int main() {
    int n;
    cin >> n; // Input the value of 'n'
    
    // Call the linearprint function with 'cnt' initially set to 1
    linearprint(1, n);
    
    return 0;
}
```
**Approach:**
- The program defines a function linearprint that takes two arguments: cnt (the current integer to print) and n (the upper limit).
- The function recursively prints integers from 'cnt' to 'n'.
- It has a base case where it returns if 'cnt' exceeds 'n'.
- In each recursive call, it prints the current integer 'cnt', increments 'cnt', and recursively calls the function with the incremented 'cnt'.
  
**Time Complexity:**
- The time complexity of the linear print function implemented with recursion is O(n), where 'n' is the value inputted by the user. This is because the function makes 'n' recursive calls, each performing constant-time operations (printing and incrementing).

## Recursive Print Function

This program prints a given string `n` times using a recursive function.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to print the string 'name' 'n' times recursively
void print(string name, int n) {
    // Base case: if 'n' is 0, return
    if (n == 0)
        return;
    
    // Print the string 'name'
    cout << name << endl;
    
    // Recursively call the function with 'n-1'
    print(name, n - 1);
}

int main() {
    string name;
    getline(cin, name); // Input the string to be printed
    int n;
    cin >> n; // Input the number of times the string should be printed
    
    // Call the print function with the input string and number of times
    print(name, n);
    
    return 0;
}
```

**Approach:**
- The program defines a function print that takes two arguments: name (the string to print) and n (the number of times to print the string).
- The function recursively prints the string 'name' 'n' times.
- It has a base case where it returns if 'n' is 0.
- In each recursive call, it prints the string 'name', decrements 'n', and recursively calls the function with the decremented 'n'.

**Time Complexity:**
- The time complexity of the print function implemented with recursion is O(n), where 'n' is the number of times the string is printed. This is because the function makes 'n' recursive calls, each performing constant-time operations (printing and decrementing).

## Linear Print (Descending Order)

This program prints integers from 'n' to 1 using a linear print function implemented with recursion.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to print integers from 'n' to 1 recursively
void linearprint(int n) {
    // Base case: if 'n' is less than 1, return
    if (n < 1)
        return;
    
    // Print the current integer 'n'
    cout << n << endl;
    
    // Recursively call the function with 'n-1'
    linearprint(n - 1);
}

int main() {
    int n;
    cin >> n; // Input the value of 'n'
    
    // Call the linearprint function with 'n'
    linearprint(n);
    
    return 0;
}
```
**Approach:**
- The program defines a function linearprint that takes one argument: n (the current integer to print).
- The function recursively prints integers from 'n' to 1.
- It has a base case where it returns if 'n' is less than 1.
- In each recursive call, it prints the current integer 'n', decrements 'n', and recursively calls the function with the decremented 'n'.
  
**Time Complexity:**
- The time complexity of the linear print function implemented with recursion is O(n), where 'n' is the value inputted by the user. This is because the function makes 'n' recursive calls, each performing constant-time operations (printing and decrementing).

## Reverse Array using Recursion

This program reverses an array using a recursive function.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to reverse the array 'arr' from index 'l' to index 'r' recursively
vector<int> reversearray(vector<int> arr, int l, int r) {
    // Base case: if 'l' is greater than or equal to 'r', return the array 'arr'
    if (l >= r)
        return arr;
    
    // Swap the elements at indices 'l' and 'r'
    swap(arr[l], arr[r]);
    
    // Recursively call the function with 'l+1' and 'r-1'
    return reversearray(arr, l + 1, r - 1);
}

int main() {
    vector<int> arr = {1, 2, 3, 4, 5}; // Input array
    arr = reversearray(arr, 0, arr.size() - 1); // Reverse the array
    for (int i = 0; i < arr.size(); i++) {
        cout << arr[i] << " "; // Print the reversed array
    }
    return 0;
}
```
**Approach:**
- The program defines a function reversearray that takes three arguments: arr (the array to be reversed), l (the left index), and r (the right index).
- The function recursively reverses the array elements between indices 'l' and 'r'.
- It has a base case where it returns the array 'arr' if 'l' is greater than or equal to 'r'.
- In each recursive call, it swaps the elements at indices 'l' and 'r', increments 'l', and decrements 'r'.
  
**Time Complexity:**
- The time complexity of the function to reverse an array using recursion is O(n), where 'n' is the number of elements in the array. This is because the function makes 'n/2' recursive calls, each performing constant-time operations (swapping elements).

## Recursive Product Calculation

This program calculates the product of two integers 'n' and 'i' using recursion.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to calculate the product of 'n' and 'i' recursively
int prod(int n, int i) {
    // Base case: if 'i' is 0, return 'n'
    if (i == 0)
        return n;
    
    // Recursively call the function with 'i-1' and multiply the result by 'n'
    return n * prod(n, i - 1);
}

int main() {
    int n, i;
    cin >> n; // Input the value of 'n'
    cin >> i; // Input the value of 'i'
    
    // Calculate the product of 'n' and 'i'
    int p = prod(n, i);
    
    // Output the result
    cout << p;
    
    return 0;
}
```

**Approach:**
- The program defines a function prod that takes two arguments: n (the first integer) and i (the second integer).
- The function recursively calculates the product of 'n' and 'i' by multiplying 'n' with the result of the function call with 'i-1'.
- It has a base case where it returns 'n' if 'i' is 0.
  
**Time Complexity:**
- The time complexity of the function to calculate the product of two integers using recursion is O(i), where 'i' is the value of the second integer. This is because the function makes 'i' recursive calls, each performing constant-time operations (multiplication).

## Recursive Sum Calculation (Parameterized Recursion)

This program calculates the sum of integers from 1 to 'n' using recursion.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to calculate the sum of integers from '1' to 'n' recursively
void sum(int i, int n) {
    // Base case: if 'i' is less than 1, print the sum 'n' and return
    if (i < 1) {
        cout << n;
        return;
    }
    
    // Recursively call the function with 'i-1' and update the sum by adding 'i' to 'n'
    sum(i - 1, n + i);
}

int main() {
    int n;
    cin >> n; // Input the value of 'n'
    
    // Call the sum function with 'n' and initial sum 0
    sum(n, 0);
    
    return 0;
}
```
**Approach:**
- The program defines a function sum that takes two arguments: i (the current integer to add) and n (the current sum).
- The function recursively calculates the sum of integers from 1 to 'n' by adding 'i' to the current sum 'n' and calling itself with 'i-1'.
- It has a base case where it prints the sum 'n' if 'i' is less than 1.
- 
**Time Complexity:**
- The time complexity of the function to calculate the sum of integers from 1 to 'n' using recursion is O(n), where 'n' is the value inputted by the user. This is because the function makes 'n' recursive calls, each performing constant-time operations (addition).

## Recursive Sum Calculation (Functional Recursion)

This program calculates the sum of integers from 1 to 'n' using recursion.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to calculate the sum of integers from 1 to 'n' recursively
int sum(int n) {
    // Base case: if 'n' is 0, return 0
    if (n == 0)
        return 0;
    
    // Recursively call the function with 'n-1' and add 'n' to the result
    return n + sum(n - 1);
}

int main() {
    int n;
    cin >> n; // Input the value of 'n'
    
    // Calculate the sum of integers from 1 to 'n'
    int s = sum(n);
    
    // Output the result
    cout << s;
    
    return 0;
}
```
**Approach:**
- The program defines a function sum that takes an integer 'n'.
- The function recursively calculates the sum of integers from 1 to 'n' by adding 'n' to the result of the function call with 'n-1'.
- It has a base case where it returns 0 if 'n' is 0.
  
**Time Complexity:**
- The time complexity of the function to calculate the sum of integers from 1 to 'n' using recursion is O(n), where 'n' is the value inputted by the user. This is because the function makes 'n' recursive calls, each performing constant-time operations (addition).

## Backtracking with Recursion

This program demonstrates backtracking using recursion to print numbers from '1' to 'n' in reverse order.

```cpp
#include<bits/stdc++.h>
using namespace std;

// Function to perform backtracking recursively
void backtrack(int i, int n) {
    // Base case: if 'i' is less than or equal to 0, return
    if (i <= 0)
        return;
    
    // Recursively call the function with 'i-1' and 'n' and print 'i'
    backtrack(i - 1, n);
    cout << i << endl;
}

int main() {
    int n;
    cin >> n; // Input the value of 'n'
    
    // Call the backtrack function with 'n' and 'n'
    backtrack(n, n);
    
    return 0;
}
```
**Approach:**
- The program defines a function backtrack that takes two integers 'i' and 'n'.
- The function recursively performs backtracking by decrementing 'i' until it reaches 0 and printing the value of 'i' at each step.
- It has a base case where it returns if 'i' is less than or equal to 0.
  
**Time Complexity:**
- The time complexity of the function to perform backtracking with recursion is O(n), where 'n' is the value inputted by the user. This is because the function makes 'n' recursive calls, each performing constant-time operations (printing a number).

## 509.Fibonacci Number 

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

- F(0) = 0, F(1) = 1
- F(n) = F(n - 1) + F(n - 2), for n > 1.
- Given n, calculate F(n).

```cpp
class Solution {
public:
    // Function to calculate the nth Fibonacci number recursively
    int fib(int n) {
        // Base cases: if 'n' is 0 or 1, return the respective Fibonacci number
        if (n == 0) return 0;
        if (n == 1) return 1;
        
        // Recursive step: return the sum of the (n-1)th and (n-2)th Fibonacci numbers
        return fib(n - 1) + fib(n - 2);
    }
};
```
**Approach:**
- The class Solution provides a method fib to calculate the nth Fibonacci number recursively.
- It defines base cases for 'n' equal to 0 and 1, where it returns 0 and 1 respectively.
- For other values of 'n', it recursively calculates the Fibonacci number by summing the (n-1)th and (n-2)th Fibonacci numbers.
  
**Time Complexity:**
- The time complexity of calculating the nth Fibonacci number using recursion is exponential, O(2^n), where 'n' is the input parameter. This is because each call to fib results in two recursive calls, leading to exponential growth in the number of function calls and redundant calculations.

