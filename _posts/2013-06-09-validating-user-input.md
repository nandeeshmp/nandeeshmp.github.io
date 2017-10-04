---
layout: post
title: Validating User Input For Malacious Code
---

All forms that take input from the user are vulnarable for SQL injection attacks. It is very crucial to validate the user input before running a SQL query. Below function demonstrates the use of mysql_real_escape_string(), get_magic_quotes_gpc(), addslashes() and stripslashes() to validate the user input before running SQL queries.

get_magic_quotes_gpc() -- Gets the configuration setting of magic_quotes_gpc. Returns 0 if it is set off  or 1 otherwise.

mysql_real_escape_string() -- Escapes special charecters in a string.

addslashes() and stripslashes()  -- As their names indicate, used to add slashes and strip slashes from a string. Specially useful when we want to escape special charecters like single quote ( ' ), double quote ( " ), back slash ( \ ) and NUL from a string that we want to store in the database.


    function validate_query( $query ){
        $real_escape_string_exists = function_exists("mysql_real_escape_string");
        $magic_quotes_active = get_magic_quotes_gpc();

        if( $real_escape_string_exists ){
            if( $magic_quotes_active ){
                $query = stripslashes($query);
            }
            $query = mysql_real_escape_string($query);
        }else{
            if( !$magic_quotes_active ){
                $query =  addslashes($query);
            }
        }
        return $query;
    }
