# Description: Javascript Exercise 1

### Description
1. Write a function which iterates over an object and prints all the properties including the nested.

        function printValues(obj) {
           for (var key in obj) {
               if (typeof obj[key] === "object") {
                   printValues(obj[key]);
               } else {
                   console.log(obj[key]);
               }
           }
        }
        var obj = {
           'object_1': {
               1: 'Property 1',
               2: 'Property 2',
               'object_2': {
                   3: 'Property 3',
                   4: 'Property 4',
                   5: 'Property 5'
               }
           },
           'object_3': {
                   6: 'Property 6'
           }
        };
        printValues(obj);

1. Write a function to create an object from an array of key value pairs.
   > sample input: `[["key1", "val1"],["key2", "val2"]]`
   
        function array_to_obj(array) {
         const mp = new Map(array);
         const obj = Object.fromEntries(mp);
         console.log(obj)
        };
        const sample_input = [["license", "GPL"],["version", "1.0"]];
        array_to_obj(sample_input);
        
1. Write a function to extend a given object and adds new properties from array of key value pairs. 
    > sample input: `{"license": "GPL", "version":"1.0"}, [["key1", "val1"],["version", "val2"]]`

         var sample_input = {"license": "GPL", "version":"1.0"}
         var new_sample_input = {};
         new_sample_input.key = "key1" ;
         new_sample_input.value = "val1";
         new_sample_input.key = "version";
         new_sample_input.value = "val2";
        
         function extend(obj, src) {
             for (var key in src) {
                 if (src.hasOwnProperty(key)) obj[key] = src[key];
             }
             return obj;
         }
         var sample_input = extend(sample_input, new_sample_input);
        
         console.log(sample_input);
         
1.  Write a function which takes number n as input and returns nth Fibonacci number. Implement it in following 2 ways.
    - using recursion
            
            var fibonacci_series_recursive = function(n) {
                if(n <= 2) {
                    return 1;
                } else {
                    return this.fibonacci_series_recursive(n - 1) + this.fibonacci_series_recursive(n - 2);
                }
            };
             console.log(fibonacci_series_recursive(8));
    
    - without using recursion
             
             var fibonacci_series = function(n) {
                 var a = 0, b = 1, f = 1;
                 for(var i = 2; i <= n; i++) {
                     f = a + b;
                     a = b;
                     b = f;
                 }
                 return f;
             };
             console.log(fibonacci_series(8));
             
1. Given an array of numbers, create an array of squares of them using `map`.

        const array = [2, 5, 9, 12, 15];
            let squares = array.map((i) => i * i);
        console.log(squares);
        console.log(array);
        
1. Given an array of numbers, create a new array with prime numbers using `filter`.

        var numArray = [2, 3, 4, 5, 6, 7, 8, 9, 10]
        
        numArray = numArray.filter((number) => {
          for (var i = 2; i <= Math.sqrt(number); i++) {
            if (number % i === 0) return false;
          }
          return true;
        });
        
        console.log(numArray);

1. Implement stack and queue using javascript arrays.

        function Stack() {
          this.dataStore = [];
          this.top = 0;
          this.push = push;
          this.pop = pop;
          this.peek = peek;
          this.clear = clear;
          this.length = length;
        }
        function push(element) {
          this.dataStore[this.top++] = element;
        }
        function peek() {
          return this.dataStore[this.top-1];
        }
        function pop() {
          return this.dataStore[--this.top];
        }
        function clear() {
          this.top = 0;
        }
        function length() {
          return this.top;
        }
        var stack = new Stack();
        stack.push(10);
        stack.push(20);
        stack.push(30);
        stack.push(40);
        stack.push(50);
        console.log(stack.peek());
        console.log("Popped element is: " + stack.pop());
        console.log(stack.peek());
        
        
        
        
        
        
        function Queue() {
               this.elements = [];
        }
        Queue.prototype.enqueue = function (e) {
          this.elements.push(e);
        };
        Queue.prototype.dequeue = function () {
           return this.elements.shift();
        };
        Queue.prototype.isEmpty = function () {
           return this.elements.length == 0;
        };
        Queue.prototype.peek = function () {
           return !this.isEmpty() ? this.elements[0] : undefined;
        };
        Queue.prototype.length=function(){
        return this.elements.length;
        }
        var queue = new Queue();
        queue.isEmpty();
        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
        queue.enqueue(50);
        console.log(queue.peek());
        console.log(queue.dequeue());
        console.log(queue.peek());
        console.log(queue.length());

