The call `arr[2]()` is syntactically the good old `obj[method]()`, in the role of `obj` we have `arr`, and in the role of `method` we have `2`.

فراخوان `arr[2]()` از لحاظ نحوی اصطلاح خوب خوب `obj[method]()` است ، در نقش "obj" ما "arr" داریم و در نقش "روش" ما `2 داریم.

So we have a call of the function `arr[2]` as an object method. Naturally, it receives `this` referencing the object `arr` and outputs the array:

بنابراین ما یک فراخوانی از تابع `arr[2]` به عنوان یک روش شیء داریم. به طور طبیعی ، این `this` را با استفاده از `arr` ارجاع می دهد و آرایه را بیرون می کشد:

```js run
let arr = ["a", "b"];

arr.push(function() {
  alert( this );
})

arr[2](); // "a","b",function
```

آرایه 3 مقدار دارد: در ابتدا دارای دو مقدار بود اما بعد از آن یک تابع اضافه شد.

