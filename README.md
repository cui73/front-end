# Front-end Interview 算法

1. Flatten Array

```text
  function flatten(arr) {
    return arr.reduce(function (flat, toFlatten) {
      return flat.concat(Array.isArray(toFlatten) ? flatten(toFlatten) : toFlatten);
   }, []);
  }
flatten([[[1, [1.1]], 2, 3], [4, 5]]);
```

2. flatten objects

```text
  var flattenObject = function(ob) {
    var toReturn = {};
  
    for (var i in ob) {
      if (!ob.hasOwnProperty(i)) continue;
    
      if ((typeof ob[i]) == 'object') {
        var flatObject = flattenObject(ob[i]);
        for (var x in flatObject) {
          if (!flatObject.hasOwnProperty(x)) continue;
        
          toReturn[i + '.' + x] = flatObject[x];
        }
      } else {
         toReturn[i] = ob[i];
      }
   }
   return toReturn;
};
```



