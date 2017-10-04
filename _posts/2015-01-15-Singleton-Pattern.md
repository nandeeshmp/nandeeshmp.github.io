---
layout: post
title: Singleton Pattern
---

Singleton pattern is used whenever there is a need to instantiate only one object of a class across the system.
Its like providing a global point of access to the object.

Examples where singleton pattern can be applied :
* Logger Classes
* Filesystems
* Database access

Singleton patter is also considered as anti-pattern because of the following in reasons :
* It breaks Single Responsibility Principle by controlling both object instantiation and its own purpose.
* It acts sort of like global state and makes testing difficult.


    class Singleton
    {
        private static $instance;

        private function __construct(){}

        public static function getInstance()
        {
            if (self::$instance == null)
            {
                self::$instance = new self();
            }
            return static::$instance;
        }
    }

    $object = Singleton::getInstance();
    var_dump($object === Singleton::getInstance());  //return true
