vagrant-lamp-ansible
----------------------

This is a simple recipe for *vagrant* that sets up an Ubuntu virtual machine including common daemons and tools required for PHP web development. Specifically it automatically installs:

- Ubuntu 12.04 (precise), 64bit version
- PHP 5.5
- MySQL
- phpMyAdmin
- beanstalkd
- memcached
- asset comilation tools
    - compass
    - node.js (for asset compilation)

This recipe uses the excellent `ansible` as the provisioning tool for *vagrant*. It does not use vagrant's `ansible` plugin, however, because it controls the VM from the outside. Instead, this recipe runs `ansible` in its "local" mode (using `-c local`). See `ansible/provision.sh` for details.

To get started, install

- Vagrant (http://www.vagrantup.com/)
- VirtualBox (https://www.virtualbox.org/)

preferably in their latest versions from the web sites.

Then clone this repository to a local directory. After changing into the directory, run:

    vagrant up

This should download, run and provision the virtual machine.

If something goes wrong, have a look at `ansible/playbook.yml`, which contains the provisioning recipe. You can re-provision the VM using:

    vagrant provision

After bringing up the virtual machine, open this url in your browser: http://localhost:9888/. You should be greeted by the `phpinfo()` output from public/index.php.

When you're done playing with the VM, you can delete it:

    vagrant destroy
