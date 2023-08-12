# cloud_class_lab1

Cloud Class Lab 1

Note: In this lab we will get familiar with the concept and technology of virtualization locally and on cloud. We will set up a virtual machine and use it to access our server remotely from our system. We will then explore the ease and facility of serverless architecture.

Tools:
- PC: minimum capacity for 4GB Ram Core i5 or i7 and at least 10GB storage to spare (Windows, Linux, MAC)
- VMPlayer
- Ubuntu Desktop
- DigitalOcean Droplets
- DigitalOcrean Apps
- Python3
- Flask
- GitHub

Only do what you are comfortable with. A credit card is needed to use Digital Ocean. You are responsible of your own finances, machine, accounts, and actions. If you have a question, ask during class or email instructor@minuteschool.com

****************************************************************************************

# Part I: Create an Ubuntu Virtual Machine

- Download and install vmplayer https://kb.vmware.com/s/article/2053973
- Download Ubuntu Dekstop ISO file https://ubuntu.com/download/desktop

- Create VM: https://youtu.be/9rUhGWijf9U?t=134

*configurations and installations will vary depending what machine you have*

- Test and confirm machine can run

Noe: always good practice to run a
`$ sudo apt-get update`
and 
`$ sudo apt-get upgrade`


****************************************************************************************

# Part II: Create a Digital Ocean Droplet

- create a digital ocean account: https://cloud.digitalocean.com/registrations/new

- create a droplet: https://docs.digitalocean.com/products/droplets/how-to/create/

****************************************************************************************

# Part III: Connect to Droplet passwordless with SSH keys

- Initial server setup to create new user and set firewall: https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04

- Add user with admin privileges
  `adduser [user]`
  `usermod -aG sudo [user]`
  
- On local machine create ssh keys to access remotely with openssh and share ssh keys prior to that ensure OpenSSH is allowed:
  `ufw enable`
  `ufw status`
  `ufw allow OpenSSH`
https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/openssh/

https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/to-existing-droplet/

Additional reading:
- https://blog.invgate.com/what-are-ssh-keys#:~:text=An%20SSH%20key%20is%20used,encrypted%20using%20the%20public%20key.

- https://www.simplilearn.com/tutorials/cryptography-tutorial/aes-encryption

****************************************************************************************

# Part IV: Deploy a python app

# Build locally on to test off cloud

- create a directory called myapp:https://linuxize.com/post/how-to-create-directories-in-linux-with-the-mkdir-command/

- create a python vm in the directory myapp: https://realpython.com/python-virtual-environments-a-primer/

- git init the directory myapp: https://www.datacamp.com/tutorial/git-push-pull

- git pull from: https://github.com/quirozity/DigitalOceanDemo.git

- install pip and flask dependencies:

`$ sudo apt-get install python3 python3-pip python3-venv`
`$pip install Flask`

*most likely pyhon3 is already installed* 

for flask app from myapp run
`$ export FLASK_APP=app.py`
`$ flask run`

if when running flask it gets a used port: https://stackoverflow.com/questions/41150975/how-to-display-list-of-running-processes-python
identify the taks with: 
`$ ps -ef | grep python`
find the flask taks then kill with"
`$ sudo kill -9 [task#]` 

- test running app on local machine

# Build app on cloud
 
 * we will anndon the droplet and use the app service instead of the droplet to go serverless. If we wan to build it on the droplet it will require more work: https://tecadmin.net/deploying-flask-application-on-ubuntu-apache-wsgi/ *

- deploy on digital ocean apps with gunicorn https://docs.digitalocean.com/tutorials/app-deploy-flask-app/
- Try deploying the ccs quiz app: https://github.com/quirozity/quizapp1.git
- Remember to update the run command with `gunicorn --worker-tmp-dir /dev/shm app:app`

****************************************************************************************

# Part V: Play

Review Digital Ocean's Cloud Guide and try any one of their demos: https://www.digitalocean.com/community/tutorial-series/getting-started-with-cloud-computing

For example, you can make your own VPN server and your virtual machine: https://www.digitalocean.com/community/tutorials/how-to-set-up-and-configure-an-openvpn-server-on-ubuntu-22-04
