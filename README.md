CAUTION
=======
 - This project is in alpha state. You should not used it except for experimental purposes.
 - This project is only supported for Gradle build system (if you use an IDE, only Android Studio is supported).

vb-android-library-cache
========================

This android library provide a cache with 2 layers, one in RAM in top of one on local storage.
The particularity of this cache is to provide an expiry date for the cached object.

Setup
-----
 - Add to your repositories the following url :
 
   ```gradle
   maven {
       url 'https://github.com/vincentbrison/vb-maven/raw/master/release/'
   }
   ```
   and to your dependencies :
   
   ```gradle
     compile 'vb.android.library.cache.lib:vbcache:0.0.+@aar'
   ```
    The alpha releases will use 0.0.+, the beta releases 0.1.+, the stables releases 1.+.+.
 - If you want activate the log of this library :
 
  ```Java
   VBLibCacheLogUtils.enableLog();
  ```
 - You have to provide a Context to the cache. Please use the [application context] (http://developer.android.com/reference/android/content/Context.html#getApplicationContext())
 to avoid ugly memory leak : 
 
  ```Java
   VBLibCacheContextUtils.setContext(getApplicationContext());
  ```
  
 - You are good to go !
  
Put
---
 - You can only cache Serializable object.
 - You have to use a CacheWrapper object to cache an object. With the CacheWrapper you can set a expiry date to your object. If you set null as the expiry date, the object
 will remain in the cache until the end times.
 - Basic example :
 
 ```Java
 // Strings are serializable so they can be cached.
 CacheWrapper wrapper = new CacheWrapper("object10sec", date);
 CacheManager cache = CacheManager.getCacheManager("mycache");
 cache.put("mykey", wrapper);
 ```

    
Get
---
 - Basic example :
 
 ```Java
 CacheManager cache = CacheManager.getCacheManager("mycache");
 String object = null;
 object = cache.get("mykey", String.class);
  ```
  
License
=======

    Copyright 2013 Vincent Brison.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

 