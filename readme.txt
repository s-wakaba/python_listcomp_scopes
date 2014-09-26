*** About ***

Patch of an optional future of enclosed scopes
in list comprehensions for CPython 2.7.8
written by s-wakaba @ GitHub.

Anyone can use these patch and ducument freely on
PYTHON SOFTWARE FOUNDATION LICENSE VERSION 2.



*** Usage ***

[yourname@hostname:~/listcomp_scopes/2.7.8]
$ md5sum listcomp_scopes-2.7.8.patch Python-2.7.8.tgz 
41aa4f61d250b485256c90f3392e342f  listcomp_scopes-2.7.8.patch
d4bca0159acb0b44a781292b5231936f  Python-2.7.8.tgz

[yourname@hostname:~/listcomp_scopes/2.7.8]
$ tar -xzf Python-2.7.8.tgz 

[yourname@hostname:~/listcomp_scopes/2.7.8]
$ patch -p 1 -i listcomp_scopes-2.7.8.patch 
patching file Python-2.7.8/Include/code.h
patching file Python-2.7.8/Include/compile.h
patching file Python-2.7.8/Include/pythonrun.h
patching file Python-2.7.8/Lib/__future__.py
patching file Python-2.7.8/Python/compile.c
patching file Python-2.7.8/Python/future.c
patching file Python-2.7.8/Python/symtable.c

[yourname@hostname:~/listcomp_scopes/2.7.8]
$ cd Python-2.7.8

[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ ./configure && make


=== Please Wait a Moment... ===


[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ cat > test1.py
a = 'spam'
b = [a*2 for a in xrange(10)]
print a

[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ ./python test1.py
9

[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ ( echo 'from __future__ import listcomp_scopes'; cat test1.py ) > test2.py

[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ cat test2.py
from __future__ import listcomp_scopes
a = 'spam'
b = [a*2 for a in xrange(10)]
print a

[yourname@hostname:~/listcomp_scopes/2.7.8/Python-2.7.8]
$ ./python test2.py
spam

