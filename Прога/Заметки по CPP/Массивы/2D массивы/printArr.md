```c++
void printArr(int *arr, int cols, int rows){
    for(int i=0;i<rows;i++){
        for(int j=0;j<cols;j++){
        cout<<*(arr++)<<" ";
        }
    cout<<endl;
    }
}
```

использование
```c++
int rows,cols;
cin>>rows>>cols;
int arr[rows][cols];
fillArr(&arr[0][0],cols,rows);
```
