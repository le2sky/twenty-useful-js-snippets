# twenty-useful-js-snippets

Small solutions to single well-defined problems.

## TOC

1. [Reference](#reference)
2. [Snippets usage](#snippets-usage)
   - [Get Value](#get-value)
   - [Clamp](#clamp)
   - [Sleep](#sleep)
   - [Group by](#group-by)
   - [Collect by](#collect-by)

## Reference

This is the repository to store the code based on the article written by @henrik1

- Henrik Larsen Toft's
  [20 JavaScript snippets that will make you a better developer](https://levelup.gitconnected.com/20-javascript-snippets-that-will-make-you-a-better-developer-68dfe4bf5019)

## Snippets usage

#### Get Value

함수는 지정된 경로의 값을 반환하고, 값이 없으면 null을 반환합니다.

```js
getValue({ a: { b: { c: "d" } } }, "a.b.c"); // = d
```

| Function   | Parameter                     | Description                           |
| :--------- | :---------------------------- | :------------------------------------ |
| `getValue` | obj: `object`, path: `string` | if, vaild path return value else null |

---

#### clamp

값이 지정된 범위 내에 있는지 확인하고, 지정된 범위에 값이 없다면 최소값과 최대값에 가장 가까운 값을 반환(클램프)합니다.

```js
clamp(0, 10, -5); // = 0
```

| Function | Parameter                                    | Description                    |
| :------- | :------------------------------------------- | :----------------------------- |
| `clamp`  | min: `number`, max: `number`, value:`number` | value or clamp value(min, max) |

---

#### Sleep

다음 작업을 수행하기 전에 지정된 기간(밀리초)을 기다립니다.

```js
await sleep(1000); // waits 1 sec
```

| Function | Parameter          | Description                                 |
| :------- | :----------------- | :------------------------------------------ |
| `sleep`  | duration: `number` | Wait the specified duration in milliseconds |

---

#### Group By

keying-function에 따라 개체의 관련 항목을 그룹화하고 색인화합니다.

```js
groupBy(
  (vehicle) => vehicle.make,
  [
    { make: "tesla", model: "3" },
    { make: "tesla", model: "y" },
    { make: "ford", model: "mach-e" },
  ]
);
// {
//   tesla: [ { make: 'tesla', ... }, { make: 'tesla', ... } ],
//   ford: [ { make: 'ford', ... } ],
```

| Function  | Parameter                   | Description  |
| :-------- | :-------------------------- | :----------- |
| `groupBy` | fn:`Function` list: `Array` | return `obj` |

---

#### Collect By

keying-function에 따라 관련 항목을 포함하는 하위 목록을 만듭니다.

```js
collectBy(
  (vehicle) => vehicle.make,
  [
    { make: "tesla", model: "3" },
    { make: "tesla", model: "y" },
    { make: "ford", model: "mach-e" },
  ]
);

// [
//   [ { make: 'tesla', ... }, { make: 'tesla', ... } ],
//   [ { make: 'ford', ... } ],
// ]
```

| Function    | Parameter                   | Description             |
| :---------- | :-------------------------- | :---------------------- |
| `collectBy` | fn:`Function` list: `Array` | **groupBy is required** |

---

#### Head

리스트의 첫 번째 요소를 가져옵니다. 이 함수는 깨끗하고 읽기 쉬운 코드를 작성하는 데 유용합니다.

```js
head([1, 2, 3]); // = 1
head([]); // = undefined
```

| Function | Parameter     | Description                     |
| :------- | :------------ | :------------------------------ |
| `head`   | list: `Array` | return first value or undefiend |

---

#### Tail

리스트의 첫 번째 요소를 제외한 모든 요소를 ​​가져옵니다. 이 함수는 깨끗하고 읽기 쉬운 코드를 작성하는 데 유용합니다.

```js
tail([1, 2, 3]); // = [2, 3]
tail([]); // = []
```

| Function | Parameter     | Description                               |
| :------- | :------------ | :---------------------------------------- |
| `tail`   | list: `Array` | return rest of list, except first element |

---

#### Flatten

중첩된 하위 리스트에서 모든 항목을 재귀적으로 가져와서 플랫 리스트를 만듭니다.

```js
flatten([[1, 2, [3, 4], 5, [6, [7, 8]]]]); // = [1, 2, 3, 4, 5, 6, 7, 8]
```

| Function  | Parameter     | Description      |
| :-------- | :------------ | :--------------- |
| `flatten` | list: `Array` | return flat list |

---

#### Intersection By

keying-function에 의해 정의된 대로 두 목록에 존재하는 모든 값을 찾습니다. (교집합)

```js
intersectionBy((v) => v, [1, 2, 3], [2, 3, 4]); // = [2, 3]
intersectionBy(
  (v) => v.a,
  [{ a: 1 }, { a: 2 }],
  [{ a: 2 }, { a: 3 }, { a: 4 }]
); // = [{ a: 2 }];
```

| Function         | Parameter                                    | Description                 |
| :--------------- | :------------------------------------------- | :-------------------------- |
| `intersectionBy` | fn: `Function` listA: `Array` listB: `Array` | return Array\<intersection> |
