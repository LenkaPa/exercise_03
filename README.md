# Computational Complexity

## Computational Complexity
### Task 1
* Calculate the computational complexity of this code segment.

```
1   for r ← 1 to m
2     for s ← 1 to n
3       count ← 0
4       for t ← 1 to k
5         if seq(r, s) = bases(t)
6           count ← count + 1
7       if count = 0
8         bases(k + 1) ← seq(r, s)
9         k ← k + 1
```

## Selection Sort
The following algorithm, called Selection Sort, is a naive but simple iterative 
method to solve the sorting problem. First, Selection sort finds the
smallest element in the list of integers, and moves it to the first position by swapping it with
whatever happens to be in the first position. Next, Selection sort
finds the second-smallest element in the list, and moves it to the second position,
again by swapping with value in the second position. At the *i*<sup>th</sup> iteration, Selection sort finds the *i*<sup>th</sup>
smallest element in the list, and moves it to the *i*<sup>th</sup> position.

### Task 2
* In R, implement the function `IndexOfMin()` according to the following pseudocode.

* Input:
    * a list of integers
    * an index of the first position
    * an index of the last position

* Output:
    * an index of the smallest element of the list between the first and last index

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size. 


IndexOfMin <- function(array, first, last) {
  index <- first
  for (k in (first + 1):last) {
    if (array[k] < array[index]) {
      index <- k
    }
  }
  return(index)
}

v <- c(7, 3, 9, 1, 5)
IndexOfMin(v, 1, length(v))


### Task 3 
* In R, implement the function `SelectionSort()` according to the following pseudocode.

* Input:
    * a list of integers
    * a count of integers in the list

* Output:
    * a sorted list of integers

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size.
* Determine the *O* notation.

SelectionSort <- function(array, n) {
  for (i in 1:(n - 1)) {
    j <- IndexOfMin(array, i, n)
    
    # Swap array[i] and array[j]
    temp <- array[i]
    array[i] <- array[j]
    array[j] <- temp
  }
  return(array)
}

v <- c(64, 25, 12, 22, 11)
sorted_v <- SelectionSort(v, length(v))
print(sorted_v)

### Task 4
* In R, implement the function `RecursiveSelectionSort()` according to the following pseudocode.

* Input:
    * a list of integers
    * an index of the first position
    * an index of the last position

* Output:
    * a sorted list of integers

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size.
* Determine the *O* notation.
* Decide which algorithm (`SelectionSort()` or `RecursiveSelectionSort()`) algorithm is more efficient.

RecursiveSelectionSort <- function(array, first, last) {
  if (first < last) {
    # Find index of smallest element in current range
    index <- IndexOfMin(array, first, last)
    
    # Swap array[first] and array[index]
    temp <- array[first]
    array[first] <- array[index]
    array[index] <- temp
    
    # Recursively sort the remainder of the array
    array <- RecursiveSelectionSort(array, first + 1, last)
  }
  return(array)
}

v <- c(29, 10, 14, 37, 13)
sorted_v <- RecursiveSelectionSort(v, 1, length(v))
print(sorted_v)



## Download files from GitHub
<details>
<summary>Basic Git settings</summary>

>* Configure the Git editor
>    ```bash
>    git config --global core.editor notepad
>    ```
>* Configure your name and email address
>    ```bash
>    git config --global user.name "Zuzana Nova"
>    git config --global user.email z.nova@vut.cz
>    ```
>* Check current settings
>    ```bash
>    git config --global --list
>    ```
>
</details>

* Create a fork on your GitHub account. 
  On the GitHub page of this repository find a <kbd>Fork</kbd> button in the upper right corner.
  
* Clone forked repository from your GitHub page to your computer:
```bash
git clone <fork repository address>
```
* In a local repository, set new remote for a project repository:
```bash
git remote add upstream https://github.com/mpa-prg/exercise_03.git
```

#### Send files to GitHub
Create a new commit and send new changes to your remote repository.
* Add file to a new commit.
```bash
git add <file_name>
```
* Create a new commit, enter commit message, save the file and close it.
```bash
git commit
```
* Send a new commit to your GitHub repository.
```bash
git push origin main
```
