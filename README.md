# Data Science Env

This is the quickest way to get started with Jupyter Notebooks for [Practical Data Science](https://www.datasciencecourse.org). We use Vagrant to configure a virtual machine that can be run on all operating systems.

To get started with this:

1. download the contents of this repository and put it somewhere on your computer.
2. (if on Windows) install [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). You need it to be in your `%PATH%`, so use the installer.
3. install [Vagrant](https://www.vagrantup.com/downloads.html)
4. (if on Windows) run `vagrant plugin install vagrant-multi-putty` in any directory to install the PuTTY plugin.
5. install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
6. open terminal/CMD **in the same directory as the Vagrantfile** and run the command `vagrant up`
7. you will see the virtual machine boot up. This takes ~3 minutes on my laptop. Once you see the prompt `ubuntu-disco login:`, minimize the virtual machine window.
8. in the original terminal/CMD window, run the command `vagrant ssh` (`vagrant putty` on Windows) to connect to the virtual machine.
9. you should get a bash shell. `cd assignments` to get to the folder that is automatically synced to the `assignments` folder here.

Great! You have a supported environment set up and ready.

To start working on a homework:

1. copy the handout to the `assignments` sub-folder here.
2. navigate to the folder with `cd` and list files with `ls` to make sure the file is there.
3. extract the handout with `tar  -xv -C hw1_get_started -f hw1_get_started.tgz`. To see what this command does, you can use [this website](https://explainshell.com/explain?cmd=tar++-xv+-C+hw1_get_started+-f+hw1_get_started.tgz).
4. install additional pip requirements for some homeworks. To do that, run `pip3 install -r requirements.txt`. (**Update**: you no longer need to run `sudo pip ...`, it continues to be a *Very Bad Idea*.)
5. start the Jupyter Notebook with `python3 -m jupyter notebook`. If you get the error `Exception: Jupyter command ``jupyter-notebook`` not found.`, then log out (with Ctrl+D) and log back in (with `vagrant ssh` or `vagrant putty`)
6. Copy the URL displayed and paste it into your favorite web browser. Jupyter Notebook should load.

To shut down the VM, run `vagrant halt` on your machine or `sudo poweroff` inside the virtual machine.

## Upgrading/Resetting

If you are upgrading environment versions, you may need to reset the VM. To do that:

1. run `vagrant halt` to stop the running virtual machine
2. run `vagrant destroy` to delete the current virtual machine (and keep the assignments folder)
3. download and replace the previous `datascienceenv` folder (make sure you save your work elsewhere!)
4. run `vagrant up`
