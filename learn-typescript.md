# ✨ TypeScript Introduction

> TypeScript is JavaScript with added syntax for types.

## What is TypeScript?
TypeScript is a syntactic superset of JavaScript which adds **static typing**.

This basically means that TypeScript adds syntax on top of JavaScript, allowing developers to add **types**.

> TypeScript being a "Syntactic Superset" means that it shares the same base syntax as JavaScript, but adds something to it.

## Why should I use TypeScript?
JavaScript is a loosely typed language. It can be difficult to understand what types of data are being passed around in JavaScript.

In JavaScript, function parameters and variables don't have any information! So developers need to look at documentation, or guess based on the implementation.

TypeScript allows specifying the types of data being passed around within the code, and has the ability to report errors when the types don't match.

For example, TypeScript will report an error when passing a string into a function that expects a number. JavaScript will not.

> TypeScript uses compile time type checking. Which means it checks if the specified types match **before** running the code, not **while** running the code.

## How do I use TypeScript?
A common way to use TypeScript is to use the official TypeScript compiler, which transpiles TypeScript code into JavaScript.

The next section shows how to get the compiler setup for a local project.

Some popular code editors, such as Visual Studio Code, have built-in TypeScript support and can show errors as you write code!

# ✨ TypeScript Getting Started
## TypeScript Compiler
TypeScript is transpiled into JavaScript using a compiler.

> TypeScript being converted into JavaScript means it runs anywhere that JavaScript runs!

## Installing the Compiler
TypeScript has an official compiler which can be installed through npm.

Within your npm project, run the following command to install the compiler:

```shell
npm install typescript --save-dev
```

The compiler is installed in the `node_modules` directory and can be run with: `npx tsc`.

```shell
npx tsc
```

## Configuring the compiler
By default the TypeScript compiler will print a help message when run in an empty project.

The compiler can be configured using a `tsconfig.json` file.

You can have TypeScript create `tsconfig.json` with the recommended settings with:

```shell
npx tsc --init
```

Here is an example of more things you could add to the `tsconfig.json` file:

```json
{
	"include": ["src"],
	"compilerOptions": {
		"outDir": "./build"
	}
}
```

You can open the file in an editor to add those options. This will configure the TypeScript compiler to transpile TypeScript files located in the `src/` directory of your project, into JavaScript files in the `build/` directory.

# ✨ TypeScript Simple Types
Typescript supports some simple types (primitives) you may know.

There are three main primitives in JavaScript and TypeScript.
- **boolean** - true or false values
- **number** - whole numbers and floating point values
- **string** - text values like "TypeScript Rocks"

## Type Assignment
When creating a variable, there are two main ways TypeScript assigns a type:
- Explicit
- Implicit

In both examples below `firstName` is of type `string`

### Explicit Type
**Explicit** - writing out the type:

```ts
let firstName: string = "Dylan";
```

**Explicit** type assignment are easier to read and more intentional.

### Implicit Type
**Implicit** - TypeScript will "guess" the type, based on the assigned value:

```ts
let firstName = "Dylan";
```

> Note: Having TypeScript "guess" the type of a value is called **infer**.

Implicit assignment forces TypeScript to **infer** the value.

**Implicit** type assignment are shorter, faster to type, and often used when developing and testing.

## Error In Type Assignment
TypeScript will throw an error if data types do not match.

**Example**
```ts
let firstName: string = "Dylan" // type string
firstName = 33;  // attemps to re-assign the value to a differnt type
```

**Implicit** type assignment would have made `firstName` less noticeable as a `string`, but both will throw an error:

**Example**
```ts
let firstName = "Dylan"  // inferred to type string
firstName = 33; // attemps to re-assign the value to a different type
```

**JavaScript** will **NOT** throw an error for mismatched types.

## Unable to Infer
TypeScript may not always properly infer what the type of a variable may be. In such cases, it will set the type to `any` which disables type checking.

**Example**
```ts
// Implicit any as JSON.parse doesn't know what type of data it returns so it can be "any" thing...
const json = JSON.parse('55');
// Most expect json to be an object, but it can be a string or a number like this example
console.log(typeof json);
```

This behavior can be disabled by enabling `noImplicitAny` as an option in a TypeScript's project `tsconfig.json`. That is a JSON confile for customizing how some of TypeScript behaves.

> NOTE: you may see primitive types capitalized like `Boolean`.
> 
> boolean !== Boolean
> For this tutorial just know to use the lower-cased values, the upper-case ones are for very specific circumstances.

# ✨ TypeScript Special Types
TypeScript has special types that may not refer to any specific type of data.

## Type: any
`any` is a type that disables type checking and effectively allows all types to be used.

The example below does not use `any` and will throw an error:

**Example without `any`**
```ts
let u = true;
u = "string"; // Error: Type 'string' is not assignable to type 'boolean'
Math.round(u); // Error: Argument of type 'boolean' is not assignable to parameter of type 'number'.
```

Setting `any` to the special type `any` disables type checking:

**Example with `any`**
```ts
let v: any = true;
v = 'string'; // no error as it can be 'any' type
Math.round(v); // no error as it can be 'any' type
```

> `any` can be a useful way to get past errors since it disables type checking, but TypeScript will not be able provide type safety, and tools which rely on type data, such as auto completion, will not work. Remember, it should be avoided at 'any' cost...

## Type: unknown
`unknown` is a similar, but safer alternative to `any`.

TypeScript will prevent `unknown` types from being used, as shown in the below example:

```ts
let w: unknown = 1;
w = 'string'; // no error
w = {
	runANonExistentMethod: () => {
		console.log("I think therefore I am");
	}
} as { runANonExistentMethod: () => void }
// How can we avoid the error for the code commented out below when we don't know the type?
// w.runANonExistentMethod(); // Error: Object is of type 'unknown'.
if (typeof w === 'object' && w !== null) {
	(w as { runANonExistentMethod: Function }).runANonExistentMethod();
}
// Although we have to cast multiple times we can do a check in the if to secure our type and have a safer casting
```

Compare the example above to the previous example, with `any`.

> `unknown` is best used when you don't know the type of data being typed. To add a type later, you'll need to cast it.
> 
> Casting is when we use the "as" keyword to say property or variable is of the casted type.

## Type: never
`never` effectively throws an error whenever it is defined.

```ts
let x: never = true; // Error: Type 'boolean' is not assignable to the type 'never'
```

> `never` is rarely used, especially by itself, its primary use is in advanced generics.

## Type: undefined & null
`undefined` and `null` are types that refer to the JavaScript primitives `undefined` and `null` respectively.

```ts
let y: undefined = undefined;
let z: null = null;
```

> These types don't have much use unless `strictNullChecks` is enable in the tsconfig.json file.

# ✨ TypeScript Arrays
TypeScript has a specific syntax for typing arrays.

**Example**
```ts
const names: string[] = [];
names.push("Dylan"); // no error
// names.push(3); // Error: Arguments of type 'number' is not assignable to parameter of type 'string'
```

## Readonly
The `readonly` keyword can prevent arrays from being changed.

```ts
const names: readonly string[] = ['Dylan'];
names.push("Jack"); // Error: Property 'push' does not exist on type 'readonly string[]'
// try removing the readonly modifier and see if it works?
```

## Type Inference
TypeScript can infer the type of an array if it has values.

**Example**
```ts
const numbers = [1, 2, 3]; // inferred to type number[]
numbers.push(4); // no error
// comment line below out to see the successful assignment
numbers.push("2"); // Error: Argument of type 'string' is not assignable to parameter of type 'number'
let head: number = numbers[0]; // no error
```

# ✨ TypeScript Tuples
## Typed Arrays
A **tuple** is a typed <u>array</u> with a pre-defined length and types for each index.

Tuples are great because they allow each element in the array to be in known type of value.

To define a tuple, specify the type of each element in the array:

**Example**
```ts
// define our tuple
let ourTuple: [number, boolean, string];

// initialize correctly
ourTuple = [5, false, 'Coding God was here'];
```

As you can see we have a number, boolean, and a string. But what happens if we try to set them in the wrong order:

**Example**
```ts
// define our tuple
let ourTuple: [number, boolean, string];

// initialized incorrectly which throws an error
ourTuple = [false, 'Coding God was mistaken', 5];
```

> Even though we have a `boolean`, `string`, and `number` the order matters in our tuple and will throw an error.

## Readonly Tuple
A good practice is to make your **tuple** `readonly`.

Tuples only have strongly defined types for the initial values:

**Example**
```ts
// define our tuple
let ourTuple: [number, boolean, string];

// initialize correctly
ourTuple = [5, false, 'Coding God was here'];

// we have no type safety in our tuple for index 3+
ourTuple.push('Something new and wrong');
console.log(ourTuple);
```

You see the new valueTuples only have strongly defined types for the initial values:

**Example**
```ts
// define our readonly tuple
const ourReadonlyTuple: readonly [number, boolean, string] = [5, true, 'The Real Coding God'];

// throws error as it is readonly.
ourReadonlyTuple.push('Coding God took a day off');
```

## Named Tuples
**Named tuples** allow us to provide context for our values at each index.

**Example**
```ts
const graph: [x: number, y: number] = [55.2, 41.3];
```

> **Named tuples** provide more context for what our index values represent.

## Destructing Tuples
Since tuples are arrays we can also destructure them.

**Example**
```ts
const graph: [number, number] = [55.2, 41.3];
const [x, y] = graph;
```

# ✨ TypeScript Object Types
TypeScript has a specific syntax for typing objects.

**Example**
```ts
const car: { type: string, model: string, year: number } = {
	type: "Toyota",
	model: "Corolla",
	year: 2009
};
```

## Type Inference
TypeScript can infer the types of properties based on their values.

**Example**
```ts
const car = {
	type: "Toyota",
};
car.type = "Ford" // no error
car.type = 2; // Error: Type 'number' is not assignable to type 'string'.
```

## Optional Properties
Optional properties are properties that don't have to be defined in the object definition.

**Example without an optional property**
```ts
const car: { type: string, mileage: number } = {
 // Error: Property 'mileage' is missing in type ' {type: string }' but required in type '{ type: string; mileage: number }'.
	type: "Toyota",
};
car.mileage = 2000;
```

**Example with an optional property**
```ts
const car: { type: string, mileage?: number } = {
	type: "Toyota"
};
car.mileage = 2000;
```

## Index Signatures
Index signatures can be used for objects without a defined list of properties.

**Example**
```ts
const nameAgeMap: { [index: string]: number } = {};
nameAgeMap.Jack = 25; // no error
nameAgeMap.Mark = "Fifty"; // Error: Type 'string' is not assignablee to type 'number'
```

> Index signatures like this one can also be expressed with utility types like `Record<string, number>`.

# ✨ TypeScript Enums
An **enum** is a special "class" that represents a group of constants (unchangeable variables).

Enums come in two flavors `string` and `numeric`. Lets start with numeric.

## Numeric Enums - Default
By default, enums will initialize the first value to `0` and add 1 to each additional value:

**Example**
```ts
enum CardinalDirections {
	North,
	East,
	South,
	West
}
let currentDirrection = CardinalDirections.North;
// logs 0
console.log(currentDirrection);
// throws error as 'North' is not a valid enum
currentDirection = 'North';
// Error: "North" is not assignable to type 'CardinalDirections'
```

## Numeric Enums - Initialized
You can set the value of the first numeric enum and have it auto increment from that:

**Example**
```ts
enum CardinalDirections {
	North = 1,
	East,
	South,
	West
}
// logs 1
console.log(CardinalDirections.North);
// logs 4
console.log(CardinalDirections.West)
```

## Numeric Enums - Fully Initialized
You can assign unique number values for each enum value. Then the values will not incremented automatically:

**Example**
```ts
enum StatusCodes {
	NotFound = 404,
	Success = 200,
	Accepted = 202,
	BadRequest = 400
}
// logs 404
console.log(StatusCodes.NotFound);
// logs 200
console.log(StatusCodes.Success);
```

## String Enums
Enums can also contain `strings`. This is more common than numeric enums, because of their readability and intent.

**Example**
```ts
enum CardinalDirections {
	North = 'North',
	East = 'East',
	South = 'South',
	West = 'West'
}; 
// logs 'North'
console.log(CardinalDirections.North);
// logs 'West'
console.log(CardinalDirections.West);
```

> Technically, you can mix and match string and numeric enum values, but it is recommended not to do so.

# ✨ TypeScript Type Aliases and Interfaces
TypeScript allows types to be defined separately from the variables that use them.

Aliases and Interfaces allows types to be easily shared between different variables/objects.

## Type Aliases
Type Aliases allow defining types with a custom name (an Alias).

Type Aliases can be used for primitives like `string` or more complex types such as `objects` and `arrays`:

**Example**
```ts
type CarYear = number
type CarType = string
type CarModel = string

type Car = {
	year: CarYear,
	type: CarType,
	model: CarModel
}

const carYear: CarYear = 2001
const carType: CarType = "Toyota"
const carModel: CarModel = "Corolla"
const car: Car = {
	year: carYear,
	type: carType,
	model: carModel
};
```

## Interfaces
Interfaces are similar to type aliases, except they **only** apply to `object` types.

**Example**
```ts
interface Rectangle {
	height: number,
	width: number
}

const rectangle: Rectangle = {
	height: 20,
	width: 10
};
```

## Extending Interfaces
Interfaces can extend each other's definition.

> **Extending** an interface means you are creating a new interface with the same properties as the original, plus something new.

**Example**
```ts
interface Rectangle {
	height: number,
	width: number
} 

interface ColoredRectangle extends Rectangle {
	color: string
}

const coloredRectangle: ColoredRectangle = {
	height: 20,
	width: 10,
	color: 'red'
};
```

# ✨ TypeScript Union Types
**Union types** are used when a value can be more than a single type.

Such as when a property would be `string` or `number`.

## Union | (OR)
Using the `|` we are saying our parameters is a `string` or `number`:

**Example**
```ts
function printStatusCode(code: string | number) {
	console.log(`My status code is ${code}.`)
}
printStatusCode(404);
printStatusCode('404');
```

## Union Type Errors
**Note**: you need to know what your type is when union types are being used to avoid type errors:

**Example**
```ts
function printStatusCode(code: string | number) {
	console.log(`My status code is ${code.toUpperCase()}.`) // error: Property 'toUpperCase' does not exist ontype 'string | number'.
	Property 'toUpperCase' does not exist on type 'number'
}
```

In our example we are having an issue invoking `toUpperCase()` as its a `string` method and `number` doesn't have access to it.

# ✨ TypeScript Functions
TypeScript has a specific syntax for typing function parameters and return values.

## Return Type
The type of the value returned by the function can be explicitly defined.

**Example**
```ts
// the `: number` here specifies that this function returns a number
function getTime(): number {
	return new Date().getTime();
}
```

> If no return type is defined, TypeScript will attempt to infer it through the types of the variables or expressions returned.

## Void Return Type
The type `void` can be used to indicate a function doesn't return any value.

**Example**
```ts
function printHello(): void {
	console.log('Hello!'):
}
```

## Parameters
Function parameters are typed with a similar syntax as variable declarations.

**Example**
```ts
function multiply(a: number, b: number) {
	return a * b;
}
```

> If no parameter type is defined, TypeScript will default to using **any**, unless additional type information is available as shown in the Default Parameters and Type Alias section below.

## Optional Parameters
By default TypeScript will assume all parameters are required, but they can be explicitly marked as optional.

**Example**
```ts
// the `?` operator here marks parameter `c` as optional
function add(a: nnumber, b: number, c?: number) {
	return a + b + (c || 0);
}
```

## Default Parameters
For parameters with default values, the default value goes after the type annotation:

**Example**
```ts
function pow(value: number, exponent: number = 10) {
	return value ** exponent;
}
```

TypeScript can also infer the type from the default value.

## Named Parameters
Typing named parameters follows the same pattern as typing normal paramters.

**Example**
```ts
function divide({ dividend, divisor }: { dividend: number, divisor: number }) {
	return dividend / divisor;
}
```

## Rest Parameters
Rest parameters can be typed like normal parameters, but the type must be an array as rest parameters are always arrays.

**Example**
```ts
function add(a: number, b: number, ...rest: number[]) {
	return a + b + rest.reduce((p, c) => p + c, 0);
}
```

## Type Alias
Function types can be specified separately from functions with type aliases.

These types are written similarly to arrow functions.

**Example**
```ts
type Negate = (value: number) => number;

// in this function, the parameter `value` automatically gets assigned the type `number` from the type `Negate`

const negateFunction: Negate = (value) => value * -1;
```

# ✨ TypeScript Casting
There are times when working with types where it's necessary to override the type of a variable, such as when incorrect types are provided by a library.

Casting is the process of overriding a type.

## Casting with `as`
A straightforward way to cast a variable is using the `as` keyword, which will directly change the type of the given variable.

**Example**
```ts
let x: unknown = 'hello';
console.log((x as string).length);
```

> Casting doesn't actually change the type of the data within the variable, for example the following code with not work as expected since the variable **x** is still holds a number.

```ts
>let x: unknown = 4; 
>console.log((x as string).length);  // prints undefined since number don't have a length
```

> TypeScript will still attempt to typecheck casts to prevent casts that don't seem correct, for example the following will throw a type error since TypeScript knows casting a string to a number doesn't makes sense without converting the data:

```ts
console.log((4 as string).lenth);  // Error: Conversion of type 'number' to type 'string' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first.
```

> The Force casting section below covers how to override this.

## Casting with `<>`
Using <> works the same as casting with `as`.

**Example**
```ts
let x: unknown = 'hello';
console.log((<string>x).length);
```

> This type of casting will not work with TSX, such as when working on React files.

## Force casting
To override type errors that TypeScript may throw when casting, first cast to `unknown`, then to the target type.

**Example**
```ts
let x = 'hello';
console.log(((x as unknown) as number).length); // x is not actually a number so this will return undefined
```

# ✨ TypeScript Classes
TypeScript adds types and visibility modifiers to JavaScript classes.

## Members: Types
The members of a class (properties & methods) are typed using type annotations, similar to variables.

**Example**
```ts
class Person {
	name: string;
}

const person = new Person();
person.name = "Jane";
```

## Members: Visibility
Class members also be given special modifiers which affect visibility.

There are three main visibility modifiers in TypeScript.
- **public** - (default) allows access to the class member from anywhere
- **private** - only allows access to the class member from within the class
- **protected** - allows access to the class member from itself and any classes that inherit it, which covered in the inheritance section below

**Example**
```ts
class Person {
	private name: string;

	public constructor(name: string) {
		this.name = name;
	}

	public getName(): string {
		return this.name;
	}
}

const person = new Person('Jane');
console.log(person.getName()); // person.name isn't accessible from outside the class since it's private
```

> The `this` keyword in a class usually refers to the instance of the class.

## Parameter Properties
TypeScript provides a convenient way to define class members in the constructor, by adding a visibility modifiers to the parameter.

**Example**
```ts
class Person {
	// name is a private member variable
	public constructor(private name: string) {}

	public getName(): string {
		return this.name;
	}
}

const person = new Person('Jane');
console.log(person.getName());
```

## Readonly
Similar to arrays, the `readonly` keyword can prevent class members from being changed.

**Example**
```ts
class Person {
	private readonly name: string;

	public constructor(name: string) {
	// name cannot be changed after this initial definition, which has to be either at it's declaration or in the constructor.
	this.name = name;
	}

	public getName(): string {
		return this.name;
	}
}

const person = new Person('Jane');
console.log(person.getName());
```

## Inheritance: Implements
Interfaces (covered [[#✨ TypeScript Type Aliases and Interfaces]]) can be used to defined the type a class must follow through the `implements` keyword.

**Example**
```ts
interface Shape {
	getArea: () => number;
}

class Rectangle implements Shape {
	public constructor(protected readonly width: number, protected readonly height: number) {}

	public getArea(): number {
		return this.width * this.height;
	}
}
```

> A class can implement multiple interfaces by listing each one after `implements`, separated by a comma like so: `class Rectangle implements Shape, Colored {`

## Inheritance: Extends
Classes can extend each other through the `extends` keyword. A class can only extends one other class.

**Example**
```ts
interface Shape {
	getArea: () => number;
}

class Rectangle implements Shape {
	public constructor(protected readonly width: number, protected readonly height: number) {}

	public getArea(): number {
		return this.width * this.height;
	}
}

class Square extends Rectangle {
	public constructor(width: number) {
		super(width, width);
	}

	// getArea gets inherited from Rectangle
}
```

## Override
When a class extends another class, it can replace the members of the parent class with the same name.

Newer versions of TypeScript allow explicitly marking this with the `override` keyword.

**Example**
```ts
interface Shape {
	getArea: () => number;
}

class Rectangle implements Shape {
	// using protected for these members allows access from classes that extend from this class, such as Square
	public constructor(protected readonly width: number, protected readonly height: number) {}

	public getArea(): number {
		return this.width * this.height;
	}

	public toString(): string {
		return `Rectangle[width=${this.width}, height=${this.height}]`;
	}
}

class Square extends Rectangle {
	public constructor(width: number) {
		super(width, width);
	}

	// this toString replaces the toString from Rectangle
	public override toString(): string {
		return `Square[width=${this.width}]`;
	}
}
```

> By default the **override** keyword is optional when overriding a method, and only helps to prevent accidentally overriding a method that does not exist. Use the setting **noImplicitOverride** to force it to be used when overriding.

## Abstract Classes
Classes can be written in a way that allows them to be used as a base class for other classes without having to implement all the members. This is done by using the `abstract` keyword. Members that are left unimplemented also use the `abstract` keyword.

**Example**
```ts
abstract class Polygon {
	public abstract getArea(): number;

	public toString(): string {
		return `Polygon[area=${this.getArea()}]`;
	}
}

class Rectangle extends Polygon {
	public constructor(protected readonly width: number, protected readonly height: number) {
		super();
	}

	public getArea(): number {
		return this.width * this.height;
	}
}
```

> Abstract classes cannot be directly instantiated, as they do not have all their members implemented.

# ✨ TypeScript Basic Generics
Generics allow creating 'type variables' which can be used to create classes, functions & type aliases that don't need to explicitly define the types that they use.

Generics makes it easier to write reusable code.

## Functions
Generics with functions help make more generalized methods which more accurately represent the types used and returned.

**Example**
```ts
function createPair<S, T>(vl: S, vs: T): [S, T] {
	return [v1, v2];
}
console.log(createPair<string, number>('hello', 42)); // ['hello', 42]
```

> TypeScript can be also infer the type of the generic parameter from the function parameters.

## Classes
Generics can be used to create generalized classes, like <u>JavaScript Maps</u>.

**Example**
```ts
class NamedValue<T> {
	private _value: T | undefined;

	constructor(private name: string) {}

	public setValue(value: T) {
		this._value = value;
	}

	public getValue(): T | undefined {
		return this._value;
	}

	public toString(): string {
		return `${this.name}: ${this._value}`;
	}
}

let value = new NamedValue<number>('myNumber');
value.setValue(10);
console.log(value.toString()); // myNumber: 10
```

> TypeScript can also infer the type of the generic parameter if it's used in a constructor parameter.

## Type Aliases
Generics in type aliases allow creating types that are more reusable.

**Example**
```ts
type Wrapped<T> = { value: T };

const wrappedValue: Wrapped<number> = { value: 10 };
```

> This also works with interfaces with the following syntax: `interface Wrapped<T> {`

## Default Value
Generics can be assigned default values which apply if no other value is specified or inferred.

**Example**
```ts
class NamedValue<T = string> {
	private _value: T | undefined;

	constructor(private name: string) {}

	public setValue(value: T) {
		this._value = value;
	}

	public getValue(): T | undefined {
		return this._value;
	}

	public toString(): string {
		return `${this.name}: ${this._value}`;
	}
}

let value = new NamedValue('myNumber');
value.setValue('myValue');
console.log(value.toString()); // myNumber: myValue
```

## Extends
Constraints can be added to generics to limit what's allowed. The constraints make it possible to rely on a more specific type when using the generic type.

**Example**
```ts
function createLoggedPairs<S extends string } number, T extends string | number>(v1: S, v2: T): [S, T] {
	console.log(`creating pair: v1='${v1}', v2='${v2}'`);
	return [v1, v2];
}
```

> This can be combined with a default value.

# ✨ TypeScript Utility Types
TypeScript comes with a large number of types that can help with some common type manipulation, usually referred to as utility types.

This chapter covers the most popular utility types.

## Partial
`Partial` changes all the properties in an object to be optional.

**Example**
```ts
interface Point {
	x: number;
	y: number;
}

let pointPart: Partial<Point> = {}; // `Partial` allows x and y to be optional
pointPart.x = 10;
```

## Required
`Required` changes all the properties in an object to be required.

**Example**
```ts
interface Car {
	make: string;
	model: string;
	mileage?: number;
}

let myCar: Required<Car> = {
	make: 'Ford',
	model: 'Focus',
	mileage: 12000 // `Required` foces mileage to be defined
};
```

## Record
`Record` is a shortcut to defining an object type with a specific key type and value type.

**Example**
```ts
const nameAgeMap: Record<string, number> = {
	'Alice': 21,
	'Bob': 25
};
```

> `Record<string, number>` is equivalent to `{ [key: string]: number }`

## Omit
`Omit` removes keys from an object type.

**Example**
```ts
interface Person {
	name: string;
	age: number;
	location?: string;
}

const bob: Omit<Person, 'age' | 'location'> = {
	name: 'Bob'
	// `Omit` has removed age and location from the type and they can't be defined here
};
```

## Pick
`Pick` removes all but the specified keys from an object type.

**Example**
```ts
interface Person {
	name: string;
	age: number;
	location?: string;
}

const bob: Pick<Person, 'name'> = {
	name: 'Bob'
	// `Pick` has only kept name, so age and location were removed from the type and they can't be defined here
};
```

## Exclude
`Exclude` removes types from an union.

**Example**
```ts
type Primitive = string | number | boolean
const value: Exclude<Primitive, string> = true;  // a string cannot be used here since Exclude removed it from the type.
```

## ReturnType
`ReturnType` extracts the return type of a function type.

**Example**
```ts
type PointGenerator = () => { x: number; y: number };
const point: ReturnType<PointGenerator> = {
	x: 10,
	y: 20
};
```

## Parameters
`Parameters` extracts the parameter types of a function types as an array.

**Example**
```ts
type PointPrinter = (p: { x: number; y: number; }) => void;
const point: Parameters<PointPrinter>[0] = {
	x: 10,
	y: 20
};
```

# ✨ TypeScript Keyof
`keyof` is a keyword in TypeScript which is used to extract the key type from an object type.

## **keyof** with explicit keys
When used on an object type with explicit keys, `keyof` creates a union type with those keys.

**Example**
```ts
interface Person {
	name: string;
	age: number;
}
// `keyof Person` here creates a union type of "name" and "age", other strings will not be allowed

function printPersonProperty(person: Person, property: keyof Person) {
	console.log(`Printing person property ${property}: "${person[property]}"`);
}
let person = {
	name: "Max",
	age: 27
};
printPersonProperty(person, "name"); // Printing person property name: "Max"
```

## **keyof** with index signatures
`keyof` can also be used with index signatures to extract the index type.

```ts
type StringMap = { [key: string]: unknown };
// `keyofStringMap` resolve to `string` here
function createStringPair(property: keyof StringMap, value: string): StringMap {
	return { [property]: value };
}
```

# ✨ TypeScript Null & Undefined
TypeScript has a powerful system to deal with `null` or `undefined` values.

> By default `null` and `undefined` handling is disabled, and can be enabled by setting `strickNullChecks` to true.
> 
> The rest of this page applies for when `strictNullCheck` is enabled.

## Types
`null` and `undefined` are primitive types and can be used like other types, such as `string`.

**Example**
```ts
let value: string | undefined | null = null;
value = 'hello':
value = undefined;
```

> When `strictNullChecks` is enabled, TypeScript requires values to be set unless `undefined` is explicitly added to the type.

## Optional Chaining
Optional Chaining is a JavaScript feature that works well with TypeScript's null handling. It allows accessing properties on an object, that may or may not exist, with a compact syntax. It can be used with the `?.` operator when accessing properties.

**Example**
```ts
interface House {
	sqft: number;
	yard?: {
		sqft: number;
	};
}
function printYardSize(house: House) {
	const yardSize = house.yard?.sqft;
	if (yardSize === undefined) {
		console.log('No yard');
	} else {
		console.log(`Yard is ${yardSize} sqft`);
	}
}

let home: House = {
	sqft: 500
};

printYardSize(home); // Prints 'No yard'
```

## Nullish Coalescence
Nullish Coalescence is another JavaScript feature that also works well with TypeScript's null handling. It allows writing expressions that have a fallback specifically when dealing with `null` or `undefined`. This is usedful when other falsy values can occur in the expression but are still valid. It can be used with the `??` operator in an expression, similar to using the `&&` operator.

**Example**
```ts
function printMileage(mileage: number | null | undefined) {
	console.log(`Mileage: ${mileage ?? 'Not Available'}`);
}

printMileage(null); // Prints 'Mileage: Not Available'
printMileage(0); // Prints 'Mileage: 0'
```

## Null Assertion
TypeScript's inference system isn't perfect, there are times when it makes sense to ignore a value's possibility of being `null` or `undefined`. An easy way to do this is to use casting, but TypeScript also provides the `!` operator as a convenient shortcut.

**Example**
```ts
function getValue(): string | undefined {
	return 'hello';
}
let value = getValue();
console.log('value length: ' + value!.length);
```

> Just like casting, this can be unsafe and should be used with care.

## Array bounds handling
Even with `strictNullChecks` enabled, by default TypeScript will assume array access will never return undefined (unless undefined is part of the array type).

The config `noUncheckedIndexedAccess` can be used to change this behavior.

**Example**
```ts
let array: number[] = [1, 2, 3];
let value = array[0]; // with `noUncheckedIndexedAccess` this has the type `number | undefined`
```

# ✨ TypeScript Definitely Typed
NPM packages in the broad JavaScript ecosystem doesn't always have types available.

Sometimes the project are no longer maintained, and other times they aren't interested in, agree with, or have time to use TypeScript.

## Using non-typed NPM packages in TypeScript
Using untyped NPM packages with TypeScript will not be type safe due  to lack of types.

Definitely Typed is a project that provides a central repository of TypeScript definitions for NPM packages which do not have types.

**Example**
```sh
npm install --save-dev @types/jquery
```

No other steps are usually needed to use the types after installing the declaration package, TypeScript will automatically pick up the types when using the package itself.

> Editors such as Visual Studio Code will often suggest installing packages like these when types are missing.