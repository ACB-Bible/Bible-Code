<h3 align="center">A-F Javascript Functions</h3>

---

##### Table of Contents:{#toc}

[Declare Function with optional arguments](#dfwog)


---
Use This Code With Caution:

[Declare Function with optional arguments](#toc){#dfwog}
```javascript
function myFunction(param1 = 'default value 1',
param2 = 'default value 2',
param3 = 'default value 3',
param4 = 'default value 4',
param5 = 'default value 5') {
  console.log(param1, param2, param3, param4, param5);
};
myFunction();
// Output: value1 value2 value3 value4 value5
```