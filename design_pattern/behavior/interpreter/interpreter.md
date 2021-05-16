# Learn About Interpreter Design

``` javascript
var result = new Sum(new Num(100), new Min(new Num(100), new Num(50)));
expect(result.interpret()).to.equal(150);
```
we see
``` javascript
var result = new Sum(new Num(100), new Min(new Num(100), new Num(50)));
```
new Sum(new Num, new Min( new Num, new Num))

``` javascript
  constructor(left, right) {
    this.left = left;
    this.right = right;
  }
```
So có 2 tham số

- this.left = this.val = 100 (new Num)
- this.right = new Min(new Num(100), new Num(50))
So
- new Num(100) <=> this.val = 100
- new Num(50) <=> this.val = 50
- new Min(Num(100), Num(50))
- this.left = new Num(100) return 100
- this.right = new Num(50) return 50
- result.interpret()
- return this.left.interpret() + this.right.interpret() (new Min)
- Min( method interpret )
- return  this.left.interpret() - this.right.interpret()
- return 100 - 50
- => result = 100 + 50 = 150


## syntax es6
``` javascript
class Sum {

  constructor(left, right) {
    this.left = left;
    this.right = right;
  }

  interpret() {
    return this.left.interpret() + this.right.interpret();
  }
}

class Min {

  constructor(left, right) {
    this.left = left;
    this.right = right;
  }

  interpret() {
    return this.left.interpret() - this.right.interpret();
  }
}

class Num {

  constructor(val) {
    this.val = val;
  }

  interpret() {
    return this.val;
  }
}

export {
  Num,
  Min,
  Sum
};

```
## syntax es5
``` javascript
```