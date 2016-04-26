

//Fix the function before the garden dies! - 8kyu
//You have an award-winning garden and everyday the plants need exactly 40mm of water. Create a great piece of JavaScript to calculate the amount of water your plants will need when you have taken into consideration the amount of rain water that is forecast for the day.

//Solution:
function rainAmount(mm){
    if (mm < 40) {
         return "You need to give your plant " + (40 - mm) + "mm of water"
    }
    else if (mm > 40 || mm === 40)  {
         return "Your plant has had more than enough water for today!"
    }
}
