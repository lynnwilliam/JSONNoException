This is based off the JSON Java Branch json.org 2002.
 Copyright (c) 2002 JSON.org

 Permission is hereby granted, free of charge, to any person obtaining a copy
 of this software and associated documentation files (the "Software"), to deal
 in the Software without restriction, including without limitation the rights
 to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 copies of the Software, and to permit persons to whom the Software is
 furnished to do so, subject to the following conditions:

 The above copyright notice and this permission notice shall be included in all
 copies or substantial portions of the Software.

 The Software shall be used for Good, not Evil.

 THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 SOFTWARE.


# Description
This project is a Java library for dealing with JSON Objects.
Its different because!

## 1. you can now parse JSON Objects without needing to handle exceptions! 
    Most JSON string data is already normally validated before being put into the JSONObjects, which makes using Exceptions slow!

This won't throw exceptions since the JSON string is already validated probably by the client or the data-source that created it !
     JSONObject car = new JSONObject("{car}"); 

## 2. You can recursively search a JSON Object or JSON Array, for an object that matches 'name'. 
It will search the entire object recursively and return the first matching key name object. 

This is great for when web services change the location of the object, when all you want is the object and its location does not matter!

      JSONObject jsonA = "{"car":{"engine":{"sproket":"15"}}}";
      JSONObject jsonB = "{"car":{"engine": {"gears":{"sproket":"15"}}  }}";
      In this case we only want the "sproket" object and don't care about its position in the JSON map.
      Object sproketA = jsonA.getJSONObjectRecursive("sproket");
      Object sproketB = jsonB.getJSONObjectRecursive("sproket");
       objects sproketA and sproketB have the same data!  no need to change your business logic!

## 3. Use JSON for counting!!!!

   Sometimes we want to count objects, well now its easy
   JSONObject beanCounter = new JSONObject();
   beanCounter.increment("beanCounter");
   beanCounter.increment("beanCounter");
   beanCounter.increment("beanCounter");
   int beansCount =  beanCounter.getInt("beanCounter"); //will return 3 !!!

   JSONObject signoutCounter = new JSONObject();
   signoutCounter.decrement("signinAttempt");
   signoutCounter.decrement("signinAttempt");
   signoutCounter.decrement("signinAttempt");
   int signinAttempt =  signoutCounter.getInt("signinAttempt"); //will return -3 !!!
