TITLE : Swiss Tournament Schema <br>
AUTHOR : Ellis Enobun<br>
PYTHON VERSION : Python 3.5<br>
PROJECT : A Python module that uses the PostgreSQL database to keep
          track of players and matches in a game tournament<br>
CODE CHECKER: PEP8</b>

# PROJECT DESCRIPTION:

A database schema developed to store the game matches between players. Written code to query 
this data and determine the winners of various games.

I will quickly walk you through the process of setting up the virtual machine, and running this databse schema 
using the virtual machine.

I have also placed a very rich, step by step code explaination inside the tournament.sql file.

(PART A):

# GETTING STARTED:

Project was completed within the Vagrant Virtual Machine. The materials needed are the Vagrant,
Virtual Box tool and Git.

STEPS:

-- Git:  Download Git from http://git-scm.com/downloads. Install the version for your operating system.

-- VirtualBox: This runs the VM. Download it from https://www.virtualbox.org/wiki/Downloads, install.

-- Vagrant: Configures the VM and lets you share files between your host computer and the VM's 
filesystem download it from https://www.vagrantup.com/downloads. install


(PART B):

##Verify that Vagrant is installed and working by typing in the terminal:

    $ vagrant -v   # will print out the Vagrant version number

##Clone the Repository
Once you are sure that VirtualBox and Vagrant are installed correctly execute the following:

    $ git clone https://github.com/elnobun/Swiss-Tournament-Project.git
    $ cd Swiss-Tournament-Project
    $ cd vagrant

###Verify that these files exist in the newly cloned repository:###<br>

--tournament             #folder containing tournament files
----tournament.py        #file that contains the python functions which unit tests will run on
----tournament_test.py   #unit tests for tournament.py
----tournament.sql       #postgresql database 
--Vagrantfile            #template that launches the Vagrant environment
--pg_config.sh           #shell script provisioner called by Vagrantfile that performs some configurations 

###Launch the Vagrant Box

    $ vagrant up   #to launch and provision the vagrant environment
    $ vagrant ssh  #to login to your vagrant environment

###Enter the Swiss Tournament

    vagrant@vagrant-ubuntu-trusty-32:~$ cd /vagrant/tournament

###Initialize the database

    vagrant@vagrant-ubuntu-trusty-32:/vagrant/tournament$ psql
    vagrant=> \i tournament.sql
    vagrant=> \q

###Run the unit tests

    vagrant@vagrant-ubuntu-trusty-32:/vagrant/tournament$ python tournament_test.py


You should see these results:

1. Old matches can be deleted.
2. Player records can be deleted.
3. After deleting, countPlayers() returns zero.
4. After registering a player, countPlayers() returns 1.
5. Players can be registered and deleted.
6. Newly registered players appear in the standings with no matches.
7. After a match, players have updated standings.
8. After one match, players with one win are paired.
Success!  All tests pass!

(PART C):

###Shutdown Vagrant machine

    $ vagrant halt


###Destroy the Vagrant machine

    $ vagrant destroy


###References
* https://wiki.postgresql.org/wiki/Using_psycopg2_with_PostgreSQL
* http://www.postgresqltutorial.com
* http://initd.org/psycopg/docs/
* www.postgresql.org
* https://stackoverflow.com/questions/14880192/iterate-a-list-of-tuples



