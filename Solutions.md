##Concat and Join

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

##Sum of Positive

You get an array of numbers, return the sum of all of the positives ones.

Example [1,-4,7,12] => 1 + 7 + 12 = 20


Solution:

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

Best Solution:
function positiveSum(arr) {
   return arr.reduce((a,b)=> a + (b > 0 ? b : 0),0);
}
-------------------------------------------------------------------------------------------------------------

##Mathematical Operations

Your task is to create a function - basicOp().

The function should take three arguments - operation(string), value1(integer), value2(integer). The function should return result of integers after applying chosen operation.

Solution:
function basicOp(o, a, b) {
  return eval(a+o+b);
}

----------------------------------------------------------------------------------------------------------

##Name on billboard - 8kyu

You can print your name on a billboard ad. Find out how much it will cost you. Each letter is $30 but could change. You can not use multiplier * operator. If your name would be Jeong-Ho Aristotelis, ad would cost £600. 20 leters * 30 = 600 (Space counts as a letter).

Solution:
function billboard(name, price = 30){
	var count = 0;
  var splitUp = name.split('');
  for(var i = 0; i < splitUp.length; i++) {
  	count += price;
  }
  return count;
}

Best of All Solutions:
const billboard = (name, price = 30) => +(name.length / (1 / price))

------------------------------------------------------------------------------------------------------------
##Fix the function before the garden dies! - 8kyu

You have an award-winning garden and everyday the plants need exactly 40mm of water. Create a great piece of JavaScript to calculate the amount of water your plants will need when you have taken into consideration the amount of rain water that is forecast for the day.

Solution:
function rainAmount(mm){
    if (mm < 40) {
         return "You need to give your plant " + (40 - mm) + "mm of water"
    }
    else if (mm > 40 || mm === 40)  {
         return "Your plant has had more than enough water for today!"
    }
}
