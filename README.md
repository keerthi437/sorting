#include <stdio.h>
#include <stdlib.h>


void quickSort(int arr[], int low, int high);
void selectionSort(int arr[], int n);
void heapSort(int arr[], int n);
void heapify(int arr[], int n, int i);


int main() {
    int arr[10];
    int choice;

    
    printf("Enter 10 numbers to sort:\n");
    for (int i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

   
    printf("Original Array:\n");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

   
    printf("Choose sorting algorithm:\n");
    printf("1. Quick Sort\n");
    printf("2. Selection Sort\n");
    printf("3. Heap Sort\n");
    printf("Enter your choice (1/2/3): ");
    scanf("%d", &choice);

   
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

    
    printf("Sorted Array:\n");
    for (int i = 0; i < 10; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pivot = arr[high];
        int i = low - 1;

       
        for (int j = low; j <= high - 1; j++) {
            if (arr[j] < pivot) {
                i++;
                // Swap arr[i] and arr[j]
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        
       
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        int pi = i + 1;

       
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
