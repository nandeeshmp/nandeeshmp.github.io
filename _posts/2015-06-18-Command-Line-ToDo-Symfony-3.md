---
layout: post
title: Command Line Todo with Symfony - Part 3
---

In the below class we tied together everything that has been built till now. We have instantiated Application() object and registered all our commands.

Additionaly, this file can be made executable by granting +x permission and specifing the interpreter (#! /usr/bin/env php) at the top.


    #! /usr/bin/env php
    <?php
    use Simplon\Mysql\Mysql;
    use Symfony\Component\Console\Application;
    use TaDa\AddCommand;
    use TaDa\DeleteCommand;
    use TaDa\ShowCommand;

    require 'vendor/autoload.php';

    $dbConn = new Mysql('localhost', 'username', 'password', 'database');

    $app = new Application('TaDa List Manager', '1.0');

    $app->add(new AddCommand($dbConn));

    $app->add(new ShowCommand($dbConn));

    $app->add(new DeleteCommand($dbConn));

    $app->run();


Find the entire source code of this simple app at [https://github.com/nandeeshmp/console-app](https://github.com/nandeeshmp/console-app)