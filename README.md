# JS

### #1. Функция сортировки элементов массива по возрастанию:

Дополнительные условия:
- Можно передавать отрицательные числа

```js
function sortNumbs(numbers) {
   return numbers.sort((a, b) => a - b);
}
 
sortNumbs([8, 4, 5, 7, 2, 3, 10]);  // [2, 3, 4, 5, 7, 8, 10]
sortNumbs([0, -2, 3, 1, 11]);       // [-2, 0, 1, 3, 11]
```

---

### #2. Функция фильтрации нечетных чисел в массиве:

Дополнительные условия:
- Можно передавать отрицательные числа

```js
function filterOdd(numbers) {
  return numbers.filter(number => number % 2 === 0);
}
 
filterOdd([8, 4, 5, 7, 2, 3, 10]);  // [8, 4, 2, 10]
filterOdd([2, 4, 1, 1, -2, 9, 0]);  // [2, 4, -2]
```

---

### #3. Функция фильтрации дубликатов в массиве:

Дополнительные условия:
- Можно передавать отрицательные числа

```js
function removeDuplicates(numbers) {
  return Array.from(new Set(numbers));
}
 
removeDuplicates([8, 4, 4, 2, 2, 1]);   // [8, 4, 2, 1]
removeDuplicates([10, 5, 1, 2, 2, 2]);  // [10, 5, 1, 2]
```

---

### #4. Функция вывода строки в обратном порядке:

Дополнительные условия:
- Исключить все цифры из выводимой строки

```js
function processString(str) {
    return str.split('').reverse().filter(el => isNaN(el)).join('');
}

processString("абв1г3д");    // "дгвба"
processString("жн1пе8вщ0");  // "щвепнж"
```

---

### #5. Функция возврата следующего ближайшего квадрата переданного числа:

Дополнительные условия:
- Вернуть `-1` если корень не целое число

```js
function findNextSquare(number) {
  let radix = Math.sqrt(number);
  
  if (Number.isInteger(radix)) {
    return Math.pow(++radix, 2);
  }
  
  return -1;
}

findNextSquare(114);  // -1 (нет корня)
findNextSquare(144);  // 169 (корень 144 - это 12, далее 12 + 1 в квадрате - это 169)
```

---

### #6. Функция подсчёта суммы всех чисел между двумя переданными (включая их самих): 

Дополнительные условия:
- Можно передавать отрицательные числа
- Если передать два одинаковых числа, вернётся одно из них

```js
function rez(number1, number2) {
  if (number1 === number2) {
    return number1;
  }
 
  let sum = number1 + number2;

  if ((number2 - number1) === 1) {
    return sum;
  }
 
  return sum + rez(++number1, --number2);
}

rez(1, 3);  // 6
rez(2, 7);  // 27
```

---

### #7. Функция возврата даты (ГГГГ.ММ.ДД) в заданном виде:

Дополнительные условия:
- При передаче неверной строки возвращать `null`

```js
function today(date) {
  let [year, month, day] = date.split('.');
  
  if (month > 12 || day > 31) {
    return null;
  }
  
  if (!checkDateValidity(year, month, day)) {
    return null;    
  };
  
  let weekdayNum = new Date(year, month, day).getUTCDay();
  
  const monthes = ['Январь','Февраль','Март','Апрель','Май','Июнь','Июль','Август','Сентябрь','Октябрь','Ноябрь','Декабрь'];
  const weekdays = ['Понедельник','Вторник','Среда','Четверг','Пятница','Суббота','Воскресенье'];
 
  return `Год: ${year} | Месяц: ${monthes[--month]} | День: ${weekdays[weekdayNum]}`;
}

function checkIsLeapYear(year) {
   if ((year % 4 === 0) && (year % 100 !== 0)) {
     return true;
   }
   
   if ((year % 4 === 0) && (year % 100 === 0)) {
     return (year % 400 === 0);
   }
 
   return false;
}

function checkDateValidity(year, month, day) {
  if (month == 2) {
     let isLeapYear = checkIsLeapYear(year);
     if (isLeapYear) {
       return day <= 29;
     } else {
       return day <= 28;
     }
  }
  
  let monthesMaxDays30 = [4, 6, 9, 11];
  
  if (monthesMaxDays30.some(el => el === Number(month))) {
    return day <= 30;
  } else {
    return day <= 31;
  }
  return false;
}

today(2016.02.12);  // "Год: 2016 | Месяц: Февраль | День: Пятница"
today(2022.26.08);  // "Год: 2022 | Месяц: Август | День: Пятница"
```

---

### #8. Функция возврата пропущенных чисел:

```js
function missNum(numbers) {
  let arr = new Array(numbers.length);
  numbers.forEach(num => {
    let idx = num;
    arr.splice(idx, 1, num);
  });
 
  return arr.findIndex(el => typeof el == 'undefined');
}

missNum([0, 5, 1, 3, 2, 9, 7, 6, 4]);  // 8
missNum([9, 2, 4, 5, 7, 0, 8, 6, 1]);  // 3
```

---

### #9. Функция создания объекта из массивов:

Дополнительные условия:
- Если данных меньше, чем ключей, значение равняется `undefined`

```js
function createObject(keys, props) {
  const resultObject = {};
  keys.forEach((key, index) => {
    resultObject[key] = props[index];
  });
  return resultObject;
}

createObject(['foo'], ['bar']);           // { foo: 'bar' }
createObject(['foo', 'extra'], ['bar']);  // { foo: 'bar', extra: undefined }
```

---

### #10. Функция суммирования всех цифр числа:

Дополнительные условия:
- Можно передавать отрицательные числа

```js
function sumDigits(number) {
  return Math.abs(number).toString(10).split('')
         .reduce((acc, curr) => {
            return acc + Number(curr);
         }, 0);
}

sumDigits(99);   // 18
sumDigits(-32);  // 5
```

---
