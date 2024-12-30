# MLM
##

## Chapter 1. INSTALLTION

The software is developed using the Perl programming language. It can operate as a standard CGI-BIN program or Fast CGI (refer to section 1.11 for more details). In addition to running CGI, you need to access the MySQL database and execute commands under the shell, if you want to run built-in unit and functional testing suites. You should pass these tests to ensure successful installation and accurate compensation calculations.

### 1.1) Download Perl Package _Genelet_
```
```
Assume your current directory is named *SAMPLE_home*. After cloning, a new directory named *perl* will be created within *SAMPLE_home*.

Please note that in a real environment, the home directory will not be named *SAMPLE_home*. Therefore, you should replace all mentions of *SAMPLE_home* in the instructions below with the name of your actual home directory.

### 1.2) Download _mlm_
```
```
After the clone, directory _mlm_ will be created with 4 sub directories: *lib*, *conf*, *www* and *views*. The file structure will look like this:

```
SAMPLE_home /
            perl    /
                       Genelet
            mlm /
                       lib    /
                                  MLM
                       conf   /
                       www    /
                       views  /
```                     

### 1.3) Prepare Web Server

Please have your web server to assign website's document_root to be *www*. You should also assign both *SAMPLE_home/perl* and *SAMPLE_home/mlm/lib* to be in the Perl path:
```
$ export PERL5LIB=/SAMPLE_home/perl:/SAMPLE_home/mlm/lib
```
_Genelet_ and _mlm_ use only basic 3rd-party modules, which your server may already have. Here is the list of the modules and the corresponding packages in Ubuntu:
```
Test::Class               sudo apt-get install libtest-class-perl
Digest::HMAC_SHA1         sudo apt-get install libdigest-hmac-perl
JSON                      sudo apt-get install libjson-perl
XML::LibXML               sudo apt-get install libxml-libxml-perl
Template                  sudo apt-get install libtemplate-perl
CGI::Fast (optional)      sudo apt-get install libcgi-fast-perl
```

### 1.4) Create MySQL Database

Create a MySQL database, and have username and password to access it. 

#### 1.4.1) Migrate the database schema

File *01_init.sql* in *conf* is the database schedma. You need to load it into the database using a client tool. 

#### 1.4.2) Migrate data

Let's build one compensation plans, add one backend admin user and one new member into the database, so we can launch the initial website.

Load 03_setup.sql into the database using a client tool.

### 1.5) Build _config.json_ and _component.json_

Copy the sample config to config.json in this directory. i.e. $ cp SAMPLE_config.json config.json . Edit config.json, make sure
 - replace SAMPLE_homme to your top directory hosting "mlm" and "perl"
 - replace SAMPLE_domain by your real domain name (or sub-domain name)
 - choose random security codes. A typical string is about 80 chars.
 - replace the sample MySQL access parameters in the *Db* block

If you are in Bash, you may include "perl" and "mlm/lib" into your shell by
```bash
$ export PERL5LIB=/SAMPLE_home/perl:/SAMPLE_home/mlm/lib
(replace SAMPLE_home by the real one)