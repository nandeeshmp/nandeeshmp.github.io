---
layout: post
title: Error Handling In PHP
---

"Any man is liable to err, only a fool persists in error." -- Marcus Tullius Cicero. Error handing in PHP can be broadly categorized into two types.

External Errors : These errors are not bugs in the code, but something that are external that gets in the way of execution of program like failing to connect to database.
Logical Errors  : These are bugs in the code. These kind of errors are difficult to track down and difficult to debug because by definition their location is not known.
PHP has built in support for handling errors. Based on the severity we can classify them in to three levels as

E_NOTICE     :  Minor and non-fatal errors. These will not stop the execution of the script
E_WARNING    : 	Non-fatal run-time errors, doesn't halt the execution of the program.
E_ERROR      : 	These are fatal errors and will halt the execution of the program.

PHP provides the function trigger_error() to help user to trigger his own errors. Again user can trigger three types of errors:

E_USER_NOTICE, E_USER_WARNING & E_USER_ERROR

Default error level used by trigger_error() is E_USER_NOTICE.

In addition to these, there are five other categories that occurs some what less frequently.

E_PARSE				:   Script has syntactic error and cannot be parsed. It is a fatal error.
E_COMPILE_ERROR     :   A fatal error that occurred during compiling the script.
E_COMPILE_WARNING 	:   Non-fatal error that occurred while parsing the script.
E_CORE_ERROR        :   A fatal run time error occurred in the engine.
E_CORE_WARNING      :   A non-fatal run time error occurred in the engine.

In addition, PHP uses E_ALL error category for all error reporting level.

You have four choices for handling errors : Display them, log them, ignore them or act on them

###Displaying Errors

In php.ini file set the following flag 'on' to display errors.

display_errors = on;

Though setting the above flag 'on' on the development machine is recommended, it should be turned off on the production machine. Leaving it 'on' and displaying the errors to end users shows that the code is buggy and many times it reveals the script internals which can be used for nefarious purpose.

###Logging Errors

Logging provides a trace of any errors for audit-able purpose. PHP supports logging errors to a file or to a syslog. One can turn on error logging by setting the log_errors to 'on' as shown below in php.ini file.

log_errors = on

Logging to a file or to a syslog can be set as following

error_log = /path/to/filename
error_log = syslog

###Ignoring Errors

We can suppress the errors in PHP by prefixing the '@' operator. For example if you want to suppress error that could occur while opening the file if the file doesn't exists, you do this as below.

$fp = @fopen("file_name");

###Acting on Errors

PHP allows developers to set custom error handlers with set_error_handler() function. For example if you want to store all the errors that are generated into a database, you can do so by writing a custom function error_handler_store_db(){....} and calling it with set_error_handler("error_handler_store_db")