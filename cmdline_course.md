---
layout: default
---

## Commandline Tools for Linguists, fall 2020

Commandline Tools for Linguists is a course for linguists, maybe more specifically those who take interest in language technology and technological methods of language processing. The course provides students with basic knowledge and skills regarding the command line environment, UNIX operating system and some corpus-handling tools and methods. Creating a Github account and learning the basics of Git is also a part of the course, which will surely prove very helpful for making and sharing projects, which in turn will likely be helpful in working life. 

What follows next is a brief description of each week of the course as well as my reflection on what I've learned.

#### Week 1: Command Line Environments

The goal of the first week was to familiarize ourselves with the most basic commands, such as renaming files using `mv`:

```
mv file new_file
```

where 'file' is renamed 'new_file'. The goal was also to get comfortable with a command line text editor, I personally prefer to use nano. In addition to writing and manipulating text files, we got familiar with some of the useful shortcuts that are available in most command line text editors, such as being able to move to a specific line quickly, or finding out the number of lines in the file. Another important command this week was `wget`, which allows us to download files from the internet straight form the command line.

I was already familiar with most of the topics and commands learned this week, as I have used the command line environment before in my computer science studies. I think, however, that rehearsing the more simple things can be useful at times, and I definitely got more comfortable with the commands in this week's material. Getting more familiar with nano shortcuts was especially useful.

#### Week 2: Basics of a UNIX System

The topic of the second week was to get some more practice with the basic UNIX commands, such as `ls` and `cp`. In addition, we learned what it means to check and change the permissions of a file using `chmod`. For example, denying the permission to execute a file from everyone, but giving everyone a permission to read the file, is done with the following commands:

```
chmod a-x example.sh
chmod a+r example.sh
```

where example.sh is a script. Another topic of the week was process management in Unix. I learned how to check currently running processes and terminate them.

Lastly, we got to connect to a remote server using ssh, and copying files back and forth from our local server and the remote one, which, in our case, was Puhti. 

The new thing that I learned this week was reading about processes and how to manage them. It was also very important to get more practice with checking and changing permissions, even though I was sort of familiar with the topic already. Using ssh to connect to remote servers was also not a new thing for me, but rehearsing the process and commands was definitely useful.

#### Week 3: Basic Corpus Processing

One theme of week 3 was to learn about the different encoding systems and how some of them are related. I also learned new techniques and methods for corpus processing, such as the following commands:

* head
* tail
* uniq
* sort
* tr

I also learned how to convert characters, such as newlines, to a Unix-format. Probably one of the most useful tools of corpus processing, `grep` was also presented this week. I was already familiar with the basic use of `grep` and I have used regex quite a lot in the past. It was still very useful to get familiar with using regular expressions in the command line environment. Here is one example of using `egrep` along with another useful command `wc`:

```
egrep "^[Cc]" word_list.txt | wc -l
```

This spell counts the words that start with either upper or lower-case 'C' in a file called word_list.txt. The `wc -l` command counts the lines where a word that matches the regular expression `^[Cc]`.

I also learned the basics or processing csv-files in the command line, such as combining several files while omitting unnecessary columns, and applying `egrep` commands to the produced files. 

#### Week 4: Advanced Corpus Processing

The main theme of this week was the `sed` command. `sed` is a very versatile command, with which you can quite easily modify text files, such as substitute strings with another with the option `s` and delete occurrences of specific strings with the option `d`. `sed` was a completely new command for me, and getting the hang of it definitely took some trial and error. I would not consider myself an expert, but I will definitely get some use out of this tool in the future.

Another goal was to learn to pipe commands together with the `|` character, and form long pipes that perform rather complicated tasks, such as convert text to lowercase, sort the words, count frequencies and save the output to a new file:

```
cat word_count.txt | tr '[:upper:]' '[:lower:]' | sort | uniq -c | egrep "dog" > dog_count.txt
```

The command `diff`, which was another new one for me, was also introduced in this week's quiz. With it you can easily inspect the differences of two files with the following syntax:

```
diff file1 file2
```

#### Week 5: Scripting and Configuration Files

![mem](https://imgs.xkcd.com/comics/wanna_see_the_code.png)
*Comic from [xkcd](https://xkcd.com/2138)*

The goal of this week was to learn to write useful scripts and manipulate configuration files to make the command line environment more user-friendly. The idea behind script files is being able to combine several commands into one executable file. This can save a lot of time and effort when solving more complex tasks, which require several steps. Script files can take parameters that are given when executing the script. Let us look at the following script:

```
#!bin/bash

# Adding all changes to git, adding them to a commit and pushing to origin
# Required parameters are name of the commit and name of branch

git add .
git commit -m $1
git push origin $2
```

Here we have a script that adds all changes to git, creates a commit with a message given as the first parameter, and finally pushing the commit to a remote origin to a branch, of which name is given as the second parameter. If the name of the script was push.sh, the script could be executed, for example, as follows:

```
bash push.sh "Initial commit" "cmdline-course"
```

This week, I found manipulating the .bashrc file to my liking extremely helpful. I was able to make my prompt look clean and appealing to the eye and determine several useful aliases, such as navigating to the directory of this course with the command `kik` and to the directory of this Github page with `io`. 

#### Week 6: Installing and Running Programs

On week 6 the goal was to get familiar with installing programs and Python packages in the command line and learn to write and use Makefiles.

For my Ubuntu-environment, installing software is done using a package manager via the command `apt-get`. Package managers download all dependencies and packages needed for the software in question. For many installations, you will need to be the root user. Instead of actually logging in as the root user, it is recommended to execute such commands with `sudo`, which allows you to run commands as the root user from your current user. Installing a made-up software called `easyprogramming` as the root user in a Unix environment would look like this:

```
sudo apt-get install easyprogramming
```

Installing Python packages that do not come with the standard Python distribution is done using the command `pip`, which is a package manager for Python. Installing the helpful software NLTK (Natural Language Tool Kit) via pip looks like this:

```
pip install nltk
```

Lastly, I learned a completely new thing, which is the concept of Makefiles. I had never dealt with one before, and understanding the syntax took quite a bit of trial and error. Eventually, when I got the hang of it (somewhat), Makefiles seem a very helpful tool. The basic idea of Makefiles is that they are a type of file which can be executed with the program `make`. The file contains all necessary information for the `make`-program to create a working software or library. 

#### Week 7: Git, Github, Version Control, and Jekyll

For the final week, the theme was version control. I was already familiar with most of the topics this week, as I have used Git and Github before for my computer science studies. I had not, however, created a Github Pages website before, so it has been exciting to learn. For creating the site, we used the static site generator software Jekyll. Installing Jekyll and getting it to work how I wanted was quite a hassle, as it turned out my Ubuntu version (16.04) only supports ruby2.3, and what was needed is 2.5. After upgrading to Ubuntu 18.04, I managed to get everything working.

For a static web page like this one, you need a git repository with all the needed material, such as template files and a configuration file, which together form all the needed pieces for Jekyll to create a website. When the necessary pieces for the site are in the repository, you can build the site with the following command:

```
bundle exec jekyll serve
```

and see your site in the server address described in the output.
