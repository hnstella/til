# Lodash

underscore에서 성능을 개선한  자바스크립트 유틸리티 라이브러리

array, collection, date, number, object 등이 있음

자바스크립트에서 배열 안의 객체들의 값을 핸들링할 때 유용함

## Collection
### filter
> \_.filter(collection, [predicate=_.identity])

조건에 맞는 데이터를 포함한 콜렉션을 반환

```javascript
var users = [
  { 'user': 'barney', 'age': 36, 'active': true },
  { 'user': 'fred',   'age': 40, 'active': false }
];
 
_.filter(users, function(o) { return !o.active; });
// => objects for ['fred']
 
// The `_.matches` iteratee shorthand.
_.filter(users, { 'age': 36, 'active': true });
// => objects for ['barney']
 
// The `_.matchesProperty` iteratee shorthand.
_.filter(users, ['active', false]);
// => objects for ['fred']
 
// The `_.property` iteratee shorthand.
_.filter(users, 'active');
// => objects for ['barney']
```

## Array
### compact
> _.compact(array)

배열에서 false, null, 0, "", undefined, NaN 값을 제외시킨 배열 반환
```javascript
_.compact([0, 1, false, 2, '', 3]);
// => [1, 2, 3]
```

### slice
> _.slice(array, [start=0], [end=array.length])

배열을 시작 인덱스를 포함하여 길이만큼 잘라준다. 단 마지막 인덱스는 포함하지 않는다.

### uniq
> _.uniq(array)

배열의 중복 값을 제거

```javascript
_.uniq([2, 1, 2]);
// => [2, 1]
```

## Object
### omit
> _.omit(object, [paths])

객체에서 해당 키(paths)를 제외한 객체를 반환

```javascript
var object = { 'a': 1, 'b': '2', 'c': 3 };
 
_.omit(object, ['a', 'c']);
// => { 'b': '2' }
```


## LINKS
- [공식 사이트](https://lodash.com/)
- [문서](https://lodash.com/docs/4.17.10)