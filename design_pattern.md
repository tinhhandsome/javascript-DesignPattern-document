## Module Pattern

```javascript
var myModule = {
  myProperty: "someValue",
  // object literals can contain properties and methods.
  // here, another object is defined for configuration
  // purposes:
  myConfig: {
    useCaching: true,
    language: "en",
  },
  // a very basic method
  myMethod: function () {
    console.log("I can haz functionality?");
  },
  // output a value based on current configuration
  myMethod2: function () {
    console.log(
      "Caching is:" + this.myConfig.useCaching ? "enabled" : "disabled"
    );
  },
  // override the current configuration
  myMethod3: function (newConfig) {
    if (typeof newConfig == "object") {
      this.myConfig = newConfig;
      console.log(this.myConfig.language);
    }
  },
};
myModule.myMethod(); // I can haz functionality
myModule.myMethod2(); // outputs enabled
myModule.myMethod3({
  language: "fr",
  useCaching: false,
});
```

## Factory Method

- This makes an instance of several derived classes based on interfaced
  data or events.
- Factory Method Điều này tạo ra một phiên bản của một số lớp dẫn xuất dựa trên giao diện
  dữ liệu hoặc sự kiện.

## Creational

    Based on the concept of creating an object.

## Class

    - Factory Method:
    This makes an instance of several derived classes based on interfaced
    data or events.

## Object

    - Abstract Factory: Creates an instance of several families of classes without detailing concrete classes.
    - Builder: Separates object construction from its representation, always creates the same type of object.
    - Prototype: A fully initialized instance used for copying or cloning.
    - Singleton: A class with only a single instance with global access points.

## Structural

- Based on the idea of building blocks of objects
  Class

- Adapter: Match interfaces of different classes therefore classes can work together despite incompatible interfaces
  Object
  Adapter Match interfaces of different classes therefore classes can work together
  despite incompatible interfaces
  Bridge Separates an object's interface from its implementation so the two can
  vary independently
  Composite A structure of simple and composite objects which makes the total object
  more than just the sum of its parts.
  Decorator Dynamically add alternate processing to objects.
  Facade A single class that hides the complexity of an entire subsystem.
  Flyweight A fine-grained instance used for efficient sharing of information that is
  contained elsewhere.
  Proxy A place holder object representing the true object
  Behavioral Based on the way objects play and work together.
  Class
  Interpreter A way to include language elements in an application to match the
  grammar of the intended language.
  Template Method Creates the shell of an algorithm in a method, then defer the exact steps
  to a subclass.
  18 | Chapter 8: Design Pattern CategorizationObject
  Chain of Responsibility A way of passing a request between a chain of objects to find the object
  that can handle the request.
  Command Encapsulate a command request as an object to enable, logging and/or
  queuing of requests, and provides error-handling for unhandled requests.
  Iterator Sequentially access the elements of a collection without knowing the
  inner workings of the collection.
  Mediator Defines simplified communication between classes to prevent a group
  of classes from referring explicitly to each other.
  Memento Capture an object's internal state to be able to restore it later.
  Observer A way of notifying change to a number of classes to ensure consistency
  between the classes.
  State Alter an object's behavior when its state changes
  Strategy Encapsulates an algorithm inside a class separating the selection from
  the implementation
  Visitor Adds a new operation to a class without changing the class
