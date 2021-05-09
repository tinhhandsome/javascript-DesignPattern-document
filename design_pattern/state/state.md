# Tìm hiểu về Design Pattern state

```javascript
const order = new Order();
expect(order.state.name).to.equal("waitingForPayment");
order.nextState();
expect(order.state.name).to.equal("shipping");
order.nextState();
expect(order.state.name).to.equal("delivered");
```

![ScreenShot](../../image/state_detail_1.png)

- ta thấy trong `class Order`
- `constructor()`

```javascript
constructor() {
    this.state = new WaitingForPayment();
}
```

- khi `order.nextState()`
- bởi vì - `this.state = new WaitingForPayment()`
- mà `WaitingForPayment` kế thừa `OrderStatus`
- nên nó có thể sử dụng `method` của `OrderStatus`

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
```
## Trước khi call nextState()
``` javascript
nextState() {
  this.state = this.state.next();
};
```
- ta nhìn vào `constructor` của `WaitingForPayment`
``` javascript
  class WaitingForPayment extends OrderStatus {
    constructor() {
      super('waitingForPayment', Shipping);
    }
  }
```

- lúc này `OrderStatus`
- có `this.name` === `waitingForPayment`
- và `this.nextStatus` === `Shipping`

``` javascript
  this.state = this.state.next();
```
- mà `WaitingForPayment` kế thừa `OrderStatus`
- như vậy khi call `order.nextStatus()`
- lúc này tương đương
``` javascript
  class Shipping extends OrderStatus {
    constructor() {
      super('shipping', Delivered);
    }
  }
```

``` javascript
- this.name = 'shipping'
- this.nextStatus = new Delivered()
```
![ScreenShot](../../image/state_ds.png)
- tương tự

``` javascript

```


```javascript
class OrderStatus {
  constructor(name, nextStatus) {
    this.name = name;
    this.nextStatus = nextStatus;
  }

  next() {
    return new this.nextStatus();
  }
}
```

``` javascript
class WaitingForPayment extends OrderStatus {
  constructor() {
      super('waitingForPayment', Shipping);
  }
}
```
- phương thức khởi tạo của nó kế thừa `OrderStatus`
- thấy trong constructor của `OrderStatus`
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
````

- như vậy lúc này
- `this.name = 'waitingForPayment'`
- `this.nextStatus = Shipping`

- order.nextState();

``` javascript
order.nextState();
```

- ta tiếp tục nhìn vào class `Order`

```javascript
  nextState() {
    this.state = this.state.next();
  };
```

```javascript
class Shipping extends OrderStatus {
  constructor() {
    super("shipping", Delivered);
  }
}
```

- => `new this.nextStatus()` === `new Shipping()`
- nhìn vào `constructor` của `Shipping` ta có thể suy ra:
- suy ra `this.name === 'shipping'`
- và `this.nextStatus === Delivered`

![ScreenShot](../../image/state_log_1.png)

## syntax es6
```javascript
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
    super("waitingForPayment", Shipping);
  }
}

class Shipping extends OrderStatus {
  constructor() {
    super("shipping", Delivered);
  }
}

class Delivered extends OrderStatus {
  constructor() {
    super("delivered", Delivered);
  }
}

class Order {
  constructor() {
    this.state = new WaitingForPayment();
  }

  nextState() {
    this.state = this.state.next();
  }
}
```
## syntax es5
``` javascript
function Order() {
  this.state = new WaitingForPayment();

  this.nextState = function() {
    this.state = this.state.next();
  };
}

function WaitingForPayment() {
  this.name = 'waitingForPayment';
  this.next = function() {
    return new Shipping();
  };
}

function Shipping() {
  this.name = 'shipping';
  this.next = function() {
    return new Delivered();
  };
}

function Delivered() {
  this.name = 'delivered';
  this.next = function() {
    return this;
  };
}
```