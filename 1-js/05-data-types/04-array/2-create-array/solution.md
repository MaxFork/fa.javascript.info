

```js run
let styles = ["موسیقی جاز", "نوعی سرود وموسیقی جاز"];
styles.push("رقص راک اندرول");
styles[Math.floor((styles.length - 1) / 2)] = "موسیقی کلاسیک";
alert( styles.shift() );
styles.unshift("رپ", "موسیقی رگی");
```

