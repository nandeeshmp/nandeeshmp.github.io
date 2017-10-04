---
layout: post
title: Auto Loading Classes in PHP
---

__autoload() function is used to load the classes automatically on the fly. When the parser has the trouble to find a perticular class, it automatically searches for it in __autoload function. Using this function we can get rid of redundant require / include statements as explained below.


    //File Name : User.php
    class User{
        function getName(){
            return "Developer";
        }
    }


Lets assume that we are having a User class in a seperate file called User.php. One way to load this class is by calling the statement require_once 'User.php' as shown below.


    // File Name : index.php
    require_once 'User.php';
    $user = new User();  //
    echo $user->getName();


Suppose if we want to load five different classes, using the above method we will have to manually load them using five require_once statements. By using the __autoload() function we can get rid of redundant require_once statements and load classes automatically.



    // File Name : index.php
    function __autoload($className){
        require_once $className.'.php';
    }
    $user = new User();  //


When the parser executes line 6 and finds that class User() has not been defined, it immediately goes in search for it in __autoload($callName) and loads User() class using the statement in the line 3.