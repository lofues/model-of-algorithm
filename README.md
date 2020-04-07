# model-of-algorithm
model of algorithm in C++

日常算法的模板总结
## 排序

```C++
快速排序:
void quick_sort(int q[], int l, int r){
  if (l >= r) return ;
  int x = q[l], i = l - 1, j = r + 1; # 此处x 可选q[r] q[l + r >> 1]等，需要注意边界问题
  
  while (i < j){
    do i ++; while(q[i] < x);
    do j --; while(q[j] > x);
    if (i < j) swap(q[i], q[j]);
  }
  
  quick_sort(q, l, j);
  quick_sort(q, l, j + 1);
}

归并排序:
int tmp[N];
void merge_sort(int q[], int l, int r){
  if (l >= r) return ;
  
  int mid = l + r >> 1;
  merge_sort(q, l, mid), merge_sort(q, mid + 1, r);
  
  int i = l, j = mid + 1, k = 0;
  while (i <= mid && j <= r)
    if (q[i] <= q[j]) tmp[k ++ ] = q[i ++ ];
    else tmp[k ++ ] = q[ j ++ ];
   while (i <= mid) tmp[k ++ ] = q[i ++ ];
   while (j <= r) tmp[k ++ ] = q[j ++];
   for (int i = l, j = 0; i <= r && j <= k; i++ , j++) q[i ++ ] = tmp[j ++ ];
}
```
