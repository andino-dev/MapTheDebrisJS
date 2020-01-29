# MapTheDebrisJS
Return a new array that transforms the elements' average altitude into their orbital periods (in seconds).  The array will contain objects in the format {name: 'name', avgAlt: avgAlt}.  You can read about orbital periods on Wikipedia.  The values should be rounded to the nearest whole number. The body being orbited is Earth.  The radius of the earth is 6367.4447 kilometers, and the GM value of earth is 398600.4418 km3s-2.
``` javascript

function orbitalPeriod(arr) {
  var newArray = [];
  var a = 2*Math.PI
  var GM = 398600.4418;
  var earthRadius = 6367.4447;
  var orbPeriod= function(num){
    var b = Math.pow(earthRadius + num.avgAlt,3)
    var c = Math.sqrt(b/GM)
    var orbPeriod = Math.round(a*c);
    delete num.avgAlt;
    num.orbitalPeriod = orbPeriod;
    return num;
    console.log(num)
  }
  for(var i = 0;i<arr.length;i++){
newArray.push(orbPeriod(arr[i]))
  }
  return newArray;
}

console.log(orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]));

```
