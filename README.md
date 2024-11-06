#include <stdio.h>
#include <stdlib.h>

// Function Prototypes
void quickSort(int arr[], int low, int high);
void selectionSort(int arr[], int n);
void heapSort(int arr[], int n);
void heapify(int arr[], int n, int i);

// Main Function
int main() {
    int arr[10];
    int choice;

    // Input the array from user
    printf("Enter 10 numbers to sort:\n");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

    // Display the original array
    printf("Original Array:\n");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Ask user to choose sorting algorithm
    printf("Choose sorting algorithm:\n");
    printf("1. Quick Sort\n");
    printf("2. Selection Sort\n");
    printf("3. Heap Sort\n");
    printf("Enter your choice (1/2/3): ");
    scanf("%d", &choice);

    // Call corresponding sorting function
    switch (choice) {
        case 1:
            quickSort(arr, 0, 9);
            break;
        case 2:
            selectionSort(arr, 10);
            break;
        case 3:
            heapSort(arr, 10);
            break;
        default:
            printf("Invalid choice.\n");
            return 1;
    }

    // Display the sorted array
    printf("Sorted Array:\n");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
/ Selection Sort Function
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // Swap the found minimum element with the first element
        int temp = arr[minIndex];
        arr[minIndex] = arr[i];
        arr[i] = temp;
    }
}

