---
layout: post
title: Generators in PHP 5.5
---

With the release of PHP 5.5, there has been lot of buzz over the concept of 'generators' in PHP community.  Though generators are new in PHP, the concept of generators has been around since 1975. Generators first appeared in a language called CLU.

First lets look at what wikipedia has to say about generators :

In computer science, a generator is a special routine that can be used to control the iteration behaviour of a loop. A generator is very similar to a function that returns an array, in that a generator has parameters, can be called, and generates a sequence of values.
Generators are much like return statements, except they maintain the state of the function with some parameters. Next time when the function is called, it resumes execution from the point where it was saved.

So, how to write a generator? Here's the trivial example :


    <?php
    function getAlphabets(){
      yeild "A";
      yeild "B";
      yeild "C";
      yeild "D";
    }
    $alphabets = getAlphabets();
    foreach ($alphabet as $alphabets) {
        echo $alphabet;
    }


When variable $alphabets is initialized with getAlphabets() function, Generator object is returned. And when it is iterated over the foreach loop, each time it goes back to getAlphabets() function and yeilds the next value.

By this time you might be thinking why the fuck we need generators, when we can return the array of values. Well, generators come in handy when you are working with the large data sets that could out run PHP memory limits. Besides generators outperform both in memory usage and speed over the iterators.