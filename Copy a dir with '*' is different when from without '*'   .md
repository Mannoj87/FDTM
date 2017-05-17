# Copy a dir with '*' is different when from without '*'

Command (a)
cp -r /home/mannoj/* /home/kumar/*

Command (b)
cp -r /home/mannoj/* /home/kumar/


## Explanation: 
My intention was to copy all the directories and files under /home/mannoj/* to /home/kumar/ for which command(b) is a perfect one. 
But Command(a) puts all the files and folders in to the last sub directory under /home/kumar/. Also copies other subdirecotories under /home/kumar to the last sub directory. 
Not sure if its a bug or some logic behind it.

Example:
ls -ltr /home/mannoj/
-rw-------. 1 root root 3853 May 17 15:57 anaconda-ks.cfg
-rw-------. 1 root root 3853 May 17 15:57 anaconda

 # mkdir -p /home/kumar/A
 # mkdir -p /home/kumar/B
 # mkdir -p /home/kumar/C
 # cp -r /home/mannoj/* /home/kumar/*
 # ls -ltr /home/kumar/
total 0
drwx------. 2 root root  6 May 17 15:59 A
drwx------. 2 root root  6 May 17 15:59 B
drwx------. 4 root root 59 May 17 15:59 C
 # ls -ltr /home/kumar/A
total 0
 # ls -ltr /home/kumar/B
total 0
 # ls -ltr /home/kumar/C
total 8
drwx------. 2 root root    6 May 17 15:59 B
-rw-------. 1 root root 3853 May 17 15:59 anaconda-ks.cfg
-rw-------. 1 root root 3853 May 17 15:59 anaconda
drwx------. 2 root root    6 May 17 15:59 A
 # ls -ltr /home/mannoj/
total 8
-rw-------. 1 root root 3853 May 17 15:57 anaconda-ks.cfg
-rw-------. 1 root root 3853 May 17 15:57 anaconda
