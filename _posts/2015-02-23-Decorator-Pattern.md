---
layout: post
title: Decorator Pattern
---

Decorator pattern is used to prevent class explosions.


    interface PizzaClass
    {
        public function getCost();
    }

    class Pizza implements PizzaClass
    {
        public function getCost()
        {
            return 350;
        }
    }

    class Toppings implements PizzaClass
    {

        private $pizza;

        public function __construct(PizzaClass $pizza)
        {
            $this->pizza = $pizza;
        }

        public function getCost()
        {
            return 50 + $this->pizza->getCost();
        }
    }

    class Cheese implements PizzaClass
    {

        private $pizza;

        public function __construct(PizzaClass $pizza)
        {
            $this->pizza = $pizza;
        }

        public function getCost()
        {
            return 40 + $this->pizza->getCost();
        }
    }

    $pizza = new Pizza();
    $pizzaWithCheese = new Cheese($pizza);
    $pizzaWithCheeseAndToppings = new Toppings($pizzaWithCheese);

    echo $pizza->getCost();  // returns 350
    echo $pizzaWithCheese->getCost(); // returns 390
    echo $pizzaWithCheeseAndToppings->getCost(); // returns 440


By writing the code in this way, we have following benefits  -

* Adhere to single responsibility principle.
* Achieved separation of concerns.
* Coded to an interface.
* Used Dependency Injection to inject what is necessary.