## Tìm hiểu Strategy Design Pattern

## Guest test
``` javascript
    function guestStrategy(amount) {
        return amount;
    }

    const guestCart = new ShoppingCart(guestStrategy);
    guestCart.setAmount(100);
    expect(guestCart.checkout()).to.equal(100);
```
- const guestCart = new ShoppingCart(guestStrategy)
- guestCart = new ShoppingCart(new getStrategy(amount))
- guestCart.setAmount(100)
- this.amount = 100
- guestCart.checkout()
- this.discount(100)
- new guestStrategy(100)
- return 100
- guestCart.checkout() = 100
## Regular test
``` javascript
function regularStrategy(amount) {
  return amount * 0.9;
}

const regularCart = new ShoppingCart(regularStrategy);
regularCart.setAmount(100);
expect(regularCart.checkout()).to.equal(90);
```
- Similar = 0.9 * 100 = 90
## Premium test
``` javascript
function premiumStrategy(amount) {
  return amount * 0.8;
}
const premiumCart = new ShoppingCart(premiumStrategy);
premiumCart.setAmount(100);
expect(premiumCart.checkout()).to.equal(80);
```
- Similar = 0.8 * 100 = 80
## Syntax es6
``` javascript
class ShoppingCart {
    constructor(discount) {
        this.discount = discount;
        this.amount = 0;
    }

    checkout() {
        return this.discount(this.amount)
    }

    setAmount(amount) {
        this.amount = amount
    }
}

function guestStrategy(amount) {
    return amount
}
function regularStrategy(amount) {
    return amount * 0.9
}
function premiumStrategy(amount) {
    return amount * 0.8
}
```
## Syntax es5
``` javascript
```