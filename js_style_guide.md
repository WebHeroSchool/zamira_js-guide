---
__Advertisement :)__

В данном руководстве предоставлены 10 понравившихся мне практик по написанию JavaScript-кода.

---

# JavaScript Style Guide
### __Объявление переменных__
Используйте const или let для объявления переменных, избегайте var.
Если вам необходимо переопределять значения, то используйте let, если значение переменной не должно меняться, используйте const.

 ```javascript
    // плохо
    var age = 20;
    let pi = 10;

    // хорошо
    const myName = "Zamira";
    let count = 1;
    if (true) {
      count += 1;
    }
```
Не создавайте цепочки присваивания переменных.
```javascript
// плохо
(function example() {
  // JavaScript интерпретирует это, как
  // let a = ( b = ( c = 1 ) );
  // Ключевое слово let применится только к переменной a;
  // переменные b и c станут глобальными.
  let a = b = c = 1;
}());

console.log(a); // throws ReferenceError
console.log(b); // 1
console.log(c); // 1

// хорошо
(function example() {
  let a = 1;
  let b = a;
  let c = a;
}());

console.log(a); // throws ReferenceError
console.log(b); // throws ReferenceError
console.log(c); // throws ReferenceError

// тоже самое и для `const`
```
### __Объекты__
Для создания объекта используйте литеральную нотацию
```javascript
// плохо
const item = new Object();

// хорошо
const item = {};
```
Группируйте ваши сокращённые записи свойств в начале объявления объекта.
```javascript
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';

// плохо
const obj = {
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker,
};

// хорошо
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJediWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4,
};
```
Только недопустимые идентификаторы помещаются в кавычки.
```javascript
// плохо
const bad = {
  'foo': 3,
  'bar': 4,
  'data-blah': 5,
};

// хорошо
const good = {
  foo: 3,
  bar: 4,
  'data-blah': 5,
};
```
Используйте точечную нотацию для доступа к свойствам.
```javascript
const luke = {
  jedi: true,
  age: 28,
};

// плохо
const isJedi = luke['jedi'];

// хорошо
const isJedi = luke.jedi;
```
### __Массивы__
Для добавления элемента в массив используйте метод push вместо прямого присваивания.
```javascript
const someStack = [];

// плохо
someStack[someStack.length] = 'abracadabra';

// хорошо
someStack.push('abracadabra');
```
### __Строки__
Используйте одинарные кавычки '' для строк.
```javascript
// плохо
const name = "Capt. Janeway";

// плохо - литерал шаблонной строки должен содержать интерполяцию или переводы строк
const name = `Capt. Janeway`;

// хорошо
const name = 'Capt. Janeway';
```
### __Функции__
Никогда не используйте конструктор функций для создания новых функций.
```javascript
// плохо
var add = new Function('a', 'b', 'return a + b');

// всё ещё плохо
var subtract = Function('a', 'b', 'return a - b');
```
### __Импорт__
Не используйте импорт модуля через *
```javascript
// плохо
import * as AirbnbStyleGuide from './AirbnbStyleGuide';

// хорошо
import AirbnbStyleGuide from './AirbnbStyleGuide';
```
