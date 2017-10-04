---
layout: post
title: Instance Variables
---

Instance variables makes it possible to share variables even if they are not global. In case, if you want to get rid of global variables in your legacy PHP application, trick is to turn them into instance variables.

Lets assume in eCommerce project getPurchaseDetails() function uses following globals to retrive user's purchase details.


    global $database, $userDetails;
    // $database : Object representing a database connection.
    // $userDetials : Object representing details of the logged in users.


We can refactor the above code to eliminate global variables as follows :


    class PurchaseDetials(){
        public $database;
        public $userDetails;

        public __construct($database, $userDetails){
            $this->database = $database;
            $this->userDetails = $userDetails
        }

        function getPurchaseDetails(){
            $this->database->query( SELECT * FROM purchase_details );
        }
    }


Also, note that instance variable $database contains database object & variable $userDetails contains user object. In PHP5, this means an object contains reference to another object.