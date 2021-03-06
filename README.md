# DIFactory

DIFactory makes it easy to instantiate a class whose constructor uses  
dependency injection.

To make DIFactory handle dependency-injection for a class, first you  
need to register that class with DIFactory.  In this example, a class  
is registered right below its own definition:
```
export class ExampleClass{

   constructor(
        // begin injected dependencies...
        blueCar: BlueCar,
        greenCar: GreenCar,
        redCar: RedCar,
        // end injected dependencies
        
        // additional arguments:
        name: string,
        age: number
    ){ ... }

   ...code...

} // Below the closing brace, ExampleClass is registered with DIFactory:

 DIFactory.register(
     {
        class: ExampleClass,

        // Make sure the dependencies are listed in same order as they are 
        // in the constructor parameters above:
        dependencies: [BlueCar, GreenCar, RedCar]
     }
 );
 ```
 And that's it.  Now that it's registered, you can get an instance of  
 ExampleClass:
```
// for the name and age arguments in the constructor, we're passing 'Steve' and 30:
let instance = DIFactory.getInstance(ExampleClass, ['Steve', 30]);
 ```
 In the statement above, the array argument is there to hold any additional  
 arguments that get passed to ExampleClass' constructor after the injected  
 dependencies.   
 (If there are no arguments after the dependencies, it's unnecessary to pass the array.)


## Installation

You must have npm installed first.  Then, in the command line:

```bash
npm install @writetome51/di-factory
```

## Loading
```
// If using TypeScript:
import { DIFactory } from '@writetome51/di-factory';
// If using ES5 JavaScript:
var DIFactory = require('@writetome51/di-factory').DIFactory;
```
