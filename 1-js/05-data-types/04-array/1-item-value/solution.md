خروجی کد ذکر شده `4` است:


```js run
let fruits = ["سیب", "گلابی", "پرتقال"];

let shoppingCart = fruits;

shoppingCart.push("موز");

*!*
alert( fruits.length ); // 4
*/!*
```

دلیل این امر این است که آرایه ها اشیاء هستند. بنابراین ، هر دو «shoppingCart» و «fruits» ارجاع به همان آرایه دارند.

