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
