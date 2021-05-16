# Tìm hiểu về Design Pattern Facade
- Test 
``` javascript
  const shop = new ShopFacade();
  const result = shop.calc(100);
  expect(result).to.equal(99.5);
```
``` javascript
const shop = new ShopFacade();
```
ta có shop new Object `ShopFacade`
``` javascript
const result = shop.calc(100);
```
I see `constructor` of `ShopFacade`
``` javascript
constructor() {
  this.discount = new Discount();
  this.shipping = new Shipping();
  this.fees = new Fees();
}
```
const result = shop.calc(100);

```javascript
  calc(price) {
    price = this.discount.calc(price);
    price = this.fees.calc(price);
    price += this.shipping.calc();
    return price;
  }
```
- new Discount
``` javascript
price = this.discount.calc(price);
```
- new Fees 
``` javascript
price = this.fees.calc(price);
```
- new Shipping

``` javascript
  price += this.shipping.calc();
```
  - So result return
  - price = this.discount.calc(100) = 0.9*100
  - this.fees.calc(price) = 90 * 1.05
  - price += this.shipping.calc()
  - = 90 * 1.05 + 5 = 99.5
  
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
var shopFacade = {
  calc: function(price) {
    price = discount(price);
    price = fees(price);
    price += shipping();
    return price;
  }
};

function discount(value) {
  return value * 0.9;
}

function shipping() {
  return 5;
}

function fees(value) {
  return value * 1.05;
}

```