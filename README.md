# JAVASCRIPT-Promises

##### EXAMPLE

var promiseCount = 0; <br>

function testPromise() { <br>
>>var thisPromiseCount = ++promiseCount; <br>
>>>console.log(thsiPromiseCount + ': Started =Sync code started'); <br>
  
>var p1 = new Promise(function(resolve, reject){ <br>
>>>>console.log(thisPromiseCount + ': Promise started = Ascync code started'); <br>
    // This is only and example to create asynchronism <br>
>>>>>>setTimeout(function() { <br>
>>>>>>resolve(thisPromiseCount);  <br>
>>>>}, Math.random() * 2000 + 1000); <br>
>}); <br>
  
>p1.then(function(val){ <br>
>>>>>console.log(val + ': Promise fullfilled = Async code terminated"'); <br>
>>}).catch(function(reason){ <br>
>>>>>console.log('Handle rejected promise ('+ reason+') here.'); <br>
>>}) <br>
>>>>>console.log(thisPromiseCount + ' : Promise made = Sync code terminated'); <br>
>} <br>

testPromise(); <br>
