## Learn About Interator Design Pattern
``` javascript
function test(Iterator) {
  var numbers = new Iterator([1, 2, 3]);

  expect(numbers.next()).to.equal(1);
  expect(numbers.next()).to.equal(2);
  expect(numbers.next()).to.equal(3);
  expect(numbers.hasNext()).to.false;
}
test(Iterator6);
test(Iterator);
```
- Wee see script
- var numbers = new Iterator([1, 2, 3])
- numbers.next() => 1
- numbers.next() => 2
- numbers.next() => 3
- numbers.hasNext()
``` javascript
var numbers = new Iterator([1, 2, 3])
numbers.next()
```
this.elements = [1, 2, 3]
this.next()
this.elements[this.index++]
[1, 2, 3][1]
- this.hasNext()
- this.index < this.elements.length
-  1 < 3
- we change contructor by method class
## syntax es6
``` javascript
class Iterator {

  constructor(el) {
    this.index = 0;
    this.elements = el;
  }

  next() {
    return this.elements[this.index++];
  }

  hasNext() {
    return this.index < this.elements.length;
  }
}
```

## syntax es5
``` javascript
function Iterator(el) {
  this.index = 0;
  this.elements = el;
}

Iterator.prototype = {
  next: function() {
    return this.elements[this.index++];
  },
  hasNext: function() {
    return this.index < this.elements.length;
  }
};

```