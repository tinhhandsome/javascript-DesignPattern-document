

``` javascript
    const order = new Order();
    expect(order.state.name).to.equal('waitingForPayment');
    order.nextState();
    expect(order.state.name).to.equal('shipping');
    order.nextState();
    expect(order.state.name).to.equal('delivered');
```
![ScreenShot](../../image/state_ds.png)

- ta thấy trong class Order
``` javascript
this.state = new WaitingForPayment()
```
- ta tiếp tục thấy class `WaitingForPayment`
``` javascript
class WaitingForPayment extends OrderStatus {
  constructor() {
    super('waitingForPayment', Shipping);
  }
}
```
- phương thức khởi tạo của nó kế thừa `OrderStatus`
- như vậy `this.state` lúc này
- sẽ dùng phương thức khởi tạo của `OrderStatus`




``` javascript
class OrderStatus {
  constructor(name, nextStatus) {
    this.name = name;
    this.nextStatus = nextStatus;
  }

  next() {
    return new this.nextStatus();
  }
}

class WaitingForPayment extends OrderStatus {
  constructor() {
    super('waitingForPayment', Shipping);
  }
}

class Shipping extends OrderStatus {
  constructor() {
    super('shipping', Delivered);
  }
}

class Delivered extends OrderStatus {
  constructor() {
    super('delivered', Delivered);
  }
}

class Order {
  constructor() {
    this.state = new WaitingForPayment();
  }

  nextState() {
    this.state = this.state.next();
  };
}

```