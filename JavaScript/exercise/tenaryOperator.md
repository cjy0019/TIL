# 삼항 연산자로 변경

*q) 다음 코드를 삼항 연산자로 변경하시오.*

```javascript
var x = 11;
var res;

if(x === 0){
    res = '영';
}
else if( x % 2 === 0){
    res = '짝수';
}
else{
    res = '홀수';
}
```



**answer**

```javascript
var x = 11;

var res = x ? (x % 2 === 0 ? '짝수' : '홀수'): '영';
```

