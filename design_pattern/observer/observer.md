# Tìm hiểu về observer javascript

``` javascript
function register(p, f, t) {
  p.register(f);
  p.register(t);
  return p;
}
```
### ta bắt đầũ xem đoạn code dưới đây
``` javascript
let product = register(new Product(), new Fees(), new Proft())
```
ta thấy khúc này sẽ trả về 

``` javascript
p.register(f);
p.register(t);
```
Đoạn code này product call 
`Product` method
this.action.push(Fees)
this.action.push(Proft)

lúc này `Product` sẽ có dạng như sau:
`this.actions  = [Fees, Proft]`
như vậy có thể thấy dùng `observer` 

ta không cần phải sử dụng `contructor tham số` mà truyền `trực tiếp` vào




![ScreenShot](../../image/observer_result.png)

![ScreenShot](../../image/observer.png)

![ScreenShot](../../image/observer_init.jpg)


``` javascript
class Product {
  constructor() {
    this.price = 0;
    this.actions = [];
  }

  setBasePrice(val) {
    this.price = val;
    this.notifyAll();
  }

  register(observer) {
    this.actions.push(observer);
  }

  unregister(observer) {
    this.actions = this.actions.filter(el => !(el instanceof observer));
  }

  notifyAll() {
    return this.actions.forEach(el => el.update(this));
  }
}

class Fees {
  update(product) {
    product.price = product.price * 1.2;
  }
}

class Proft {
  update(product) {
    product.price = product.price * 2;
  }
}

```

