
#include <stdio.h>
#include <stdlib.h>


void quickSort(int arr[], int low, int high);
void selectionSort(int arr[], int n);
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
    printf("Enter your choice (1/2/3): ");
    scanf("%d", &choice);

   
    switch (choice) {
        case 1:
            quickSort(arr, 0, 9);
            break;
        case 2:
            selectionSort(arr, 10);
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
          // Swap arr[i + 1] and arr[high] (pivot)
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        int pi = i + 1;

        // Recursively sort the subarrays
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
       void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
       
        int temp = arr[minIndex];
        arr[minIndex] = arr[i];
        arr[i] = temp;
    }
} 
  void heapSort(int arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--) {
        heapify(arr, n, i);
    }
    for (int i = n - 1; i >= 0; i--) {
        int temp = arr[0];
        arr[0] = arr[i];
        arr[i] = temp;
        heapify(arr, i, 0);
    }
}
void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1; 
    int right = 2 * i + 2; 
    if (left < n && arr[left] > arr[largest]) {
        largest = left;
    }
    if (right < n && arr[right] > arr[largest]) {
        largest = right;
    }
    if (largest != i) {
        int temp = arr[i];
        arr[i] = arr[largest];
        arr[largest] = temp;
        heapify(arr, n, largest);   
        }
        
       
        
    

