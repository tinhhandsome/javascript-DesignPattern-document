## Learn about Mementor Design pattern

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