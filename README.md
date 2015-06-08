# SystemController4
This is the working code of the system controller build for industrial systems management.

# Requirements:
PyThon Dev libraries


# Install the code on a BeagleBone Black and get the site running

Ssh in:
	Plug in BeagleBone via USB
	If needed  ->  ssh-keygen -f "/home/dsmurl/.ssh/known_hosts" -R 192.168.7.2

	or 

	ssh root@192.168.7.2

Change root to password:

	ssh as root then:
	:> passwd
		

Add a personal user/password and add them to the admin group.  admin is needed 
to have sudo rights:

	:> adduser USERNAME
	:> usermod -a -G admin USERNAME

Make the networking through the router work.  Change the networking over to primary 
eth0 availability by editing /etc/network/interfaces.  Edit the primary section to 
look like this:

	# The primary network interface
	allow-hotplug eth0
	iface eth0 inet static
	    address 192.168.0.50
	    netmask 255.255.255.0
	    gateway 192.168.0.1

Set the corret time:

	:> sudo ntpdate pool.ntp.org

Install the python pin IO library dependancies.  Turns on and off pins, reads analog input 
pins from python:

	:> sudo apt-get update
	:> sudo apt-get install build-essential python-setuptools python-pip python-smbus

Install the IO lib through pip:

	:> sudo pip install Adafruit_BBIO

May result in:

	Requirement already satisfied (use --upgrade to upgrade): Adafruit-BBIO in 
	/usr/local/lib/python2.7/dist-packages
	leaning up...

Test your install with:

	:> sudo python -c "import Adafruit_BBIO.GPIO as GPIO; print GPIO"

Should result in:

	<module 'Adafruit_BBIO.GPIO' from '/usr/local/lib/python2.7/dist-packages/Adafruit_BBIO/GPIO.so'>

Install the code.  Go to github.com and get the current code or prefered revision, like:

	:> git clone https://github.com/dsmurl/SystemController4.git

Install the gevent dependancies:

	:> sudo pip install gevent
	
Run the code and check the site:

	:> cd SystemController4
	:> python wsgi.py

	

