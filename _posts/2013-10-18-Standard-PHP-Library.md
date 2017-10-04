---
layout: post
title: Standard PHP Library - Part 1
---

As per the PHP documentation, SPl is a set of classes and interfaces that solve common problems.

SPL has bunch of very useful tools. Seems like due to the lack of documentation, people are having hard time in understanding.
Let me try to assimilate SPL one feature at a time. To begin with DirectoryIterator.


    $directory = new DirectoryIterator('../public');
    foreach ($directory as $key => $file) {
        if ($file->isFile()) {
            $files[] = clone $file;
        }
    }
    echo $files[1]->getFilename();


### Points to note

* Lists all the files and directories in the specified directory. Its not recursive.
* It even lists dot files (. & ..) on unix file system
* Need to use the `clone` keyword to copy it to any array. Otherwise, we cannot call functions like `getFilename()` on elements.
* Object to String function is called whenever we echo the file inside for loop.a
