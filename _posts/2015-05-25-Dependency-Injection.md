---
layout: post
title: Dependency Injection
---

According to wikipedia, dependency injection is a software design pattern that implements inversion of control for resolving dependencies. 

In the below example, we are injecting Mailer service and UserRepository into user controller. By doing so, we have seperated concerns into their own classes. Thus achieving the SRP. 

Another advantage of dependency injection is we can swap out one service with another without having to change our controller. 


    class UserController extends Controller
    {
        private $mailer;
        private $user;

        public function __construct(Mailer $mailer, UserRepository $user)
        {
            $this->mailer = $mailer;
            $this->user = $user;
        }

        public function register()
        {
            $this->user->register();
            $this->mailer->sendRegistration();
        }
    }
