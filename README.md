# Javascript Total

### Const, let and var

##### Prefer to use const, this adds less complexity to the code, and constants have a single purpose.

**let** userName = Pedro
<p style='color:red'>
    let userName = 25 
</p>

**const** userName = Pedro
<p style='color:green'>
    const userName = 25 
</p>


### Arrow function
  
| Conventional | Arrow functions |
| -------- | -------- | 
| function () { }     | () => { }     | 
| function () { return { } }     | () => ( { } )   
| function double(num) { return num * 2 }     | num  => num * 2   
| function sum(num1, num2) { return num1 + num2 }     | (num1, num2) => { return num1 + num2}   
