# Tìm hiểu về Design Pattern Facade
- Test 
``` javascript
  const shop = new ShopFacade();
  const result = shop.calc(100);
  expect(result).to.equal(99.5);
```


# es6 syntax
``` javascript
class ShopFacade {
  constructor() {
    this.discount = new Discount();
    this.shipping = new Shipping();
    this.fees = new Fees();
  }

  calc(price) {
    price = this.discount.calc(price);
    price = this.fees.calc(price);
    price += this.shipping.calc();
    return price;
  }
}

class Discount {

  calc(value) {
    return value * 0.9;
  }
}

class Shipping {
  calc() {
    return 5;
  }
}

class Fees {

  calc(value) {
    return value * 1.05;
  }
}
```
# es5 Syntax
```javascript

```