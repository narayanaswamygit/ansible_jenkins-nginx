Deploy Jenkins CI server with ansible
=====================================
An [Ansible](http://www.ansibleworks.com/) playbook to easily deploy Jenkins CI
servers in [Debian](http://www.debian.org) OSs (Tested on Debian 7.2 _Wheezy_).

Setup description
-----------------
Jenkins is managed by [Nginx](http://nginx.org/) web server, which acts as a
proxy to serve the CI server via port 80. [Iptables](http://www.netfilter.org/projects/iptables/)
ensures that standard Jenkins port 8080 is unreachable from the outside.

Try it out
----------
Want to try the playbook? You can easily set up a VM using [Vagrant](http://docs.vagrantup.com/v2/installation/index.html)
and then run drectly the ansible-playbook command for it:

    vagrant box add debian-7.2 https://dl.dropboxusercontent.com/u/197673519/debian-7.2.0.box
    vagrant init debian-7.2

Now edit the Vagrantfile to include this:

    config.vm.network :forwarded_port, host: 9000, guest: 80

Launch the VM:

    vagrant up

Run Ansible playbook:

    ansible-playbook site.xml

Once finished, check it out in your browser using the localhost port 9000 (the
way to access port 80 of your running VM, remember we configured it before). You
will see the Jenkins dashboard there waiting for new jobs!
