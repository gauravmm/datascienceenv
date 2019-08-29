# Data Science Env

This is the quickest way to get started with Jupyter Notebooks for [Practical Data Science](https://www.datasciencecourse.org). We use Vagrant to configure a virtual machine that can be run on all operating systems.

To get started with this:

1. (if on Windows) install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). You need it to be in your `%PATH%`, so use the installer.
2. install [Vagrant](https://www.vagrantup.com/downloads.html)
3. (if on Windows) run `vagrant plugin install vagrant-multi-putty` in any directory to install the PuTTY plugin.
4. install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
5. open terminal/CMD in this directory and run the command `vagrant up`
6. you will see the virtual machine boot up. This takes ~3 minutes on my laptop. Once you see the prompt `ubuntu-disco login:`, minimize the virtual machine window.
7. in the original terminal/CMD window, run the command `vagrant ssh` (`vagrant putty` on Windows) to connect to the virtual machine.
8. you should get a bash shell at `/assignments`. This folder is automatically synced to the `assignments` folder here.

Great! You have a supported environment set up and ready.

To start working on a homework:

1. copy the handout to the `assignments` sub-folder here.
2. navigate to the folder with `cd` and list files with `ls` to make sure the file is there.
3. extract the handout with `tar  -xv -C hw1_get_started -f hw1_get_started.tgz`. To see what this command does, you can use [this website](https://explainshell.com/explain?cmd=tar++-xv+-C+hw1_get_started+-f+hw1_get_started.tgz).
4. install additional pip requirements for some homeworks. To do that, run `sudo pip3 install -r requirements.txt`. (Running `sudo pip ...` is a *Very Bad Idea* in most cases, this is a rare exception.)
5. start the Jupyter Notebook with `python3 -m jupyter notebook`. If you get the error `Exception: Jupyter command ``jupyter-notebook`` not found.`, then log out (with Ctrl+D) and log back in (with `vagrant ssh` or `vagrant putty`)
6. Copy the URL displayed and paste it into your favorite web browser. Jupyter Notebook should load.
