---
layout: post
title: Laravel Accessors & Mutators
---

Accessors & Mutators in laravel help us to transform the data while inserting and retriving from the database.
Note the function names should follow camel case.


    class User extends Model
    {
        protected $table = 'users';

        protected $fillable = ['name', 'email', 'password'];

        protected $hidden = ['password', 'remember_token'];

        public getFirstNameAttribute($value)
        {
            return ucfirst($value)
        }

        public setFirstNameAttribute($value)
        {
            $this->attributes['first_name'] = strtolower($value);
        }

    }


In the above code, to transform the values of first_name column we use getFirstNameAttribute/setFirstNameAttribute.