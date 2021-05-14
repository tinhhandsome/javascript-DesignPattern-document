## Tìm hiểu Decorator Dessign Pattern



## Synta Es6
``` javascript
class Pasta {
  constructor() {
    this.price = 0;
  }
  getPrice() {
    return this.price;
  }
}

class Penne extends Pasta {
  constructor() {
    super();
    this.price = 8;
  }
}

class PastaDecorator extends Pasta {
  constructor(pasta) {
    super();
    this.pasta = pasta;
  }

  getPrice() {
    return this.pasta.getPrice();
  }
}

class SauceDecorator extends PastaDecorator {
  constructor(pasta) {
    super(pasta);
  }

  getPrice() {
    return super.getPrice() + 5;
  }
}

class CheeseDecorator extends PastaDecorator {
  constructor(pasta) {
    super(pasta);
  }

  getPrice() {
    return super.getPrice() + 3;
  }
}
```

## Synta Es5
```javascript
function Pasta() {
  this.price = 0;
}
Pasta.prototype.getPrice = function() {
  return this.price;
};

function Penne() {
  this.price = 8;
}
Penne.prototype = Object.create(Pasta.prototype);

function SauceDecorator(pasta) {
  this.pasta = pasta;
}

SauceDecorator.prototype.getPrice = function() {
  return this.pasta.getPrice() + 5;
};

function CheeseDecorator(pasta) {
  this.pasta = pasta;
}

CheeseDecorator.prototype.getPrice = function() {
  return this.pasta.getPrice() + 3;
};

```