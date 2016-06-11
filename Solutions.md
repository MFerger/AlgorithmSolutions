##Round Robin
Imagine you have an array of 10 teams, and each team has a number:

```
[1,2,3,4,5,6,7,8,9,10]
```
Your goal is to write a function that takes an input array and returns an array of arrays of arrays.
For example, for an array input of `[1,2,3,4]` the result would be:

```
[
  [           // ---- round 1 -----
    [1, 4],   // 1 plays 4
    [3, 2],   // 3 plays 2
  ],
  [           // ---- round 2 -----
    [1, 3],   // 1 plays 3
    [2, 4],   // 2 plays 4
  ],
  [           // ---- round 3 -----
    [1, 2],   // 1 plays 2
    [4, 3],   // 4 plays 3
  ]
]
```
Solution:
```
function (input) {
  let split = input.length / 2;
  let schedule = [];
  let counter = 0;
  function roundRobin (array) {
    schedule[counter] = [];
    let firstHalf = array.slice(0, split);
    let secondHalf = array.slice(split, array.length).reverse();
    array.splice(1,0,array.pop());
    firstHalf.forEach(function(team, i){
      schedule[counter].push([team, secondHalf[i]])
    })
    counter++;
    array[1] !==2 ? roundRobin(array) : schedule;
  }
  roundRobin(input);
  return schedule;
}
```
---------------------------------------------------------------------------------------------

##Grading InDecline
A student is considered in decline if they have 3 grades lower than previous grades, even if there are some steady
grades in there.  Look for 3 "down" movements that are either a) separated by "even"s or b) consecutive.

For example:
```
[10, 10, 10, 9, 9, 8, 8, 8, 8, 7] // ["even", "even", "down", "even", "down", "even", "even", "even", "down"]
[10, 10, 10, 9, 9, 8, 8, 8, 8, 7] // in decline

[10, 10, 10, 11, 9, 8, 8, 8, 8, 7] // ["even", "even", "up", "even", "down", "even", "even", "even", "down"]
[10, 10, 10, 11, 9, 8, 8, 8, 8, 7] // not in decline
```
Solution:
```
function(grades) {
  var pushed = [];
  var count = 0;
  for (var i = 0; i < grades.length; i++) {
    if (i > 0) {
      if (grades[i] > grades[i - 1]) {
        pushed.push('up')
      } else if (grades[i] === grades[i - 1]) {
        pushed.push('even')
      } else {
        pushed.push('down')
      }
    }
  }
  if (pushed.length <= 1) {
    return false;
  }
  for (var i = 0; i < pushed.length; i++) {
     if (pushed[i] === 'down') {
          count++;
      } else if(pushed[i] === 'up'){
        count = 0;
      }
    }
    if (count >= 3) {
      return true;
    } else {
      return false;
    }
}
```
-----------------------------------------------------------------------------------------------

##Grading
You are given an array of grades.  You need to process this array, and return an array that describes whether each grade
was higher, lower or even to the previous grade.

So given the following array:
```
[6,3,5,4,3,4,4,5]
```
Your code would produce:
```
["down","up","down","down","up","even","up"]
```
Solution:
```
function(grades) {
  var pushed = [];
for (var i = 0; i < grades.length; i++) {
    if (i > 0) {
      if (grades[i] > grades[i - 1]) {
        pushed.push('up')
      } else if (grades[i] === grades[i - 1]) {
        pushed.push('even')
      } else {
        pushed.push('down')
      }
    }
  }
  return pushed;
}
```
--------------------------------------------------------------------------------------

##Concat and Join
```
function bigToSmall(arr){
  //coding here...
  var sortedArr = [];
  var str = "";
  arr.forEach(function(x){
   sortedArr = sortedArr.concat(x);
  })
  sortedArr.sort(function(a,b){
    return b - a;
  });
  var str = sortedArr.join(">");

  return str;
}
```
##Sum of Positive

You get an array of numbers, return the sum of all of the positives ones.

Example:
```
[1,-4,7,12] => 1 + 7 + 12 = 20
```

Solution:
```
function positiveSum(arr) {
  var sum = 0;
  var negs = 0;
  for(var i = 0; i < arr.length; i++){
  	if(arr[i] > 0) {
    sum += arr[i];
    } else {
    negs += arr[i];
    }
  }
  return sum;
}
```

Best Solution:
```
function positiveSum(arr) {
   return arr.reduce((a,b)=> a + (b > 0 ? b : 0),0);
}
```
-------------------------------------------------------------------------------------------------------------

##Mathematical Operations

Your task is to create a function - basicOp().

The function should take three arguments - operation(string), value1(integer), value2(integer). The function should return result of integers after applying chosen operation.

Solution:
```
function basicOp(o, a, b) {
  return eval(a+o+b);
}
```
----------------------------------------------------------------------------------------------------------

##Name on billboard - 8kyu

You can print your name on a billboard ad. Find out how much it will cost you. Each letter is $30 but could change. You can not use multiplier * operator. If your name would be Jeong-Ho Aristotelis, ad would cost £600. 20 leters * 30 = 600 (Space counts as a letter).

Solution:
```
function billboard(name, price = 30){
	var count = 0;
  var splitUp = name.split('');
  for(var i = 0; i < splitUp.length; i++) {
  	count += price;
  }
  return count;
}
```
Best of All Solutions:
```
const billboard = (name, price = 30) => +(name.length / (1 / price))
```

------------------------------------------------------------------------------------------------------------
##Fix the function before the garden dies! - 8kyu

You have an award-winning garden and everyday the plants need exactly 40mm of water. Create a great piece of JavaScript to calculate the amount of water your plants will need when you have taken into consideration the amount of rain water that is forecast for the day.

Solution:
```
function rainAmount(mm){
    if (mm < 40) {
         return "You need to give your plant " + (40 - mm) + "mm of water"
    }
    else if (mm > 40 || mm === 40)  {
         return "Your plant has had more than enough water for today!"
    }
}
```
