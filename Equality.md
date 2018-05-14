# 1. Can (a == 1 && a == 2 && a == 3) ever evaluate to true?
# Ref: https://stackoverflow.com/questions/48270127/can-a-1-a-2-a-3-ever-evaluate-to-true

# Solution:
const a = {
  i: 1,
  toString: function () {
    return a.i++;
  }
}

if(a == 1 && a == 2 && a == 3) {
  console.log('Hello World!');
}
# Explanation:
The reason this works is due to the use of the loose equality operator. When using loose equality, if one of the operands is of a different type than the other, the engine will attempt to convert one to the other. In the case of an object on the left and a number on the right, it will attempt to convert the object to a number by first calling valueOf if it is callable, and failing that, it will call toString. I used toString in this case simply because it's what came to mind, valueOf would make more sense. If I instead returned a string from toString, the engine would have then attempted to convert the string to a number giving us the same end result, though with a slightly longer path.


# 2. Invoking a function without parentheses
# Ref: https://stackoverflow.com/questions/35949554/invoking-a-function-without-parentheses
