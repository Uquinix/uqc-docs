## Setting up the Environment

<div class="info" markdown="1">
Information on cross-compiling will be added shortly.
</div>

Unfortunately, UQC can only be built on a FreeBSD 13 based operating system - as this is the version UQC currently uses. 

Fortunately, however, FreeBSD is easy to set up.

Work is being done to allow cross-compiling of UQC, however, this is experimental and undocumented as of yet.

### <strong>Setting up on macOS</strong>

#### Downloading UTM
For this instance, we have used [UTM](https://mac.getutm.app) - as it has a sleek, simplistic interface and is a GUI wrapper for QEMU. (Feel free to use any VM software, as it will all work).

[Download Here.](https://mac.getutm.app)

#### Creating the VM

Now that UTM and the ISO file have been installed, we can now continue to create our VM for FreeBSD.

 1. Firstly, open UTM and select "Create a new virtual machine". You can pick between "Virtualize" or "Emulate" depending on your hardware. 

 2. Then, press "Other" and browse for your ISO file. 

 3. Allocate as much RAM as you would like, as well as the number of CPU cores. 

 4. Then, specify how much storage you wish to allocate.

 5. It is then optional whether you want to have a shared directory, for this case we will just continue.

 6. You can then name your VM and boot.

### <strong>Setting up on Linux</strong>
#### Downloading Virtual Box
[Virtualbox](https://www.virtualbox.org) is a commonly used Virtual Machine Manager, it is great for both Linux and Windows due to its compatibility, performance and features.

For your VM to work correctly, you will need to enable the VT-x/VT-d extension for Intel Processors, for AMD you will have to enable AMD-v/SVM.

##### Debian-based distributions
(Debian) To begin installing VirtualBox, update your repository cache:

~~~ shell
$ sudo apt-get update
~~~

Or, for Arch-Based Distributions:

~~~ shell
$ sudo pacman -Sy
~~~

(Debian) Then, download and install VirtualBox by running:

~~~ shell
$ sudo apt-get install virtualbox
~~~

Or, for Arch-Based Distributions:

~~~ shell
$ sudo pacman -S virtualbox
~~~

(Debian) (Optional) Next, install the VirtualBox Extension Pack:

~~~ shell
$ sudo apt-get install virtualbox-ext-pack
~~~

Or, for Arch-Based Distributions:

~~~ shell
$ yay -S virtualbox-ext-oracle
~~~

Read the VirtualBox Extension Pack Personal Use and Evaluation License and select Ok to confirm you understand. The VirtualBox Extension Pack enhances your VM by adding USB2&3 support, remote desktop, and encryption.

<strong>Arch-Based Distributions</strong> will need to manually load VirtualBox Kernel Modules.

To automatically load these modules (vboxdrv), we need to create a new file "virtualbox.conf" in the /etc/modules-load.d/ directory.

~~~ shell
sudo vim /etc/modules-load.d/virtualbox.conf
~~~

Then, ESC+I and type "vboxdrv" and ESC+:wq to save and exit.

Finally, add your login user to the vboxusers system group. Doing so lets your login user use VirtualBox and all of its features. Otherwise, you will see permission errors whilst using VirtualBox.

~~~ shell
$ sudo usermod -aG vboxusers $(whoami)
~~~

For these changes to take effect, reboot your computer.

~~~ shell
$ sudo reboot
~~~

#### Creating the VM
Open your VirtualBox interface, click on New from the top left corner and in the Create Virtual Machine window give your VM a name, select BSD as its type and FreeBSD(64-bit) as its version.

From there, adjust the Memory Size and create a Hard Disk for your VM.

For further customization, you can go into the VM's settings and adjust everything from processors, display, and networking.

### <strong>Setting up on Windows</strong>

#### Downloading VirtualBox
[Virtualbox](https://www.virtualbox.org) is a commonly used Virtual Machine Manager, it is great for both Linux and Windows due to its compatibility, performance and features.

For your VM to work correctly, you will need to enable the VT-x/VT-d extension for Intel Processors, for AMD you will have to enable AMD-v/SVM.

[Download VirtualBox Here](https://www.virtualbox.org/wiki/Downloads)

#### Creating the VM

Open your VirtualBox interface, click on New from the top left corner and in the Create Virtual Machine window give your VM a name, select BSD as its type and FreeBSD(64-bit) as its version.

From there, adjust the Memory Size and create a Hard Disk for your VM.

For further customization, you can go into the VM???s settings and adjust everything from processors, display, and networking.
<br>
<br>