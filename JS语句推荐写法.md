## 1.「可选链」「双问号」语法
例子：
```
const street = car && car.manufacturer && car.manufacturer.address && 
car.manufacturer.address.street || 'default street'

```

推荐写法：
```
const street = car?.manufacturer?.address?.street ?? 'default street'
```



## 2. 对象数组去重

### 2.1 数组去重

```js
const array = [1,2,3,3,4,5]
Array.from(new Set(array))
```

### 2.2 对象数组去重

```js
/**
 * 根据数组对象的某个字段去重
 * item.name  是[{name:1}] 根据每条数据的name值来去重
 * */
unique(arr,val) {
  const res = new Map();
  return arr.filter(item => !res.has(item[val]) && res.set(item[val], 1))
}
```

