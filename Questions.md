## 1. Can (a == 1 && a == 2 && a == 3) ever evaluate to true?
Ref: https://stackoverflow.com/questions/48270127/can-a-1-a-2-a-3-ever-evaluate-to-true

**Solution:**
```
const a = {
  i: 1,
  toString: function () {
    return a.i++;
  }
}

if(a == 1 && a == 2 && a == 3) {
  console.log('Hello World!');
}
```
**Explanation:**
The reason this works is due to the use of the loose equality operator. When using loose equality, if one of the operands is of a different type than the other, the engine will attempt to convert one to the other. In the case of an object on the left and a number on the right, it will attempt to convert the object to a number by first calling valueOf if it is callable, and failing that, it will call toString. I used toString in this case simply because it's what came to mind, valueOf would make more sense. If I instead returned a string from toString, the engine would have then attempted to convert the string to a number giving us the same end result, though with a slightly longer path.


## 2. Invoking a function without parentheses
Ref: https://stackoverflow.com/questions/35949554/invoking-a-function-without-parentheses

## 3. Using delete operator in array
Ref: https://stackoverflow.com/questions/500606/deleting-array-elements-in-javascript-delete-vs-splice

**Explanation:**
Delete will delete the object property, but will not reindex the array or update its length. This makes it appears as if it is undefined.
```javascript
var myArray = ['a', 'b', 'c', 'd'];
delete myArray[0];
console.log(myArray); // [empty, "b", "c", "d"] (Chrome Browser)
```

## 4. What will be the output
```javascript
greetings();
 var greetings = function(){
console.log("first greet");
};
greetings();
function greetings(){
console.log("second greet");
};
greetings();
```
**Output:** 
```
second greet
first greet
first greet
```

```javascript
(function () {
    try {
        throw new Error();
    } catch (x) {
        var x = 1, y = 2;
        console.log(x);
    }
    console.log(x);
    console.log(y);
})();
```
**Output:** 
```
1
undefined
2
```

**Input**
```javascript
let input = {
 user: {
  name: "John",
  tech: "Frontend",
  address: {
   home: {
    add_1: "home_dummy_add_1",
    add_2: "home_dummy_add_2",
   },
   office: {
    add_1: "off_dummy_add_1",
    add_2: "off_dummy_add_2",
   },
  },
 },
};
```
**Expected Output**
```javascript
{
  user_name: 'John'
  user_tech: 'frontend'
  user_address_home_add_1: 'home_dummy_add_1'
  user_address_home_add_2: 'home_dummy_add_2'
  user_address_office_add_1: 'off_dummy_add_1'
  user_address_office_add_2: 'off_dummy_add_2'
}
```
