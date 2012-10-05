============ README ==============

=== SETUP DJANGO ===

The script works as follows:

1.)  The script first downloads the latest version of django
     from the git repo.  This will be checked out to the global
		 trunk variable folder (inside of whatever folder parameter
		 is passed).

		 This will then create a hidden file in the home directory that
		 specifies the location of the trunk so that the param is not needed
		 later.  The default name of this file is ~/.django_trunk.
		 Changing the parameter will change the location of the trunk
		 and remove the old trunk.
		

2.)  A folder is created in the user's home directory called PYENV.
     this will serve as a virtual environment for python, and will
     be the location of the virtual python environment and the django
     installation (more description on a virtual environment and how
     to use it (and love it!) follows).

3.)  After the virtual environment is installed, pip (a python package
     installer) is used to install django from the folder that was
     downloaded from git (at the user's discretion, of course).  It 
     will be installed in the python package folder within the PYENV folder.

=========== WTF IS A VIRTUAL ENVIRONMENT AND WHY DO I WANT IT? ==========

If you'd like to skip all this, go read a book on operating systems.  It's
totally not convoluted (a kid could understand virtual environments, man).

=== What they are and how they work (sort of) ===

A virtual environment is a user-level environment that doesn't require
user priveleges for things like the installation of libraries and other
binaries.  The typical user environment can be found in the /etc/profile
file (toward the top) for a general overview of folders that are used in
the user's environment.

When running a command in the command shell, the environment string is used
to find the full path of the command before telling the user whether or not
the command was found.  For example, running the command:

echo CowDung

Will take the first token of the string and look for the location of the "echo"
command based on the environment string in /etc/profile.

If one wants to run their own environment for python, it's somewhat similar.
Initially, when python is looking for packages when things like the "import"
command are used, they typically look in the folder
'/usr/lib/pythonX.X/site-packages/' or something similar before eventually
giving up and whining to the user that the package couldn't be found anywhere.

=== Why do I need crap for django? ===

If one wants to install django on a computer where they don't have root
priveleges. This script is needed because the folder /usr/lib/pythonX.X/foo-jangles
(it's not an officially supported folder, but you get the idea) requires root
priveleges in order for a user to write to it.  

Because I (the jerk that wrote this convoluted bash script in the first place) 
am too lazy to talk to the prof about having django installed on the lab computers, 
this script was written (which is way more fun that asking for 
permission like a tool).

=== How the hell do I actually ***use*** this? ===

The folder to which this script stores the virtual environment is initially PYENV,
and since this isn't appended to the /etc/profile environmental variable,
one needs to write the absolute path in order to run this "special" version of 
python that knows about the django installation.

If you read earlier, the location of this folder is in whatever folder "setup-django"
was run.  To run python through the virtual environment, you need to run it like this
from the aforementioned install directory:

./PYENV/bin/python 

But!  If you want to have a fun time not being frustrated with this, there's
a special python script called "vpython-env" included in the package that contains
the python environment.  It changes the prompt so that you can't forget you're in 
a virtual environment that contains the wacky-different version of python that runs
separate from regular python.
