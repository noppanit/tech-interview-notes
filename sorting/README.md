# Sorting

From my experience, I haven't had people asking me to implement any sorting algorithm on the spot. It's most likely going to be a problem that involves sorting for optimization. 

This is the list of sorting algorithms you might want to check it out.

1. Merge sort
2. Quick sort
3. Insertion sort
4. Heap sort

## Merge Sort

For example.
The classic problem; [Dutch national flag](https://en.wikipedia.org/wiki/Dutch_national_flag_problem).

``` python
def merge(left, right, nums):
    i = j = 0
    while i + j < len(nums):
        if j == len(right) or i < len(left) and left[i] < right[j]:
            nums[i + j] = left[i]
            i += 1
        else:
            nums[i + j] = right[j]
            j += 1


def merge_sort(nums):
    l = len(nums)

    if l < 2:
        return

    mid = l // 2
    left = nums[0:mid]
    right = nums[mid:l]

    merge_sort(left)
    merge_sort(right)
    merge(left, right, nums)


nums = [10, 9, 8, 7, 6, 5]
merge_sort(nums)
print(nums)
```

## Quick Sort

``` python
def quick_sort(nums):
    return sort(nums, 0, len(nums) - 1)


def partition(nums, low, high):
    i = low - 1
    pivot = nums[high]
    for j in range(low, high):
        if nums[j] < pivot:
            i += 1
            nums[i], nums[j] = nums[j], nums[i]
    nums[i + 1], nums[high] = nums[high], nums[i + 1]
    return i + 1


def sort(nums, low, high):
    if low < high:
        p = partition(nums, low, high)
        sort(nums, low, p - 1)
        sort(nums, p + 1, high)


nums = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
result = quick_sort(nums)
print(nums)
print(result)
```

## Insertion Sort

``` python
def insertionSort(alist):
    for i in range(1, len(alist)):
        position = i
        current_val = alist[position]
        while position > 0 and alist[position - 1] < current_val:
            alist[position] = alist[position - 1]
            position -= 1
        alist[position] = current_val


alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]
insertionSort(alist)
print(alist)
```


## Heap Sort

``` python
def heapify_max(nums, i):
    n = len(nums)
    largest = i
    l = 2 * i + 1
    r = l + 1

    if l < n and nums[i] < nums[l]:
        largest = l

    if r < n and nums[largest] < nums[r]:
        largest = r

    if largest != i:
        nums[i], nums[largest] = nums[largest], nums[i]

        heapify_max(nums, largest)


def heapify_min(nums, i):
    n = len(nums)
    smallest = i
    l = 2 * i + 1
    r = l + 1

    if l < n and nums[l] < nums[i]:
        smallest = l
    if r < n and nums[r] < nums[smallest]:
        smallest = r

    if smallest != i:
        nums[i], nums[smallest] = nums[smallest], nums[i]
        heapify_min(nums, smallest)


def heapsort(nums):
    for i in range(len(nums), -1, -1):
        heapify_min(nums, i)
        # heapify_max(nums, i)


nums = [12, 11, 20, 13, 5, 6, 7]
heapsort(nums)

from heapq import heappush

heap = []
for num in nums:
    heappush(heap, num)

print(nums)

```