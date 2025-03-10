[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/tqM-lrvp)
# CMPS 2200  Recitation 01

**Name (Team Member 1):** Madeline Davis 
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [x] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [x] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [x] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [x] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?
      
The worst case for linear search is when the key is not in the list or when it is in the last position. This means that the algorthim check every position. This means that the worst case is $O(n)$. The worst case for binary search is also when the key is not there or the key is in a position that causes it to divide and make the max number of comparisons. The worst case for binary search is $O(log_2(n))$

- [x] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

The best case input for the key for linear search would be when it is the first index. The best case for the key for binary search is when it is the index exactly in the middle. Both of these would have a complexity of $O(1)$. 

- [x] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [x] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [x] 8. Call `print_results(compare_search())` and paste the results here:


|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.003 |    0.004 |
|      100 |    0.005 |    0.002 |
|     1000 |    0.037 |    0.002 |
|    10000 |    0.759 |    0.005 |
|   100000 |    4.285 |    0.005 |
|  1000000 |   46.334 |    0.015 |
| 10000000 |  475.885 |    0.024 |

 

- [x] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

I would say the empirical results roughly follows the theoretical running times. For linear we see that the time gets about 10 times longer as we increase by a power of 10. This would be $O(n)$ because it increase at the rate that n increases. The binary case is a bit more complicated to calculate mathematically We can time increases much slower and $O(log_2(n))$ does increase at a slower rate than $O(n)$. $log_2(10^2)$ is about 7 and $log_2(10^4)$ is about 14 so it should double it that time. Our results do roughtly that. I think the reason there are some empirical results that do not align with the theoretical run time (i.e. Binary (10, 100, 1000)) is because they all happen so quickly so recording the difference is very challenging for a computer.

- [x] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search?
    
$O(kn)$

  + For binary search?
  
$O(klog_2(n) +n^2)$

  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting?

It is more efficient to use binary search and sort the list than to just use linear searh without sorting  when $k$ > $n$.
