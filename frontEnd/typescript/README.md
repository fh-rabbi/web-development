## 📜 Typescript Notes:

---
## 🔹 Index Of Contents:

1.  Environment setup:
    * **installation**
    * **configuration**
    * **convert js project to ts**
2.  Data Types - built-in:
    * `number, string, boolean, void, undefined, null`
3.  Data Types - user-defined:
    *  `Union type`
    *  `Array type`
    *  `Tuple type`
    *  `Enum type`
    *  `Any type`
    *  `Object type`
    *  `Custom type`
4. Class:
    * `Syntax`
    * `Inheritance`
    * `Abstract class`
    * `Encapsulation and access modifiers`
5. Interface
6. Generic
7. Module- export, import
8. DOM Manipulation

---

### 💠 Environment setup:

🔸 **installation:**
```
npm intsall typescript --save-dev (local)
npm install -g typescript (global)
```

🔸 **configuration:**
```
tsc --init
**Then modify rootDir and outDir**
```

🔸 **convert js project to ts:**
```
tsc main.ts
tsc -w main.ts
tsc -w
```

### 💠 Data Types - built-in:
```ts
// string TYPE EXAMPLE
let userName: string;
let id: number;
let isLoggedIn: boolean;
let a: null;
let b : undefined;

function display(): void {
  console.log("Hi I am display");
}
display();
```

### 💠 Data Types - user-defined:

🔸 Union Type: `more than one type for variable or function parameter`
```ts
let userId: string | number;
userId = 101; // no error
userId = "101"; // no error
userId = true; // error

function userIdDataType(userId: string | number) {
  console.log(typeof userId);
}
userIdDataType("123"); // no error
userIdDataType(123); // no error
userIdDataType(true); // error
```

🔸 Array Type:
```ts
let info1 = ['smith','david'];
let info2: string[];
info2 = ['john','doe'];
let info3: number[];
info3 = [1,2,3,4];

let info4 : (string|number)[];
let info4 : Array<string>;
```

🔸 Tuple type:
```ts
let users: [number, String];
users = [101, "anis"];

console.log(users);
console.log(users[0]);
console.log(users[1]);

users.push(102, "sakib");
console.log(users);
```

🔸Enum type:
```ts
// enum example
// helps us to store constants

// numeric enum
enum UserRequest {
  ReadData,
  // ReadData = 2,
  SaveData,
  UpdateData,
}

console.log(UserRequest);
console.log(UserRequest.ReadData);
console.log(UserRequest.SaveData);

// string enum
enum UserRequest {
  ReadData = "READ_DATA",
  // ReadData = 2,
  SaveData = "SAVE_DATA",
  UpdateData = "UPDATE_DATA",
}

console.log(UserRequest);
console.log(UserRequest.ReadData);
console.log(UserRequest.SaveData);
console.log(UserRequest["UpdateData"]);

// Heterogeneous enum
  enum User {
  id = 101,
  name = "anisul",
  }
```

🔸 Any type:
```ts
let data: any;
data = 'Sakib';
data = 123;
data = true;
data = null;
data = ['apple','orange'];
data = {
  name : 'smith',
  age : 20,
  city : 'US'
}
```

🔸 Object type:
```ts
let names: object;
names = { name1: "anis" };
console.log(names);

let users: object[];
users = [];

let user1: { userName: string, userId: number };
user1 = { userName: "anis", userId: 101 };
users.push(user1);

let user2: { userName: string, userId: number };
user2 = { userName: "rabu", userId: 102 };

users.push(user2);

for (const key in users) {
  console.log(users[key]["userName"]);
}
```

🔸 Custom type:
```ts
type User = { userName: string, userId: number };

let users: User[];
users = [];

let user1: User;
user1 = { userName: "anis", userId: 101 };
users.push(user1);

let user2: User;
user2 = { userName: "rabu", userId: 102 };
users.push(user2);

let user3: User;
user3 = { userName: "lucky", userId: 103 };
users.push(user3);

// console.log(users);

type RequestType = "GET" | "POST";
let getRequest: RequestType;
getRequest = "GET";

function requestHandler(requestType: RequestType) {
  console.log(requestType);
}
requestHandler("GET");
```

### 💠 Class:
🔸 Syntax:
```ts
class User {
  // properties, methods, constructor
  userName: string;
  age: number;

  constructor(userName: string, age: number) {
    this.userName = userName;
    this.age = age;
  }

  display(): void {
    console.log(`username: ${this.userName}, age: ${this.age}`);
  }
}

let user1 = new User("Anisul Islam", 25);
user1.display();

let user2 = new User("Rabeya Islam", 31);
user2.display();
```

🔸 Inheritance:
```ts
// Class inheritance:
class persons1 {
  name: string;
  age: number;
  constructor(name:string,age:number){
    this.name = name;
    this.age = age;
  }
}

let personA = new persons1('smith',20);
console.log(personA);

// Inheritance:
class persons2 extends persons1 {
  city: string;
  constructor(name:string,age:number,city:string){
    super(name,age);
    this.city = city;
  }
}

let personB = new persons2('David',22,'US');
console.log(personB);

```

🔸 Abstract class:
1. **abstraction helps us to hide the implementation of something**
2. **class declared with abstract keyword**
3. **object can not be created from abstract class**
4. **if a class extends abstract class; it must inherit all the abstract methods**

```ts
abstract class User {
  userName: string;
  age: number;

  constructor(userName: string, age: number) {
    this.userName = userName;
    this.age = age;
  }

  abstract display(): void;
}

class Student extends User {
  studentId: number;

  constructor(userName: string, age: number, studentId: number) {
    super(userName, age);
    this.studentId = studentId;
  }
  display(): void {
    console.log(
      `username: ${this.userName}, age: ${this.age}, id: ${this.studentId}`
    );
  }
}

let student1 = new Student("keya", 31, 1302020015);
student1.display();
```

🔸 Encapsulation and access modifiers:

* **Encapsulation helps us to manage the visibility of class members.**
* **Access modifiers:** `public, private, protected, readonly`

```ts
class User {
    readonly userName: string;
    public age: number;

    constructor(userName: string, age: number) {
      this.userName = userName;
      this.age = age;
    }

    display(): void {
      console.log(`username: ${this.userName}, age: ${this.age}`);
    }
  }

  class Student extends User {
    private studentId: number;

    constructor(userName: string, age: number, studentId: number) {
      super(userName, age);
      this.studentId = studentId;
    }
    display(): void {
      console.log(
        `username: ${this.userName}, age: ${this.age}, id: ${this.studentId}`
      );
    }

    setStudentId(studentId: number): void {
      this.studentId = studentId;
    }

    getStudentId(): number {
      return this.studentId;
    }
  }

  let student1 = new Student("keya", 31, 1302020015);
  student1.setStudentId(1302020017);
  console.log(student1.getStudentId());
  // student1.display();

  let user1 = new User("robi", 23);
  console.log(user1.userName);
  // user1.display();
```

### 💠 Interface:
```ts

```

### 💠 Generic:
```ts

```

### 💠 Module- export, import:
```ts
// module.js
// _____________________
export let userName: string = "David786";
export function demo():void{
  console.log('Okey');
}

// app.js
// _____________________
import {userName as uName,demo} from './module.js'
```

### 💠 DOM Manipulation:
```ts
const form = document.querySelector(".user-form") as HTMLFormElement;
console.log(form);

const userNameInput = document.querySelector("#username") as HTMLInputElement;
console.log(userNameInput);

const userEmailInput = document.querySelector("#useremail") as HTMLInputElement;
console.log(userEmailInput);

const userCountrySelect = document.querySelector(
  "#country"
) as HTMLSelectElement;
console.log(userCountrySelect);

const userFeedback = document.querySelector("#feedback") as HTMLTextAreaElement;
console.log(userFeedback);

form.addEventListener("submit", (e: Event) => {
  e.preventDefault();
  let userData = {
    userName: userNameInput.value,
    userEmail: userEmailInput.value,
    userCountry: userCountrySelect.value,
    userFeedback: userFeedback.value,
  };
  console.log(userData);
});
```
