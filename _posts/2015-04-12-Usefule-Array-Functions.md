---
layout: post
title: Useful Array Functions
---

Just a recap of useful array functions.

$cars = ['Bentley Continental GTC', 'Aston Martin DB9', 'Cadillac Escalade', 'Ferrari FF', 'Audi A8'];


    // splits the array into sizes of 2
    var_dump(array_chunk($cars, 2));

    // reverse the values of array
    var_dump(array_reverse($cars));

    // flip array keys and values
    var_dump(array_flip($cars));

    // gets all array keys
    var_dump(array_keys($cars));

    // applies callback to elements
    var_dump(array_map(function ($value)
    {
        return 'Car : '. $value;
    }, $cars));

    // pick random array element [Key]
    var_dump(array_rand($cars));

    // return array values
    var_dump(array_values($cars));

    // applies callback to elements
    var_dump(array_walk($cars, function($value, $key){
        echo $key .'=>'. $value;
    }));

    // push element to end of the array
    array_push($cars, 'Cadillac ELR');
    var_dump($cars);

    // remove last element of an array
    $cars = array_pop($cars);
    var_dump($cars);
