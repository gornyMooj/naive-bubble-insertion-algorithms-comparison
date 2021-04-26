# Comparison of naive, bubble & insertion algorithms

Counts how many iterations are needed to sort a random list with each of those 3 algorithms

```python
import random


def create_random_arrey(n,x,y):
    my_list = [random.randint(x, y) for i in range(n)]

    return my_list



def naive_sorting_algorithm(mylist):

    unsorted_list = list(mylist)
    sorted_list = []
    counter = 0
    while len(unsorted_list) > 0:
        smallest = unsorted_list[0]
        for i in unsorted_list:
            counter += 1
            if i <= smallest:
                smallest = i

        sorted_list.append(smallest)
        unsorted_list.remove(smallest)

    return sorted_list, counter



def bubble_sort_algorithm(my_list):

    bubble_list = list(my_list)
    counter = 0
    for j in range(len(bubble_list), 1, -1):
        for i in range(1, j):
            counter += 1
            if bubble_list[i - 1] > bubble_list[i]:
                bubble_list[i - 1], bubble_list[i] = bubble_list[i], bubble_list[i - 1]

    return bubble_list,counter



def insertion_sort_algorithm(my_list):
    insertion_list = list(my_list)
    counter = 0
    for i in range(1, len(insertion_list)):
        for j in range(i,0, -1):
            counter += 1
            if insertion_list[j] < insertion_list[j-1]:
                insertion_list[j],insertion_list[j-1]= insertion_list[j-1],insertion_list[j]
            else:
                #no swaps left we can break the loop
                break

    return insertion_list, counter



# generates a random list
my_list = create_random_arrey(10,1,80)
print("Random list: ",my_list)

# naive sorting alg
naively_sorted, counter = naive_sorting_algorithm(my_list)
print(f"NAIVE SORTING\nSorted list {counter}: ",naively_sorted)


# bubble sorting alg
bubble_list,counter = bubble_sort_algorithm(my_list)
print(f"BUBBLE SORTING\nSorted list {counter}: ",bubble_list)


# insertion sorting alg
insertion_list,counter = insertion_sort_algorithm(my_list)
print(f"INSERTION SORTING\nSorted list {counter}: ",insertion_list)

```
