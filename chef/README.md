chef-bootstrap
==============
Bootstrap chef from your own http server.
Intended to be used with vagrant/test-kitchen.

Requirements
------------
A web server that you can access from your vagrant VM.  I use nginx running on my workstation.

The chef .rpm and/or .deb packages from opscode.

Usage
-----
Put the 'chef' directory and subfolders on your webserver.  The ubuntu/nginx root is at /usr/share/nginx/html.
Download the chef-11.12.2-1.el6.x86_64.rpm and chef_11.12.2-1_amd64.deb from opscode.
Drop those in the 'el' and 'ubuntu' directories, accordingly.

In your .kitchen.yml or .kitchen.local.yml add the following line in the 'provisioner' section:
```chef_omnibus_url: "http://192.168.250.1/chef/install.sh"```

Change the IP address to the IP of the vmnet device serving your vagrant VMs if necessary.

Change the IP address in install.sh on line 450 - ```metadata_url=``` under ```"chef")```.

Also change the url the index.html file in both 'el' and 'ubuntu' subdirectories.

If you decide to use a different chef package other that 11.12.2-1 you will need to edit the el/index.html and ubuntu/index.html files with the new package name, md5, and sha.

Authors
-------
Opscode - see install.sh