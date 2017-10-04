---
layout: post
title: Command Line Todo with Symfony - Part 1
---

In this series of articles, We'll be building a simple To-do console app using Symfony console component.
To start with lets pull the following packages from composer repository -

* symfony/console - Its the symfony console component.
* simplon/mysql - To interact with database, we'll use this small package.


    {
        "require" : {
            "symfony/console" : "~2.0",
            "simplon/mysql": "0.7.0"
        },
        "autoload" : {
            "psr-4" : {
                "TaDa\\" : "src/"
            }
        }
    }


Note we are using psr-4 autoloading and namespaced our app as TaDa
Our ToDo app need the following functionalites -

* Add to list
* Delete from list
* Show list items

Since we want to show list items after every addition and deletion, lets include it in our base class and every other class inherit it.


    <?php
    namespace TaDa;
    use Simplon\Mysql\Mysql;
    use Symfony\Component\Console\Command\Command as SymfonyCommand;
    use Symfony\Component\Console\Helper\Table;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    class Command extends SymfonyCommand
    {
        private $dbConn;

        public function __construct(Mysql $dbConn)
        {
            $this->dbConn = $dbConn;

            parent::__construct();
        }

        public function showList(OutputInterface $output)
        {
            $tasks = $this->dbConn->fetchRowMany('SELECT id, task FROM tasks');

            $table = new Table($output);

            $table->setHeaders(['Id','Task'])->addRows($tasks)->render();

        }
    }
