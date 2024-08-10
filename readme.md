# Variable scoping 
JavaScript mein bhi variable scope ka concept hota hai, jo define karta hai ke ek variable program ke kis hissay mein accessible hai. JavaScript mein primarily do types ke scope hote hain: 

1. **Global Scope**
2. **Local Scope (Function Scope aur Block Scope)**

### 1. Global Scope
- Agar koi variable function ke bahar declare kiya jaye, to woh global scope mein hota hai. Matlab, woh poore program mein kahin bhi accessible hota hai.
- Example:

    ```javascript
    var x = 10;  // Global scope

    function myFunction() {
        console.log(x);  // 10
    }

    myFunction();
    console.log(x);  // 10
    ```

### 2. Local Scope
Local scope further do qisam ka hota hai:

- **Function Scope**
- **Block Scope**

#### Function Scope
- JavaScript mein, agar koi variable kisi function ke andar declare kiya jaye using `var`, to woh sirf us function ke andar hi accessible hota hai. Isay function scope kehte hain.
- Example:

    ```javascript
    function myFunction() {
        var y = 20;  // Function scope
        console.log(y);  // 20
    }

    myFunction();
    console.log(y);  // Error: y is not defined
    ```

#### Block Scope
- ES6 (ECMAScript 2015) ke baad se, JavaScript mein `let` aur `const` keywords ko introduce kiya gaya jo block scope ko follow karte hain. Block scope ka matlab ye hai ke ek variable sirf us block ke andar accessible hota hai jismein usay declare kiya gaya hai. Block ko curly braces `{}` ke saath define kiya jata hai.
- Example:

    ```javascript
    if (true) {
        let z = 30;  // Block scope
        console.log(z);  // 30
    }

    console.log(z);  // Error: z is not defined
    ```

### Summary
- **Global Scope**: Variable poore program mein kahin bhi accessible hota hai. (e.g., `var x = 10;`)
- **Function Scope**: `var` se declare kiya gaya variable sirf us function ke andar accessible hota hai.
- **Block Scope**: `let` aur `const` se declare kiya gaya variable sirf us block ke andar accessible hota hai.

JavaScript mein scope ko samajhna is liye zaroori hai taake aap variables ko effectively manage kar sakein aur unintended bugs se bacha sakein.

# Clouser
Closure aik programming concept hai jo JavaScript jaisi languages mein use hota hai. Ye tab banta hai jab aik function doosre function ke andar banaya jata hai, aur andar wala function bahar wale function ke variables ko use kar sakta hai, chahe bahar wala function khatam bhi ho chuka ho.

### Closure ka use kyun hota hai?

1. **Data ko chhupana**: Closure se hum kuch variables ko private rakh sakte hain, taake wo sirf andar wale function ke zariye access ho sakein.
  
2. **Aik function mein yaad rakhna**: Closure se hum aik function ko banate waqt usmein kuch cheezen yaad rakh sakte hain jo future mein use hoti hain. Jaise aik counter function jo her dafa call karne par aik number barhata hai.

### Example:

```javascript
function createCounter() {
    let count = 0;  // count aik variable hai

    return function() {  // yeh function closure hai
        count++;  // count ko aik bar barhao
        return count;  // count ki updated value return karo
    };
}

const counter1 = createCounter();
console.log(counter1());  // Output: 1
console.log(counter1());  // Output: 2

const counter2 = createCounter();
console.log(counter2());  // Output: 1
console.log(counter2());  // Output: 2
```

### Asaan Alfaaz Mein:
- **Closure** se aap aik function ke andar cheezen yaad rakh sakte hain.
- Jaise upar example mein, `counter1` aur `counter2` dono alag alag counters hain, jo apni value yaad rakhte hain aur increment karte hain.

Yeh useful hota hai jab aapko data ko secure rakhna ho ya phir functions mein kuch state yaad rakhni ho.

# Template Literals
**Template literals** ek feature hai jo JavaScript mein string handling ko asaan banata hai. Iska use karke aap strings ko directly embed kar sakte hain aur variables ko string ke andar include kar sakte hain bina concatenation ke.

### Template Literals Kya Hai?

Template literals ek special type ki strings hain jo backticks (`` ` ``) ke andar likhi jati hain. Inmein aap variables aur expressions ko `${}` ke andar directly insert kar sakte hain.

### Kyun Use Karte Hain?

1. **Readability**: Template literals se strings ko likhna aur padhna asaan hota hai, khas taur par jab aapko multiple lines ya variables ke sath strings create karni ho.

2. **Multi-line Strings**: Template literals ki madad se aap multi-line strings bina kisi special character ke likh sakte hain.

3. **Expression Evaluation**: Aap directly expressions ko string ke andar evaluate kar sakte hain, jo traditional string concatenation se zyada convenient hota hai.

### Example:

#### Traditional String Concatenation:

```javascript
const name = "Ali";
const age = 25;
const message = "Hi, my name is " + name + " and I am " + age + " years old.";
console.log(message);
```

#### Using Template Literals:

```javascript
const name = "Ali";
const age = 25;
const message = `Hi, my name is ${name} and I am ${age} years old.`;
console.log(message);
```

### Explanation:

1. **Traditional Concatenation**:
   - Aapko string ke sath variables ko concatenate karna padta hai `+` operator se. Yeh thoda cumbersome aur error-prone hota hai.

2. **Template Literals**:
   - Aap backticks (`` ` ``) ke andar string likhte hain aur `${}` ke andar variables ko directly embed kar dete hain. Yeh code ko zyada readable aur maintainable banata hai.

### Multi-line String Example:

#### Traditional Way:

```javascript
const message = "This is line 1.\n" +
                "This is line 2.\n" +
                "This is line 3.";
console.log(message);
```

#### Using Template Literals:

```javascript
const message = `This is line 1.
This is line 2.
This is line 3.`;
console.log(message);
```

Yeh example dikhata hai ke template literals se multi-line strings likhna kitna asaan aur clear hota hai.

# destructuring 
**Destructuring** ek programming technique hai jo JavaScript mein data ko easily extract karne aur variables ko assign karne mein madad karta hai. Yeh mainly objects aur arrays ke saath use hota hai.

### Destructuring Kya Hai?

Destructuring se aap ek object ya array se directly properties ya elements ko extract kar sakte hain aur unhe variables mein assign kar sakte hain. Yeh code ko concise aur readable banata hai.

### Types of Destructuring

1. **Array Destructuring**
2. **Object Destructuring**

### 1. Array Destructuring

Array destructuring se aap arrays ke elements ko directly variables mein assign kar sakte hain.

#### Example:

```javascript
const numbers = [1, 2, 3, 4];

// Traditional way
const first = numbers[0];
const second = numbers[1];

// Using array destructuring
const [first, second] = numbers;

console.log(first);  // Output: 1
console.log(second); // Output: 2
```

**Explanation**:
- Traditional way mein, aap index ke zariye elements ko access karte hain.
- Destructuring ke zariye, aap directly array se values ko variables mein assign kar sakte hain.

### 2. Object Destructuring

Object destructuring se aap objects ki properties ko directly variables mein extract kar sakte hain.

#### Example:

```javascript
const person = {
    name: "Ali",
    age: 25,
    city: "Karachi"
};

// Traditional way
const name = person.name;
const age = person.age;

// Using object destructuring
const { name, age } = person;

console.log(name); // Output: Ali
console.log(age);  // Output: 25
```

**Explanation**:
- Traditional way mein, aap object ki properties ko dot notation ke zariye access karte hain.
- Destructuring ke zariye, aap directly object ki properties ko variables mein assign kar sakte hain.

### Kyun Use Karte Hain?

1. **Code Readability**: Destructuring se code zyada readable aur clean hota hai, kyunke aap directly variables ko assign kar lete hain bina extra syntax ke.

2. **Ease of Use**: Complex objects aur arrays ke saath kaam karte waqt, destructuring se aap easily required data ko extract kar sakte hain.

3. **Function Parameters**: Destructuring ka use functions ke parameters mein bhi hota hai, jahan aap directly object ya array ke parts ko extract kar sakte hain.

#### Example with Function Parameters:

```javascript
function printPerson({ name, age }) {
    console.log(`Name: ${name}, Age: ${age}`);
}

const person = {
    name: "Ali",
    age: 25
};

printPerson(person); // Output: Name: Ali, Age: 25
```

**Explanation**:
- Function ke parameters mein destructuring use karke, aap object ki specific properties ko directly extract kar sakte hain, jo code ko concise aur easy to understand banata hai.

Destructuring ka use aapko code ko zyada readable aur manageable banane mein help karta hai, especially jab aap complex data structures ke saath kaam kar rahe hote hain.

# Default Parameter
**Default parameters** JavaScript mein ek feature hai jo functions ke parameters ko default values assign karne ki suvidha deta hai. Agar function ko koi value nahi di jati ya undefined value pass ki jati hai, to default value use hoti hai.

### Default Parameters Kya Hai?

Default parameters se aap function ke parameters ko default values assign kar sakte hain. Agar function call karte waqt koi parameter pass nahi hota, to default value automatically use hoti hai.

### Kyun Use Karte Hain?

1. **Error Handling**: Default parameters se aap ensure kar sakte hain ke function ka output predictable rahe, agar koi value pass nahi ki gayi ho.

2. **Optional Parameters**: Jab aapko function ke kuch parameters optional rakhne hote hain, default values se aap easily handle kar sakte hain.

3. **Code Simplicity**: Default parameters se code zyada simple aur readable hota hai, kyunke aapko extra checks karne ki zarurat nahi hoti.

### Example:

#### Without Default Parameters:

```javascript
function greet(name) {
    if (name === undefined) {
        name = "Guest";
    }
    console.log(`Hello, ${name}!`);
}

greet();         // Output: Hello, Guest!
greet("Ali");    // Output: Hello, Ali!
```

**Explanation**:
- Agar `name` parameter pass nahi kiya jata, to function ke andar manually check karna padta hai aur default value assign karni padti hai.

#### With Default Parameters:

```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet();         // Output: Hello, Guest!
greet("Ali");    // Output: Hello, Ali!
```

**Explanation**:
- Default parameter `name = "Guest"` se agar `name` parameter pass nahi kiya jata, to `"Guest"` value automatically use hoti hai.
- Code zyada clean aur readable hota hai kyunki aapko extra checks ki zarurat nahi hoti.

### Another Example with Multiple Parameters:

```javascript
function createProfile(name = "Unknown", age = 0, city = "Not Specified") {
    console.log(`Name: ${name}, Age: ${age}, City: ${city}`);
}

createProfile();                  // Output: Name: Unknown, Age: 0, City: Not Specified
createProfile("Ali");             // Output: Name: Ali, Age: 0, City: Not Specified
createProfile("Ali", 25);         // Output: Name: Ali, Age: 25, City: Not Specified
createProfile("Ali", 25, "Karachi"); // Output: Name: Ali, Age: 25, City: Karachi
```

**Explanation**:
- Yahan, `createProfile` function mein teen parameters hain, aur har ek parameter ko ek default value di gayi hai.
- Agar koi parameter pass nahi kiya jata, to default value automatically use hoti hai, jis se function ko use karna zyada flexible aur easy hota hai.

Default parameters ka use function calls ko handle karne mein flexibility aur convenience provide karta hai, aur aapko additional checks aur conditions likhne ki zarurat nahi padti.


# Spread And Rest Operater
**Rest** aur **Spread** operators dono JavaScript mein `...` (triple dots) ke form mein use hote hain, lekin inka use aur functionality alag hota hai.

### Rest Operator (`...`)
**Rest operator** ka use tab hota hai jab humein function mein multiple arguments ko ek array mein combine karna hota hai ya array/object ke kuch elements/properties ko extract karne ke baad baaki ke elements/properties ko ek nayi array/object mein store karna hota hai.

**Examples:**

1. **Function mein Rest Operator:**

   ```javascript
   function sum(...numbers) {
     return numbers.reduce((acc, num) => acc + num, 0);
   }

   console.log(sum(1, 2, 3, 4)); // Output: 10
   ```

   Is example mein, `...numbers` rest operator hai, jo function ko pass kiye gaye multiple arguments ko ek array `numbers` mein combine karta hai.

2. **Array Destructuring mein Rest Operator:**

   ```javascript
   const fruits = ['apple', 'banana', 'mango', 'orange'];

   const [first, ...remainingFruits] = fruits;

   console.log(first); // Output: apple
   console.log(remainingFruits); // Output: ['banana', 'mango', 'orange']
   ```

   Yahan, `...remainingFruits` baaki ke elements ko `remainingFruits` array mein collect karta hai.

### Spread Operator (`...`)
**Spread operator** ka use tab hota hai jab humein ek array ya object ko expand karna hota hai, yaani ki uske elements ya properties ko alag-alag karna hota hai. Ye generally arrays ya objects ko clone karne ya unhe merge karne ke liye use hota hai.

**Examples:**

1. **Array mein Spread Operator:**

   ```javascript
   const numbers = [1, 2, 3];
   const moreNumbers = [...numbers, 4, 5, 6];

   console.log(moreNumbers); // Output: [1, 2, 3, 4, 5, 6]
   ```

   Yahan, `...numbers` array ke elements ko alag-alag karta hai aur unhe `moreNumbers` array mein add karta hai.

2. **Object mein Spread Operator:**

   ```javascript
   const person = { name: 'John', age: 30 };
   const updatedPerson = { ...person, city: 'New York' };

   console.log(updatedPerson);
   // Output: { name: 'John', age: 30, city: 'New York' }
   ```

   Is example mein, `...person` object ke properties ko expand karta hai aur unhe `updatedPerson` object mein include karta hai.

### Rest aur Spread mein Fark
- **Rest Operator** values ko **combine** karta hai ek array ya object mein.
- **Spread Operator** values ko **expand** karta hai array ya object se.

**Example to Understand Both:**
```javascript
const numbers = [1, 2, 3, 4];

// Spread Operator: Expand the array
console.log(...numbers); // Output: 1 2 3 4

// Rest Operator: Combine the arguments into an array
function sum(...args) {
  return args.reduce((acc, num) => acc + num, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
```

Yahan `...numbers` spread operator ka use karke array ko expand karta hai, aur `...args` rest operator ka use karke function ke arguments ko combine karta hai.

### Conclusion
- **Rest Operator**: Combine karne ke liye (arguments ko ek array mein, array elements ko ek nayi array mein, ya object properties ko ek naye object mein).
- **Spread Operator**: Expand karne ke liye (array ya object ke elements/properties ko nikalne ya copy karne ke liye).

Dono `...` ka use karte hain, lekin context ke hisaab se inka behaviour alag hota hai.

# arrow function 
**Arrow functions** JavaScript mein ek concise (chhoti aur simple) syntax mein functions likhne ka tareeqa hai. Yeh `function` keyword ka ek chhota sa alternative hai aur inhe code ko cleaner aur readable banane ke liye use kiya jata hai.

### Arrow Function Syntax
Arrow function likhne ka basic syntax kuch is tarah hota hai:

```javascript
const functionName = (parameters) => {
  // function body
};
```

### Traditional Function vs Arrow Function
Pehle hum traditional function syntax dekhte hain:

**Traditional Function:**
```javascript
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // Output: 5
```

**Arrow Function:**
```javascript
const add = (a, b) => {
  return a + b;
};

console.log(add(2, 3)); // Output: 5
```

Yahan, arrow function (`=>`) use kiya gaya hai jo code ko chhota aur concise banata hai.

### Benefits of Arrow Functions

1. **Shorter Syntax**: Arrow functions mein `function` keyword nahi likhna padta, isse code concise hota hai.
   
2. **Implicit Return**: Agar arrow function ek hi statement return kar raha hai, toh aap `{}` (curly braces) aur `return` keyword ko bhi chhod sakte hain. 

   **Example:**
   ```javascript
   const multiply = (a, b) => a * b;

   console.log(multiply(2, 3)); // Output: 6
   ```

   Yahan `a * b` ka result automatically return hota hai, bina `return` keyword likhe.

3. **Lexical `this`**: Arrow functions apne surrounding context (lexical scope) se `this` inherit karte hain, jo ki traditional functions ke comparison mein easy hota hai jab humein `this` handle karna hota hai.

### Example with Lexical `this`
Traditional function aur arrow function ke beech `this` ko handle karne ka farq samajhte hain:

**Traditional Function:**
```javascript
function Person() {
  this.name = 'Alice';
  setTimeout(function() {
    console.log(this.name); // undefined, because `this` refers to the global object or undefined in strict mode
  }, 1000);
}

new Person();
```

**Arrow Function:**
```javascript
function Person() {
  this.name = 'Alice';
  setTimeout(() => {
    console.log(this.name); // Output: Alice, because arrow function inherits `this` from its lexical scope
  }, 1000);
}

new Person();
```

Yahan arrow function (`=>`) ka use karne se, `this` correctly refer karta hai `Person` object ko, kyunki arrow function apne surrounding context (yaha `Person` object) se `this` ko inherit karta hai.

### Conclusion
Arrow functions JavaScript mein functions likhne ka ek simple aur concise tareeqa hai. Yeh code ko cleaner banata hai aur `this` ko handle karna easy banata hai. Arrow functions ka use tab karna chahiye jab aapko ek simple function likhna ho, ya jab aapko `this` keyword se bachna ho jo traditional functions mein problematic ho sakta hai.

# Enhanced Object literals
**Enhanced Object Literals** JavaScript mein ek feature hai jo objects ko aur bhi concise aur expressive tarike se likhne ki suvidha deti hai. Is feature ke tehat, hum object properties aur methods ko zyada easily aur efficiently define kar sakte hain.

### Enhanced Object Literals ke Features

1. **Property Shorthand**: Agar aapke paas variable ka naam aur object property ka naam same hai, toh aapko alag se property assign karne ki zaroorat nahi hai. 

   **Example:**
   ```javascript
   const name = 'Alice';
   const age = 25;

   // Traditional way
   const person = {
     name: name,
     age: age
   };

   // Enhanced object literal way
   const person = {
     name,
     age
   };

   console.log(person); // Output: { name: 'Alice', age: 25 }
   ```

2. **Method Shorthand**: Object methods ko define karne ka simplified syntax. Aapko `function` keyword likhne ki zaroorat nahi hoti.

   **Example:**
   ```javascript
   // Traditional way
   const person = {
     greet: function() {
       console.log('Hello!');
     }
   };

   // Enhanced object literal way
   const person = {
     greet() {
       console.log('Hello!');
     }
   };

   person.greet(); // Output: Hello!
   ```

3. **Computed Property Names**: Agar aapko object property ka naam dynamically set karna ho, toh aap is feature ka use kar sakte hain. Ye property name ko calculate karne ki suvidha deta hai.

   **Example:**
   ```javascript
   const propName = 'age';

   const person = {
     name: 'Alice',
     [propName]: 25
   };

   console.log(person); // Output: { name: 'Alice', age: 25 }
   ```

   Yahan `[propName]` ka use karke, `age` property ko dynamically add kiya gaya hai `person` object mein.

### Benefits of Enhanced Object Literals

1. **Concise Syntax**: Enhanced object literals code ko chhota aur readable banate hain.
2. **Dynamic Property Names**: Computed property names ka use karke aap dynamic properties easily define kar sakte hain.
3. **Less Repetition**: Property shorthand aur method shorthand ke saath, aapko extra repetition avoid karne mein madad milti hai.

### Example Combining All Features

```javascript
const firstName = 'Alice';
const lastName = 'Smith';
const propKey = 'age';

const person = {
  firstName, // Property shorthand
  lastName,  // Property shorthand
  [propKey]: 30, // Computed property name
  greet() {  // Method shorthand
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}.`);
  }
};

console.log(person); 
// Output: { firstName: 'Alice', lastName: 'Smith', age: 30 }

person.greet(); 
// Output: Hello, my name is Alice Smith.
```

### Conclusion
**Enhanced object literals** JavaScript mein objects ko zyada concise aur efficient tarike se likhne ke liye use hote hain. Yeh features code ko cleaner banate hain aur dynamically properties define karna easy karte hain. Isliye, aapko complex objects banate waqt inhe use karna chahiye taaki aapka code readable aur maintainable rahe.

# Iterators & `for..of`:
   - **Iterators**: JavaScript mein, iterators ek special object hote hain jo sequence (jaise arrays, strings, etc.) ke elements ko one-by-one access karne ka method provide karte hain. Yeh `next()` method ke zariye agle element ko access karte hain, aur jab sequence khatam hota hai, to yeh `done: true` return karte hain.
   - **`for..of` Loop**: Yeh loop kisi iterable object (jaise arrays, strings, etc.) ke har element par iterate karta hai. Iska use iterators ko simplify karne ke liye hota hai.

   **Example**:

   ```javascript
   const array = [1, 2, 3, 4];

   for (const value of array) {
       console.log(value);  // Outputs: 1, 2, 3, 4
   }
   ```

   **Zaroorat**: `for..of` iterators ko handle karna asan banata hai, aur saath hi non-numeric keys (like in objects) ko handle karne mein madad karta hai.

# Generators:
   - **Generators**: Generators special functions hote hain jo execution ko pause aur resume kar sakte hain. Yeh `function*` syntax se declare kiye jate hain, aur `yield` keyword se execution ko pause kiya jata hai.

   **Example**:

   ```javascript
   function* myGenerator() {
       yield 1;
       yield 2;
       yield 3;
   }

   const gen = myGenerator();
   console.log(gen.next().value);  // 1
   console.log(gen.next().value);  // 2
   console.log(gen.next().value);  // 3
   ```

   **Zaroorat**: Generators asynchronous operations ko handle karne mein madadgar hote hain, jaise ke API requests ya animations.

# Modules:
   - **Modules**: JavaScript modules files ka separate code hoti hain jinko import/export ke zariye manage kiya jata hai. Yeh modular programming ko promote karte hain, jahan code ko multiple files mein divide kiya ja sakta hai.

   **Example**:

   ```javascript
   // myModule.js
   export const greeting = 'Hello, World!';

   // main.js
   import { greeting } from './myModule.js';
   console.log(greeting);  // 'Hello, World!'
   ```

   **Zaroorat**: Modules large codebases ko manage karne mein asani dete hain, reusability aur maintainability ko improve karte hain.

# Map:
   - **Map**: JavaScript mein `Map` ek collection hota hai jismein key-value pairs store hote hain. Yeh object se different hota hai kyunki ismein keys kisi bhi data type ki ho sakti hain.

   **Example**:

   ```javascript
   const map = new Map();
   map.set('key1', 'value1');
   map.set(1, 'value2');

   console.log(map.get('key1'));  // 'value1'
   console.log(map.get(1));  // 'value2'
   ```

   **Zaroorat**: `Map` objects ke muqablay mein efficient hota hai jab keys non-string type ki hoti hain.

# Array Methods:
   - **Array Methods**: JavaScript mein arrays ke saath operations perform karne ke liye bohot saare built-in methods hote hain, jaise `map()`, `filter()`, `reduce()`, etc.

   **Example**:

   ```javascript
   const numbers = [1, 2, 3, 4];

   const doubled = numbers.map(num => num * 2);
   console.log(doubled);  // [2, 4, 6, 8]
   ```

   **Zaroorat**: Array methods code ko concise aur readable banate hain aur array operations ko simplify karte hain.

# Higher-Order Functions:
   - **Higher-Order Functions**: Yeh wo functions hote hain jo doosre functions ko as an argument accept karte hain ya unhe return karte hain.

   **Example**:

   ```javascript
   function higherOrder(fn) {
       return function(x) {
           return fn(x) + 1;
       };
   }

   function addTwo(x) {
       return x + 2;
   }

   const resultFn = higherOrder(addTwo);
   console.log(resultFn(3));  // 6
   ```

   **Zaroorat**: Yeh code reusability ko badhate hain aur functional programming mein commonly use hote hain.

# Callback:
   - **Callback**: Callback ek function hota hai jo doosre function ko argument ke taur par diya jata hai aur execution ke baad call kiya jata hai.

   **Example**:

   ```javascript
   function fetchData(callback) {
       setTimeout(() => {
           callback('Data received');
       }, 1000);
   }

   fetchData(message => {
       console.log(message);  // 'Data received'
   });
   ```

   **Zaroorat**: Callback functions asynchronous operations ko handle karne mein use hote hain.

# Promises:
   - **Promises**: Promises JavaScript mein asynchronous operations ko handle karne ka modern tareeqa hai. Yeh pending, fulfilled, aur rejected states mein hote hain.

   **Example**:

   ```javascript
   const promise = new Promise((resolve, reject) => {
       setTimeout(() => {
           resolve('Promise fulfilled');
       }, 1000);
   });

   promise.then(result => {
       console.log(result);  // 'Promise fulfilled'
   });
   ```

   **Zaroorat**: Promises asynchronous code ko handle karne ke liye cleaner aur more readable way provide karte hain.

# Exponentiation Operator (`**`):
   - **Exponentiation Operator**: JavaScript mein exponentiation operator (`**`) power calculation ke liye use hota hai.

   **Example**:

   ```javascript
   console.log(2 ** 3);  // 8
   ```

   **Zaroorat**: Yeh operator power calculation ko asan aur intuitive banata hai.

### 10. **Classes:**
   - **Classes**: JavaScript mein classes object-oriented programming ko implement karne ke liye use hoti hain. Yeh syntax sugar hain, jo prototype-based inheritance ko simplify karti hain.

   **Example**:

   ```javascript
   class Person {
       constructor(name) {
           this.name = name;
       }

       greet() {
           console.log(`Hello, ${this.name}`);
       }
   }

   const person = new Person('Alice');
   person.greet();  // 'Hello, Alice'
   ```

   **Zaroorat**: Classes code ko organize karne mein madad karte hain aur object-oriented approach ko promote karte hain.

# Ternary Operator:
   - **Ternary Operator**: Yeh ek shorthand if-else statement hota hai jo condition ko check karta hai aur uske mutabiq value return karta hai.

   **Example**:

   ```javascript
   const age = 18;
   const canVote = age >= 18 ? 'Yes' : 'No';
   console.log(canVote);  // 'Yes'
   ```

   **Zaroorat**: Ternary operator code ko concise aur readable banata hai.

# **Optional Chaining (`?.`):
   - **Optional Chaining**: Yeh operator nested objects ke properties ko safely access karne ke liye use hota hai. Agar property exist nahi karti to yeh `undefined` return karta hai bajaye error throw karne ke.

   **Example**:

   ```javascript
   const user = {
       profile: {
           name: 'Alice',
       },
   };

   console.log(user.profile?.name);  // 'Alice'
   console.log(user.profile?.age);  // undefined
   ```

   **Zaroorat**: Optional chaining deep nested objects mein properties access karte waqt errors se bachata hai.
