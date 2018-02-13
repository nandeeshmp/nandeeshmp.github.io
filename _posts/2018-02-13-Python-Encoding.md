---
layout: post
title: Encoding Python Source Files.
---

Python interpreter defaults to ASCII as default encoding, if no encoding is specified. To specify encoding one can place below line as firts or second line in the source files. 

### Specifing Encoding
   # _*_ coding: <encoding name> _*_


### Example Encoding
   # _*_ coding: utf-8 _*_


Encoding can be specified in couple of more formats. In short, it has to match below regular expression.

### Encoding regex
   ^[ \t\v]*#.*?coding[:=][ \t]*([-_.a-zA-Z0-9]+)


[[https://github.com/nandeeshmp/nandeeshmp.github.io/blob/master/images/2018-02-13_07-32-39.png|alt=python-encoding]]
