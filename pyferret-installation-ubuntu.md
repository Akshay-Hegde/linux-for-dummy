layout: page
title: "PyFerret Installation on Ubuntu 18.04/20.04 ( Python Ferret ) "
permalink: /linux-for-dummy/pyferret-installation-on-ubuntu

# PyFerret Installation on Ubuntu 18.04/20.04 ( Python Ferret ) 

Lets say current working directory is Downloads, this is your interest anywhere you can download 

```
akshay@ideapad:~/Downloads$ pwd
/home/akshay/Downloads
akshay@ideapad:~/Downloads$ mkdir pyferret
akshay@ideapad:~/Downloads$ cd pyferret/

```
Download ferret datasets from PMEL ftp

```
akshay@ideapad:~/Downloads/pyferret$ wget ftp://ftp.pmel.noaa.gov/ferret/pub/data/fer_dsets.tar.gz
--2019-07-19 22:03:39--  ftp://ftp.pmel.noaa.gov/ferret/pub/data/fer_dsets.tar.gz
           => ‘fer_dsets.tar.gz’
Resolving ftp.pmel.noaa.gov (ftp.pmel.noaa.gov)... 161.55.85.50, 64:ff9b::a137:5532
Connecting to ftp.pmel.noaa.gov (ftp.pmel.noaa.gov)|161.55.85.50|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /ferret/pub/data ... done.
==> SIZE fer_dsets.tar.gz ... 43511858
==> PASV ... done.    ==> RETR fer_dsets.tar.gz ... done.
Length: 43511858 (41M) (unauthoritative)

fer_dsets.tar.gz                    100%[=================================================================>]  41.50M   473KB/s    in 85s     

2019-07-19 22:05:09 (502 KB/s) - ‘fer_dsets.tar.gz’ saved [43511858]
```

Download latest version of pyferret from github repository
```
akshay@ideapad:~/Downloads/pyferret$ wget https://github.com/NOAA-PMEL/PyFerret/releases/download/v7.5.0/PyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz
--2019-07-19 22:11:02--  https://github.com/NOAA-PMEL/PyFerret/releases/download/v7.5.0/PyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz
Resolving github.com (github.com)... 13.234.210.38, 64:ff9b::dea:b066
Connecting to github.com (github.com)|13.234.210.38|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://github-production-release-asset-2e65be.s3.amazonaws.com/48462280/a3de6980-6769-11e9-8d1f-9bc7aef2bdcf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20190719%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190719T164103Z&X-Amz-Expires=300&X-Amz-Signature=82f5b8d9e2412e46d56e1b6c0c469ab413a3b946d0601ab1861d267f74d5c37a&X-Amz-SignedHeaders=host&actor_id=0&response-content-disposition=attachment%3B%20filename%3DPyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz&response-content-type=application%2Foctet-stream [following]
--2019-07-19 22:11:03--  https://github-production-release-asset-2e65be.s3.amazonaws.com/48462280/a3de6980-6769-11e9-8d1f-9bc7aef2bdcf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20190719%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190719T164103Z&X-Amz-Expires=300&X-Amz-Signature=82f5b8d9e2412e46d56e1b6c0c469ab413a3b946d0601ab1861d267f74d5c37a&X-Amz-SignedHeaders=host&actor_id=0&response-content-disposition=attachment%3B%20filename%3DPyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz&response-content-type=application%2Foctet-stream
Resolving github-production-release-asset-2e65be.s3.amazonaws.com (github-production-release-asset-2e65be.s3.amazonaws.com)... 52.216.138.12, 64:ff9b::34d8:8a0c
Connecting to github-production-release-asset-2e65be.s3.amazonaws.com (github-production-release-asset-2e65be.s3.amazonaws.com)|52.216.138.12|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6887241 (6.6M) [application/octet-stream]
Saving to: ‘PyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz’

PyFerret-7.5.0-RHEL7-64-Python2.7.t 100%[=================================================================>]   6.57M  1.25MB/s    in 8.7s    

2019-07-19 22:11:13 (772 KB/s) - ‘PyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz’ saved [6887241/6887241] 
```
Now install dependency packages being sudo user
```
akshay@ideapad:~/Downloads/pyferret$ sudo su
[sudo] password for akshay: 
root@ideapad:/home/akshay/Downloads/pyferret# sudo apt-get install libnetcdf-dev default-jre python-numpy  python-pyshp python-qt4 libcurl4-openssl-dev libgfortran3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```
Lets say, will install pyferret in /usr/local, you may choose path of your interest, and extract ferret executables
```
root@ideapad:/home/akshay/Downloads/pyferret# cd /usr/local/ 
root@ideapad:/usr/local# tar -xf /home/akshay/Downloads/pyferret/PyFerret-7.5.0-RHEL7-64-Python2.7.tar.gz 
root@ideapad:/usr/local# mv PyFerret-7.5.0-RHEL7-64-Python2.7/ pyferret 
root@ideapad:/usr/local# cd pyferret/ 
```
Extract ferret datasets we downloaded above from PMEL ftp
```
root@ideapad:/usr/local/pyferret# mkdir fer_dsets 
root@ideapad:/usr/local/pyferret# cd fer_dsets/ 
root@ideapad:/usr/local/pyferret/fer_dsets# tar -xf /home/akshay/Downloads/pyferret/fer_dsets.tar.gz 
root@ideapad:/usr/local/pyferret/fer_dsets# ls
data  descr  grids 
root@ideapad:/usr/local/pyferret/fer_dsets# cd .. 
root@ideapad:/usr/local/pyferret# ls
bin  contrib  examples  ext_func  fer_dsets  go  lib  ppl
root@ideapad:/usr/local/pyferret# cd bin/ 
root@ideapad:/usr/local/pyferret/bin# ls
build_fonts  Fenv                       Fgrid         Fpalette         Fpurge      Fsymbol               pyferret_template
Fdata        ferret_paths_template.csh  Fgrids        Fpattern         FshowGO     install_ferret_links
Fdesc        ferret_paths_template.sh   Finstall      Fprint           Fsort       mtp
Fdescr       Fgo                        Finstall.log  Fprint_template  Fsort.nawk  pyferre
```
Now finally install using "Finstall" script
```
root@ideapad:/usr/local/pyferret/bin# ./Finstall 
 
 This script creates the  'ferret_paths.csh' and 'ferret_paths.sh' in a directory 
 you choose using values of FER_DIR (Ferret software directory at your site) and 
 FER_DSETS (Ferret default data at your site).  Furthermore, the link (shortcut) 
 'ferret_paths' can be created which refers to either 'ferret_paths.csh' or 
 'ferret_paths.sh'.  Finally, the executable shell script 'pyferret' is created. 
 
 Sourcing one of these 'ferret_paths' files ('source ferret_paths.csh' for csh or 
 tcsh, '. ferret_paths.sh' for bash, sh ksh, or dash) will set up a user's 
 environment for running pyferret.  The pyferret script will automatically source 
 the ferret_paths script created here if it detects the ferret environment has 
 not already been set up. 
 
 You will want to run this script if you are installing PyFerret for the first time 
 or if you relocated where PyFerret is installed. 
 
 Proceed? (y/n) [y] y
 
 Customize ferret_paths files...
 
 Enter the name of the PyFerret installation directory (FER_DIR). 
 This should be the directory created from extracting the PyFerret 
 tar.gz file.  It contains subdirectories bin, contrib, examples, 
 ext_func, go, lib, and ppl. 
 A relative path name can be given (such a '.') 
 
 FER_DIR --> /usr/local/pyferret
 
 Enter the name of the directory containing the default Ferret 
 data sets (FER_DSETS).  It contains subdirectories data, descr, 
 and grids, including the data file data/coads_climatology.cdf 
 A relative path name can be given (such a '../FerretDatasets') 
 
 FER_DSETS --> /usr/local/pyferret/fer_dsets/
 
 Enter the name of the directory where you want to place 
 the newly created 'ferret_paths.csh', 'ferret_path.sh', 
 and pyferret scripts.
 A relative path name can be given (such a '.') 
 
 desired ferret_paths location --> /usr/local/
 
 To duplicate behavior found in older version of Ferret, you can 
 create a link (shortcut) 'ferret_paths' that refers to either 
 'ferret_paths.csh' or 'ferret_paths.sh'.  This is simply a 
 convenience for users and should only be done on systems where 
 all Ferret users work under the same shell (such as tcsh or bash). 
 The files 'ferret_path.csh' and 'ferret_paths.sh' can always be 
 used regardless of the answer to this question. 
 
 ferret_paths link options: 
    c - link to ferret_paths.csh (all users work under tcsh, csh) 
    s - link to ferret_paths.sh (all users work under bash, dash, ksh, sh) 
    n - do not create the link (use ferret_paths.csh or ferret_paths.sh)
 ferret_paths link to create? (c/s/n) [n] --> s
 
 Enter the desired python executable to use for running PyFerret. 
 This may simply be 'python', but on systems with multiple versions 
 of python, you need to specify the version to use, such as 'python2.6' 
 or 'python2.7', or the full-path name to desired version of python. 
 
 python executable to use: ['python'] --> 
 
 Created Finstall.log in /usr/local/pyferret/bin 
 
 Created /usr/local/ferret_paths.csh 
 
 Created /usr/local/ferret_paths.sh 
 
 Created /usr/local/ferret_paths 
     as a link to ferret_paths.sh 
 
 Created executable script /usr/local/pyferret/bin/pyferret
```

Now all done, open your favorite editor nano, gedit, vi any and add 2 lines as listed below, alias py='pyferret' is like shortcut for, instead of typing full pyferret

```
root@ideapad:/usr/local/pyferret/bin# vi /home/akshay/.bashrc
 
akshay@ideapad:~$ tail -2 /home/akshay/.bashrc 
source /usr/local/ferret_paths
alias py='pyferret'
```
Now either type pyferret or py in new terminal, after hitting go coads_demo you should be able to see map as listed below.
```
akshay@ideapad:~$ pyferret 
  NOAA/PMEL TMAP
  PyFerret v7.5 (optimized)
  Linux 3.10.0-957.10.1.el7.x86_64 - 04/25/19
  20-Jul-19 00:18     

yes? go coads_demo
! coads_demo.jnl *jd* 11/91
 
akshay@ideapad:~$ py
  NOAA/PMEL TMAP
  PyFerret v7.5 (optimized)
  Linux 3.10.0-957.10.1.el7.x86_64 - 04/25/19
  23-Jul-19 21:50     

yes? 

```
