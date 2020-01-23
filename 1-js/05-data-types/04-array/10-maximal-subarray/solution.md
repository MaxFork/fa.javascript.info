# راه حل کم سرعت و کند

ما می توانیم تمام زیرمجموعه های احتمالی را محاسبه کنیم.

ساده ترین راه ، گرفتن هر عنصر و محاسبه جمع تمام زیر مجموعه ها که از همان شروع می شود.

به عنوان مثال ، برای [[-1 ، 2 ، 3 ، -9 ، 11] :

```js no-beautify
// Starting from -1:
-1
-1 + 2
-1 + 2 + 3
-1 + 2 + 3 + (-9)
-1 + 2 + 3 + (-9) + 11

// Starting from 2:
2
2 + 3
2 + 3 + (-9)
2 + 3 + (-9) + 11

// Starting from 3:
3
3 + (-9)
3 + (-9) + 11

// Starting from -9
-9
-9 + 11

// Starting from -11
-11
```

این کد در واقع یک حلقه تو در تو است: حلقه خارجی بر روی عناصر آرایه ، و داخلی زیر عناصر شمارش داخلی که از همان عنصر شروع می شود را شمارش می کند.

```js run
function getMaxSubSum(arr) {
  let maxSum = 0; // if we take no elements, zero will be returned

  for (let i = 0; i < arr.length; i++) {
    let sumFixedStart = 0;
    for (let j = i; j < arr.length; j++) {
      sumFixedStart += arr[j];
      maxSum = Math.max(maxSum, sumFixedStart);
    }
  }

  return maxSum;
}

alert( getMaxSubSum([-1, 2, 3, -9]) ); // 5
alert( getMaxSubSum([-1, 2, 3, -9, 11]) ); // 11
alert( getMaxSubSum([-2, -1, 1, 2]) ); // 3
alert( getMaxSubSum([1, 2, 3]) ); // 6
alert( getMaxSubSum([100, -9, 2, -3, 5]) ); // 100
```

راه حل دارای پیچیدگی زمانی [O(n<sup>2</sup>)](https://en.wikipedia.org/wiki/Big_O_notation) است. به عبارت دیگر ، اگر اندازه آرایه را 2 بار افزایش دهیم ، الگوریتم 4 برابر بیشتر و طولانی تر کار خواهد کرد.

برای آرایه های بزرگ (1000 ، 10000 مورد یا بیشتر) چنین الگوریتم هایی می توانند به یک کندی جدی منجر شوند.

# راه حل سریع و پر سرعت

بیایید آرایه را طی کنیم و مقدار جزئی عناصر فعلی را در متغیر `s نگه داریم. اگر در بعضی از نقاط 's منفی شود ،' s = 0 'را اختصاص دهید. حداکثر جواب همه اینها خواهد بود.

Let's walk the array and keep the current partial sum of elements in the variable `s`. If `s` becomes negative at some point, then assign `s=0`. The maximum of all such `s` will be the answer.

اگر توضیحات خیلی مبهم است ، لطفاً کد را ببینید ، به اندازه کافی کوتاه است:

```js run
function getMaxSubSum(arr) {
  let maxSum = 0;
  let partialSum = 0;

  for (let item of arr) { // for each item of arr
    partialSum += item; // add it to partialSum
    maxSum = Math.max(maxSum, partialSum); // remember the maximum
    if (partialSum < 0) partialSum = 0; // zero if negative
  }

  return maxSum;
}

alert( getMaxSubSum([-1, 2, 3, -9]) ); // 5
alert( getMaxSubSum([-1, 2, 3, -9, 11]) ); // 11
alert( getMaxSubSum([-2, -1, 1, 2]) ); // 3
alert( getMaxSubSum([100, -9, 2, -3, 5]) ); // 100
alert( getMaxSubSum([1, 2, 3]) ); // 6
alert( getMaxSubSum([-1, -2, -3]) ); // 0
```

این الگوریتم دقیقاً به 1 آرایه نیاز دارد ، بنابراین پیچیدگی زمان O(n) است.

می توانید اطلاعات بیشتر در مورد الگوریتم را در اینجا بیابید: [Maximum subarray problem](http://en.wikipedia.org/wiki/Maximum_subarray_problem). اگر هنوز مشخص نیست که چرا این کار می کند ، لطفاً الگوریتم را در مثالهای بالا ردیابی کنید ، ببینید که چگونه کار می کند ، بهتر از هر کلمه است.
