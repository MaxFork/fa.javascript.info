اهمیت: 2

---

# بزرگترین زیر عضو یک آرایه

ورودی مجموعه ای از اعداد است ، به عنوان مثال `arr = [1, -2, 3, 4, -9, 6]`.

وظیفه این است که پیوسته زیر عضو آرایه `arr`را با بزرگترین مجموع عنصر ها پیدا کنید.

تابع `getMaxSubSum(arr)` را بنویسید که مجموع را برمی گرداند.


برای مثال:

```js
getMaxSubSum([-1, *!*2, 3*/!*, -9]) = 5 (the sum of highlighted items)
getMaxSubSum([*!*2, -1, 2, 3*/!*, -9]) = 6
getMaxSubSum([-1, 2, 3, -9, *!*11*/!*]) = 11
getMaxSubSum([-2, -1, *!*1, 2*/!*]) = 3
getMaxSubSum([*!*100*/!*, -9, 2, -3, 5]) = 100
getMaxSubSum([*!*1, 2, 3*/!*]) = 6 (take all)
```

If all items are negative, it means that we take none (the subarray is empty), so the sum is zero:

```js
getMaxSubSum([-1, -2, -3]) = 0
```

Please try to think of a fast solution: [O(n<sup>2</sup>)](https://en.wikipedia.org/wiki/Big_O_notation) or even O(n) if you can.
