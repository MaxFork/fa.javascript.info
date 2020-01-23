لطفاً به جزئیات ظریف و مهم راه حل توجه کنید. ما "value" را بلافاصله پس از دریافت از کاربر توسط "prompt" به عدد تبدیل نمی کنیم ، زیرا اگر این تبدیل را انجام دهیم بعد از `value = +value` نمی توانیم تفاوت یک رشته خالی را از عدد ظصفر (که یک عدد معتبر است) تشخیص دهیم. بنابراین بعداً این کار را می کنیم.


```js run demo
function sumInput() {
 
  let numbers = [];

  while (true) {

    let value = prompt("A number please?", 0);

    // should we cancel?
    if (value === "" || value === null || !isFinite(value)) break;

    numbers.push(+value);
  }

  let sum = 0;
  for (let number of numbers) {
    sum += number;
  }
  return sum;
}

alert( sumInput() ); 
```

