# 归并排序
## 描述
- 归并排序，稳定排序。
- O(nlogn)
## 细节介绍
## 思路

## 实现
```javascript
for (var fraction = Math.floor(len / 2); fraction > 0; fraction = Math.floor(fraction / 2)) {
    for (var i = fraction; i < len; i++) {
        for (var j = i - fraction; j >= 0 && arr[j] > arr[fraction + j]; j -= fraction) {
            var temp = arr[j];
            arr[j] = arr[fraction + j];
            arr[fraction + j] = temp;
        }
    }
}
```

