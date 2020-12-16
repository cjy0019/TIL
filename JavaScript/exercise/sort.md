# 정렬

## 정렬 확인

- 주어진 배열(array)이 정렬되어 있다면 true, 그렇지 않다면 false를 반환하는 함수를 구현하라. 단, 어떠한 빌트인 함수도 사용하지 않고 for문을 사용하여 구현하여아 한다.

```javascript
function isSorted(array) {
     ...
}

console.log(isSorted([1, 2, 3, 4, 5])); // true
console.log(isSorted([2, 3, 4, 1, 5])); // false
```

**Answer**

```javascript
function isSorted(array) {
  for (let i = 0; i < array.length - 1; i++) {
    // array 길이 만큼 비교할 경우 array[i+1]이 크기를 넘어가기 때문에
    // undefined를 반환하게 되고 arr[array.length] < undefined 결과로 false를 반환하게 됨
    if (array[i] <= array[i + 1]) continue;
    else return false;
  }
  return true;
}
console.log(isSorted([1, 2, 3, 4, 5])); // true
console.log(isSorted([2, 3, 4, 1, 5])); // false
console.log(isSorted([2, 2, 2, 3, 4, 5, 6])); //true

```



## 버블 정렬

- 버블 정렬(bubble sort)은 순차적으로 배열을 순회하면서 인접한 두 요소를 비교하여 작은 요소를 왼쪽으로, 큰 요소를 오른쪽으로 교환한다.
- 버블 정렬은 가장 간단하지만 가장 느린 정렬 알고리즘이다.
- 시간 복잡도: O(n2)

![img](https://poiemaweb.com/assets/fs-images/bubble-sort.png)



버블 정렬을 통해 주어진 배열(array)을 정렬하는 함수를 구현하여라. 단, 어떠한 빌트인 함수도 사용하지 않고 for 문을 사용하여 구현하여야 한다.

```javascript
function bubbleSort(array){
     ...
}

console.log(bubbleSort([2, 4, 5, 1, 3]));     // [1, 2, 3, 4, 5]
console.log(bubbleSort([5, 2, 1, 3, 4, 6]));  // [1, 2, 3, 4, 5, 6]
console.log(bubbleSort([3, 1, 0, -1, 4, 2])); // [-1, 0, 1, 2, 3, 4]
```

**Answer**

```javascript
function bubbleSort(array) {
  for (let i = 0; i < array.length - 1; i++) {
    for (let j = 0; j < array.length; j++) {
      if (array[j] > array[j + 1]) {
        let temp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = temp;
      } else if (array[j] <= array[j + 1]) continue;
    }
  }
  return array;
}

console.log(bubbleSort([2, 4, 5, 1, 3])); // [1, 2, 3, 4, 5]
console.log(bubbleSort([5, 2, 1, 3, 4, 6])); // [1, 2, 3, 4, 5, 6]
console.log(bubbleSort([3, 1, 0, -1, 4, 2])); // [-1, 0, 1, 2, 3, 4]
```

