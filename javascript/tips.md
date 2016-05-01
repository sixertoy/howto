# JS Tips

## Arrays

**Push in an array**

```javascript
arr[arr.length] = 'item';
```

**Empty an Array**

```javascript
var arr = [1, 2, 3, 4];
arr.length = 0;
```

**Flatten nested arrays**

```javascript
var arr = [[1, 2],[3, 4, 5], [6, 7, 8, 9]];
arr = [].concat.apply([], arr);
```

## Strings

**First to uppercase**

```javascript
var str = str.charAt(0).toUpperCase() + string.slice(1).toLowerCase();
```

**Convert string to number**

```javascript
var onestr = '1',
// Number 1
// faster than (+one)
onenum = (1 * one);
```

## Date

**Timestamp**

```javascript
var time =  (Date.now() / 1000 | 0);
```

## Miscellaneous

**Log execution time**

```javascript
console.time('Executed in');
[...]
console.timeEnd('Executed in');
```
