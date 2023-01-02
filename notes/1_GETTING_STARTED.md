# Getting started with typescript

## Goals

1. Learn about Typescript 4
2. Understand the relationship between Typescript snd Javascript
3. Learning the Unified Modeling Language(UML)


### Typescript 4

Basic types in Typescripts includes:

1. Primitive types: Such as number, string, boolean, void, null, undefined, unknown, never, unique, bigint

```ts
    const one: string = "one";
    const two: boolean = false;
    const three: number = 3;
    const four: null = null;
    const five: unknown = 5;
    const six: any = 6;
    const seven: unique symbol = Symbol("seven");
    let eight: never;
    
    // const eight: never will trigger an error, cause a constant of never cannot be initialized
```

2. Enums: Helps creating named constant

```ts
    enum Keys {
    Up,
    Down,
    Left,
    Right
    }

    let up: Keys = Keys.Up;
```

3. Arrays and Tuples: Array is a collection of items, it has a dynamic size while Tuple on the rother hand is a fixed array;

```ts
    const arr: number[] = [1,2,3];
    
    const tup: [number] = [1];
```


4. Class: OOP Abstractions helps in defining objects with specific shape, properties, methods and visiblity.

```ts
    class User {
    private name: string;

    constructor(name: string) {
        this.name = name;
    }
    
    public getName(): string{
        return this.name;
    }
}

const user = new User("Akeju");
console.log(user.getName());
```


```ts
    //abstract classes

    abstract class BaseApiClient {
        abstract fetch(req: any): Promise<any>; 
    //    this abstract fetch will need to be implemented in sub classes
    }
    
    class UsersClient extends BaseApiClient {
    fetch(req: any): Promise<any> {
        return Promise.resolve(undefined);
    }
    }
    
    const client = new UsersClient();
    client.fetch({url:'/user'})
```

4. Interfaces and Types: An abstraction that helps define an shape of an object and its properties without specifying the implementation the object itself

```ts
    interface Comparable<T> {
    compareTo(o: T): number 
    }
    
    
    interface AppConfig {
        paths: {
            base: string;
        };
        maxRetryCount?:number;
    }
    
    
    const appConfig: AppConfig = {
    path: {
        base: '/'
    }
    }
    
    //? means optional: we can choose to add te maxRetryCount to our object or not.


    // Types

    type E = {
        name: string;
    }
    
    type F = E & {
        age: number;
    }
    
    let e: F = {
        name:"Theo",
        age:10
    }
    
    
    // interfaces are most recommended over types except when you need to combines types
```

#### Typescript 4 features

- Variadic tuple types: can be used in modelling 2D or 3D
```ts
    type Point2d = [number, number];
    type Point3d = [number, number, number];
    const point1: Point2d = [1,2];
    const point2: Point3d = [1,2,3];
```

- Type parameter for tuple

```ts
    type Point2d = [number, number];
    type Point3d = [number, number, number];
    
    type NamedType<T extends unknown[]> = [string,...T];
    type: NamedPoint2d = NamedType<Point2d>;
    const point3: NamedPoint2d = ['Point: (1,2)',1,2];
```

- Labeled tuples:
```ts
    type Point2dL = [x: number, y: number];
```

- Template literal types

```ts
    type Suit = `${"Spades" | "Heart" | "Diamond" }}`;
    type Rank = `${"2" | "3" | "4"}`;
    type Deck = `${Rank} of ${Suit}`;
```


