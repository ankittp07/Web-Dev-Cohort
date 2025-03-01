# Topics of the Class

## Data Structure in JS

- The way from which we store the data in the memory is Data Structure.
- It varies and depends upon the upon the type of data.

## Types of Data Structure

Primarly there are two types of Data Structures :-

### Primitive -

- The type of data structure which is support out of box or are in built in the language(JS)
- Array --> In Array we store data in sequencial manner
- Objects --> Object is kind of container in which we store data in key-vaule pairs and for Objects we use "{}"

```javascript
let remote = {
    name: "Smart remote",
    price: 245,
    dimension: {
        length: 2,
        height: 3,
        width: 5
    }
    isChargable: false,
    specification: ["black", "long range", "Made in India"]
    turnOff: function(){
        return "Off"
    }
}
console.log(remote);

console.log(remote.price);
// output - 245

console.log(remote.turnOff());
// output - Off

console.log(remote.dimension.height);
// output - 3

console.log(remote.specification[2]);
// output - Made in India
```

### Non-Primitive -

- The type of data structure which we built/design by ourselves or not in built in JS
- Stack, Link List and Graph

## Memory

Two types of memory:-

### Stack Memory -

- Primitive datatypes are stored in it.
- Stack memory is not dynamically expandable which mean we can't add or remove from it afterwards.
- here if we declare a variable in which we allocate another variable as its value then we will be allocated the reference of copy of the original value(variable) in memory and whatever change we commit will be in that copy only and will not imply on the original variable

#### Example -

```javascript
let myName = "ankit";
let anotherName = myName;

console.log(myName);
// ankit
console.log(anotherName);
// ankit

anotherName = "sachin";

console.log(myName);
// ankit
console.log(anotherName);
// sachin
```

so in above example if we change value of anotherName variable myName value dont change because while declaring anotherName variable value to myName we allocated the reference of copy of value of myName in memory so the change will be in copy value not in original value of myName

### Heap Memory -

- Non-primitive datatypes are stored in it
- Heap memory is dynamically expandable which means we can add or remove things in it afterward (in object and array we add and remove values)
- here if we declare a variable in which we allocate another variable as its value we allocated the reference of original value in the memory location and the change we commit in new variable will be also effect the orignial variable value

#### Example -

```javascript
let userOne = {
  email: "ankit@google.com",
  city: "sikar",
};

console.log(userOne);
// { email: 'ankit@google.com', city: 'sikar' }

let userTwo = userOne;

console.log(userTwo);
// { email: 'ankit@google.com', city: 'sikar' }

userTwo.email = "jk@google.com";
// in object we access by '.'

console.log(userOne);
// { email: 'jk@google.com', city: 'sikar' }
console.log(userTwo);
// { email: 'jk@google.com', city: 'sikar' }
```

so here when we change value of userTwo variable userOne value also change because while declaring userTwo variable value to userOne we allocated the reference original value of userOne in memory so the change will be in original value of userOne also

#### Example -

For instance we have a variable "A" in which we have a object. That object will be stored in heap memory and we will get the address of that data location in memory. That address will be placed in the place of the value(object) in that variable. Now it will be stored in the stack memory. It is called "Pointer" because in that variable in place of object(value) we get the address of that object which is pointing at that data/value(object) in heap memory. Which means pointer of non-primitive datatypes is stored in stack memory. Now we have new variable "B" which value is variable "A" so in stack memory we have address in place of value so that address will assigned as the value of variable "B". If the we made in any change in "B" that change will also apply on "A" because the address is changing.

### Garbage Collector -

- Javascript has Garbage Collector
- Which means once the variable is out of scope implies it work is done then it get cleared/deleted from stack memory. But in case of non-primitive datatypes we have pointers(address of the memory/value in the variable as its value). So in the stack memory the pointer get cleared but the memory of the data which was allocated in heap memory is still there. If the language has Garbage collector then that memory will also cleared automatically since it have no pointer left. But if there is no Garbage collector we have to clear that memory manually.

### Memory Leak -

- For instance, as we see in one of above example we have two objects "A" and "B". They stored in stack memory as pointer while pointing to the same data(memory) because we assign "A" as value of "B".
  Now variable "B" is out of scope and the pointer get cleared from stack memory and which means we also cleared the allocated memory from heap memory (we were doing it manually in C++). The data or that allocated place in the memory is cleared and maybe that part of memory is allocated to some other data. But the pointer variable "A" is still in stack memory with the address of that data in memory pointing to that data. So it will be a mismatch when it will access other data that was allocated afterwards and maybe result in error or something. It is called memory leak.
- In Javascript we don't have to worry about it since it is taken care automatically by garbage collector.

### Shallow Copy (...) -

- Shallow copy allow to copy only the surficial values.
- In Shallow Copy it doesn't copy the value of nested objects as we can see in variable p4 and p5.

```javascript
let p1 = {
  fname: "Ankit",
  lname: "Punia",
};

// first way
let p2 = {
  fname: p1.fname,
  lname: p1.lname,
};

// second way - recommended and more effiecent
let p3 = {
  ...p1, // spread operator
};

// inner objects
let p4 = {
  fname: "Joe",
  lname: "Roy",
  address: {
    house: 2,
    street: 5,
  },
};
let p5 = {
  ...p4,
};
```

- In both ways we will get the same value as of p1 in our both variable p2 and p3 but if we make any change in p2 and p3 it will not effect the value of p1(original/primary variable) because all these variables have different memory locations in heap memory unlike if we directly give p1 reference in value of variable. Because here we are copying the values of p1 but not getting the reference of p1.
- But spread doesn't work in inner objects(object or array). In p5 if i change fname or lname, it will not the values of p4, but in p5 if i change the values of address then it will also effect the address values in p4 because here it is a object and we are not copying the values but getting the reference of it.

### Deep Copy -

- In deep copy we can copy values of nested objects instead of getting reference of them. So we can make change without affecting other but can still get same values of other objects.

```javascript
// first method
let p5 = {
  ...p4,
  address: {
    ...p4.address,
  },
};

// second method - recommended and more efficient

let p4KaString = JSON.stringify(p4);
// convert p4 into string

let p5 = JSON.parse(p4KaString);
// convert back p4 into object
```

- In second method we first convert p4 into string(primitive) because string always get copyied instead of getting reference and afterwards we convert it back into object(non-primitive) in p5. This way we will copy the values instead of getting the reference of it.
- The shape of both variables is same but address is different. So any change in p5 will not effect p4.

#### Converting the Object into String is called Serialization. Converting back the String into the Object is called Deserialization.

- We can share over internet or anything the serialized version of object. And the receiver can deserialize it and can get the object back. Since we can't share directly the object because we have the pointer which is pointing the memory location of data in our local memory which is different (memory) for the receiver.
