# Giải thích code `chain-of-resp`
## Giải thích các case
- ## Case 1:
## `> $ 500`
``` javascript
const discount = new Discount();
const sc = new ShoppingCart();
sc.addProduct(1000);
let resp = discount.calc(sc.products);
expect(resp).to.equal(0.1);
```

- ### `step 11`:
``` javascript
function Discount() {
  this.calc = function(products) {
    var ndiscount = new NumberDiscount();
    var pdiscount = new PriceDiscount();
    var none = new NoneDiscount();

    ndiscount.setNext(pdiscount);
    pdiscount.setNext(none);

    return ndiscount.exec(products);
  };
}
const discount = new Discount();
console.log(discount, 'discount')
```
![ScreenShot](../../image/discount_dp21.png)

- ### `step 12`:
``` javascript
function ShoppingCart() {
  this.products = [];

  this.addProduct = function(p) {
    this.products.push(p);
  };
}
const sc = new ShoppingCart();
```
![ScreenShot](../../image/shopping_cart_dp22.png)

- ### `step 13`:
``` javascript
`discount`

function Discount() {
  this.calc = function(products) {
    var ndiscount = new NumberDiscount();
    var pdiscount = new PriceDiscount();
    var none = new NoneDiscount();

    ndiscount.setNext(pdiscount);
    pdiscount.setNext(none);

    return ndiscount.exec(products);
  };
}

const discount = new Discount();
console.log(discount, 'discount')
const sc = new ShoppingCart();
console.log(sc, 'sc')
sc.addProduct(1000);
console.log(sc, 'sc 1')
let resp = discount.calc(sc.products);
console.log(resp, 'resp')
```
![ScreenShot](../../image/all_dp22.png)




- ## All code
``` javascript
function ShoppingCart() {
  this.products = [];

  this.addProduct = function(p) {
    this.products.push(p);
  };
}

function Discount() {
  this.calc = function(products) {
    var ndiscount = new NumberDiscount();
    var pdiscount = new PriceDiscount();
    var none = new NoneDiscount();

    ndiscount.setNext(pdiscount);
    pdiscount.setNext(none);

    return ndiscount.exec(products);
  };
}

function NumberDiscount() {
  this.next = null;
  this.setNext = function(fn) {
    this.next = fn;
  };

  this.exec = function(products) {
    var result = 0;
    if (products.length > 3)
      result = 0.05;

    return result + this.next.exec(products);
  };
}

function PriceDiscount() {
  this.next = null;

  this.setNext = function(fn) {
    this.next = fn;
  };

  this.exec = function(products) {
    var result = 0;
    var total = products.reduce(function(a, b) {
      return a + b;
    });

    if (total >= 500)
      result = 0.1;

    return result + this.next.exec(products);
  };
}

function NoneDiscount() {
  this.exec = function() {
    return 0;
  };
}
```