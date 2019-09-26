# Data Structures and algorithms

## Sorting algorithms

### Insertion Sort

Here shifting as we do while playing cards.

```c
    int arr[] = {2,1,3,4,6,5};
    for(int i =1 ; i< 6; i++) {
        int key = arr[i];
        int j = i-1;
        while (j >= 0 && arr[j] > key){
            arr[j+1] = arr[j];
            j--;
        }
        arr[j+1] = key;
    }
    for( int i = 0; i < 6; i++){
        printf("%d  ", arr[i]);
    } // 1 2 3 4 5 6
```

### Selection Sort

```c
    int arr[] = {2,1,3,4,6,5};
    for(int i =0 ; i< 6; i++) {
        int min = 99, pos = -1;
        for(int j = i ; j< 6 ; j++) {
            if(min >= arr[j]){
                min = arr[j];
                pos = j;
                printf("%d %d %D \n", arr[j], j , i);
            }
        }
        int temp = arr[i];
        arr[i] = arr[pos];
        arr[pos] = temp;
    }
    for( int i = 0; i < 6; i++){
        printf("%d  ", arr[i]);
    } // 1 2 3 4 5 6
```

### Bubble sort

```c
    int arr[] = {2,1,6,4,5,3];
    for(int i =0 ; i< 5; i++) {
        for(int j = i; j< 5; j++)
            if(arr[j] > arr[j+1]){
                arr[j] += arr[j+1];
                arr[j+1] = arr[j] - arr[j+1];
                arr[j] = arr[j] - arr[j+1];
            }
    }
    for( int i = 0; i < 6; i++){
        printf("%d  ", arr[i]);
    } // 1 2 3 4 5 6
```

