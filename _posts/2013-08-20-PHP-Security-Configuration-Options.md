---
layout: post
title: PHP Security Configuration Options
---

There are several PHP configuration settings that affect security features.

* register_globals set to off.

* safe_mode set to off. This parameter doesn't really make anything safe.

* error_reporting set to off. This is visible error reporting that sends a message to the user's browser if something goes wrong. For production servers, use error logging instead. Development servers can enable error logging as long as they're behind a firewall.

* Disable these functions: system(), exec(), passthru(), shell_exec(), proc_open(), and popen().

* open_basedir set for both the /tmp directory (so that session information can be stored) and the web root so that scripts cannot access files outside a selected area.

* expose_php set to off. This feature adds a PHP signature that includes the version number to the Apache headers.

* allow_url_fopen set to off. This isn't strictly necessary if you're careful about how you access files in your code-that is, you validate all input parameters.

* allow_url_include set to off. There's really no sane reason for anyone to want to access include files via HTTP.