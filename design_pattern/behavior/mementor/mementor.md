## Learn about Mementor Design pattern
``` javascript
    const originator = {
      store: function(val) {
        return new Memento(val);
      },
      restore: function(memento) {
        return memento.value;
      }
    };

    const careTaker = new Caretaker();
    careTaker.addMemento(originator.store("hello"));
    careTaker.addMemento(originator.store("hello world"));
    careTaker.addMemento(originator.store("hello world !!!"));

    var result = originator.restore(careTaker.getMemento(1));
    expect(result).to.equal("hello world");
```
- const careTaker = new Caretaker()
``` javascript
addMemento(memento) {
  this.values.push(memento);
}
```
-`Caretaker` [new Memento('hello')]
- careTaker.addMemento(originator.store("hello world"));
- [ new Memento('hello'),
    new Memento('hello world')]
- careTaker.addMemento(originator.store("hello world !!!"));
- [ new Memento('hello'),
    new Memento('hello world'),
    new Memento('hello world !!!')]
- careTaker.getMemento(1)
- this.values[1];
- = new Memento('hello world')
``` javascript
class Memento {
    constructor(value) {
      this.value = value;
    }
  }
```
- var result = originator.restore(careTaker.getMemento(1));
- result = 'hello world'
## syntax es6
``` javascript
class Memento {
  constructor(value) {
    this.value = value
  }
}

const originator = {
  store: function(val) {
    return new Memento(val)
  },
  restore: function(memento) {
    return memento.value
  }
}

class Caretaker {
  constructor() {
    this.values = []
  }

  addMemento(memento) {
    this.values.push(memento)
  }
  getMemento(index) {
    return this.values[index]
  }
}
```

## syntax es5
``` javascript
function Memento(value) {
    this.value = value
}

var origintor = {
  store: function(val) {
    return new Mementor(val)
  },
  restore: function(memento) {
    return memento.value
  }
}
function Caretaker() {
  this.values = []
}

Caretaker.prototype.addMemento = function(memento) {
  this.values.push(memento)
}

Caretaker.prototype.getMemento = function(index) {
  return this.values[index]
}
```