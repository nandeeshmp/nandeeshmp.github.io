---
layout: post
title: Command Line Todo with Symfony - Part 2
---

Each command class implements configure() and execute() functions. 

configure() function is the place to configure the command and execute() function handles all the necessary logic to perform the perticular action.

Also, note we are injecting InputInterface and OutputInterface to get the user input and write out text to console respectively.

### Add a To-Do

    namespace TaDa;
    use Simplon\Mysql\Mysql;
    use Symfony\Component\Console\Input\InputArgument;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    class AddCommand extends Command {

        private $dbConn;

        public function __construct(Mysql $dbConn)
        {
            $this->dbConn = $dbConn;
            parent::__construct($this->dbConn);
        }

        public function configure()
        {
            $this->setName('add')
                ->addArgument('task', InputArgument::REQUIRED)
                ->setDescription('Add task to the list');
        }

        public function execute(InputInterface $input, OutputInterface $output)
        {
            $task = $input->getArgument('task');  // get the task from user
            $this->dbConn->insert('tasks', ['task' => $task]); // insert task into db
            $output->writeln($task);
            $this->showList($output); // show the list of todos
        }
    }


### Delete a To-Do

    namespace TaDa;
    use Simplon\Mysql\Mysql;
    use Symfony\Component\Console\Input\InputArgument;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    class DeleteCommand extends Command{

        private $dbConn;

        public function __construct(Mysql $dbConn)
        {
            $this->dbConn = $dbConn;
            parent::__construct($this->dbConn);
        }

        public function configure()
        {
            $this->setName('del')
                ->addArgument('task', InputArgument::REQUIRED)
                ->setDescription('Delete task from the list');
        }

        public function execute(InputInterface $input, OutputInterface $output)
        {
            $taskId = $input->getArgument('task');
            $this->dbConn->delete('tasks', ['id' => $taskId]);
            $output->writeln('<info>Task deleted from the list</info>');
            $this->showList($output);
        }
    }


### Show list of To-Dos

    namespace TaDa;
    use Symfony\Component\Console\Input\InputInterface;
    use Symfony\Component\Console\Output\OutputInterface;

    class ShowCommand extends Command
    {

        public function configure()
        {
            $this->setName('show')
                ->setDescription('Show the list of tasks');
        }

        public function execute(InputInterface $input, OutputInterface $output)
        {
            $this->showList($output);
        }
    }
