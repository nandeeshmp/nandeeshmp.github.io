---
layout: post
title: Multiple Calls To mysql_connect()
---

Script To Make Multiple Calls To mysql_connect()

One can make multiple calls to mysql_connect using the following script :


    $dbhandle_1 = mysql_connect ( $host, $user, $pass );
    $dbhandle_2 = mysql_connect ( $host, $user, $pass, true );
    $database1 = mysql_select_db ( 'database_name_1', $dbhandle_1 );
    $database2 = mysql_select_db ( 'database_name_2', $dbhandle_2 );


Now to query 'database_name_1' use statement1 and for 'database_name_2'  use statement2


    mysql_query( "SELECT * FROM table", $dbhandle_1 ); //statement1
    mysql_query( "SELECT * FORM table", $dbhandle_2 ); //statement2


If both databases are on the same host and share same credentials, keep calling mysql_select_db to switch between databases.