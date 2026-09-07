**Package Commands**

sudo add-apt-repository / dpkg


**Manual Download Example** 
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

Add Sublime Text 3's repository to our apt sources list. A good practice is to have a separate file for every different community/3rd party repository that we add.

Create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information like so:

And now use Nano or a text editor of your choice to add \& save the Sublime Text 3 repository into this newly created file:
deb https://download.sublimetext.com/ apt/stable/



After we have added this entry, we need to update apt to recognise this new entry -- this is done using the apt update command



Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using apt install sublime-text



Removing packages is as easy as reversing. This process is done by using the add-apt-repository --remove ppa:PPA\_Name/ppa command or by manually deleting the file that we previously added to. Once removed, we can just use apt remove \[software-name-here] i.e. apt remove sublime-text

