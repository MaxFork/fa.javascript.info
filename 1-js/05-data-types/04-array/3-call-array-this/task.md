اهمیت: 5

---

# دسترسی به اعضای آرایه

نتیجه چیست؟ چرا؟

```js
let arr = ["a", "b"];

arr.push(function() {
  alert( this );
})

arr[2](); // ?
```

