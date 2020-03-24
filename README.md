"# codewars-solutions-of-4-5-levels" 
"# codewars-solutions-of-4-5-levels" 

My solutions
* [x] [Strings Mix](https://www.codewars.com/kata/5629db57620258aa9d000014)
```javascript
function mix(s1, s2) {
  s1 = s1.replace(/[^a-z]/g,'');
  s2 = s2.replace(/[^a-z]/g,'');
  let obj1 = {};
  let obj2 ={};
  for (let i of s1){
    if (obj1[i]) obj1[i]++;
    else obj1[i] = 1;
  }
 for (let i of s2){
    if (obj2[i]) obj2[i]++;
    else obj2[i] = 1;
  }
  for (let i in obj1){
    if (obj1[i] < 2) delete obj1[i];
  }
  for (let i in obj2){
    if (obj2[i] < 2) delete obj2[i];
  }
  let res = '';
  for (let i in obj1){
    if (obj2.hasOwnProperty(i)) {
      if (obj2[i] > obj1[i]) {
        res = res + '2:' + i.repeat(obj2[i])+'/';
      } else if (obj2[i] < obj1[i]){
        res = res + '1:' + i.repeat(obj1[i])+'/';
      } else res = res + '=:' + i.repeat(obj1[i]) +'/'
    } else res = res + '1:' + i.repeat(obj1[i])+ '/'
  }
  for (let i in obj2){
    if (!obj1.hasOwnProperty(i)) {
      res = res + '2:' + i.repeat(obj2[i]) + '/';
    }
  }
  res = res.slice(0,-1);
let arr = res.split('/');
let arr6 = arr.filter(el=>el.length === 8).sort();
let arr5 = arr.filter(el=>el.length === 7).sort();
let arr4 = arr.filter(el=>el.length === 6).sort(); 
let arr3 = arr.filter(el=>el.length === 5).sort(); 
let arr2 = arr.filter(el=>el.length === 4).sort();   
 return arr6.concat(arr5,arr4, arr3, arr2).join('/');
  
}
```