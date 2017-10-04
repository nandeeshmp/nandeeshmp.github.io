---
layout: post
title: Using cURL in PHP
---

curl_init() is used to make a connection to a web page and retrieve its data.


    $c = curl_init();


Now with curl_setopt() function to specify the connection settings. The most important setting is the target URL. Call the function as follows, with CURLOPT_URL as the option name and the last argument the desired URL:


    curl_setopt($c, CURLOPT_URL, "http://www.google.com/");


One of these features is including the HTTP header with the output. We can turn it off as follows:


    curl_setopt($c, CURLOPT_HEADER, false);


cURL automatically prints the accessed page instead of returning it as a string. We need a string if we intend to analyze the page somehow, so use the CURLOPT_RETURNTRANSFER option to say that we want the output as a string:


    curl_setopt($c, CURLOPT_RETURNTRANSFER, true);


We are now ready to access the page with the curl_exec() function:


    $page_data = curl_exec($c);


Finally, we close the connection with curl_close():


    curl_close($c);
