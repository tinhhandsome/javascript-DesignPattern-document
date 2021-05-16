## Learn about Mediator Design Pattern

``` javascript
  var trafficTower = new TrafficTower();
  var boeing1 = new Airplane(10, trafficTower);
  var boeing2 = new Airplane(15, trafficTower);
  var boeing3 = new Airplane(55, trafficTower);

  expect(boeing1.requestPositions()).to.deep.equals([10, 15, 55]);
```
- var trafficTower = new TrafficTower()
- var boeing1 = new Airplane(10, trafficTower)
- var boeing1 = new Airplane(10, new TrafficTower)
- contructor Airplane
``` javascript
    constructor(position, trafficTower) {
      this.position = position;
      this.trafficTower = trafficTower;
      this.trafficTower.airplanes.push(this);
    }
  
```
- this.position = 10
- this.trafficTower = new TrafficTower
- this = (10, new TrafficTower)
- this.trafficTower.airplanes.push(this)
- constructor TrafficTower

``` javascript
    constructor() {
      this.airplanes = [];
    }
```
- this.airplanes = [new Airplane(10, TrafficTower)]
- the same, similar
- this.airplanes = [new Airplane(10, TrafficTower),
                    new Airplane(15, TrafficTower),
                    new Airplane(55, TrafficTower)]
```javascript
boeing1.requestPositions()
```
- return this.trafficTower.requestPositions()
``` javascript
    return this.airplanes.map(airplane => {
        return airplace.position
    })
```
- [10, 15, 55]
## syntax es6
``` javascript
class TrafficTower {

  constructor() {
    this.airplanes = [];
  }

  requestPositions() {
    return this.airplanes.map(airplane => {
      return airplane.position;
    });
  }
}

class Airplane {

  constructor(position, trafficTower) {
    this.position = position;
    this.trafficTower = trafficTower;
    this.trafficTower.airplanes.push(this);
  }

  requestPositions() {
    return this.trafficTower.requestPositions();
  }
}
```
## syntax es5
``` javascript
function TrafficTower() {
  this.airplanes = [];
}

TrafficTower.prototype.requestPositions = function() {
  return this.airplanes.map(function(airplane) {
    return airplane.position;
  });
};

function Airplane(position, trafficTower) {
  this.position = position;
  this.trafficTower = trafficTower;
  this.trafficTower.airplanes.push(this);
}

Airplane.prototype.requestPositions = function() {
  return this.trafficTower.requestPositions();
};
```