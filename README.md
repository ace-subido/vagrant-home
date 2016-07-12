# vagrant-home

Vagrant + Ansible script to boot up a basic development box

This creates a local VM where you can put in your projects. It installs the following:

- zsh, with tmux and fasd_cd
- open-jdk
- rvm
- and you can easily add other stuff you can think of...

### Usage

1. Add a `/mnt` folder in this repository, this is the folder that'll be synced in the VM.
2. Make sure that Vagrant and Ansible is installed in your computer
3. Add an ubuntu/trusty32 via `vagrant box add ubuntu/trusty32` (if you have a 64-bit machine, do `vagrant box add ubuntu/trusty64`)
4. Run `vagrant up`
5. Go inside the `ansible` folder and then run `ansible-playbook -i hosts setup_dev_box.yml -u vagrant -k -vvvv`

### Development Workflow

- Synced folder is locally accessible in the `/mnt/` folder.
- Inside the VM, you can see them under `/home/vagrant/src/`.
- In your local machine, fire up your text editor and work on the projects as usual.
- See the errors and etc.

### Why?

1. You can quickly move into a new machine if your laptop breaks down.
2. Quickly on-board a new developer.
3. Idempotency in development environments: to remove the "It works on my machine" problem.
4. Avoid messing up your **local machine** further: You work on a clean machine that only contains things that are related for your development


