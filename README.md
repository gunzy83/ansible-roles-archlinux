ansible-roles-archlinux
=======================

**ansible-roles-archlinux** is a pair of modules for configuration of Arch Linux specific systems. Current roles are:

* pacman - configures pacman options and repos
* pacman-repo - adds a pacman repo (use as a dependecy for other roles)
* pacserve - configures pacserve
* reflector - configures reflector to run periodically as a service
* makepkg - configures makepkg for the system type

Installation
============

Clone the repo:

    $ git clone https://github.com/gunzy83/ansible-roles-archlinux.git ~/projects/ansible-roles-archlinux

Then add the path to your *ansible.cfg* file:

    roles_path = ~/projects/ansible-roles-archlinux

Usage
=====

    ---
    - name: Arch Linux Hosts
      hosts: arch
      become: yes

      roles:
        - pacman
        - reflector
        - pacserve
        - makepkg

Using pacman-repo as a dependency:
    
    ---
    dependencies:
      - { 
        role: pacman-repo, 
        pacman_repo_name: "{{pacserve_repo}}", 
        pacman_repo_server: "{{pacserve_server}}"
      }


Future Plans
============

* Aura install and configuration
* Travis CI tests

License
=======

**ansible-roles-archlinux** is provided under the terms of [The MIT License](http://opensource.org/licenses/MIT)

Copyright &copy; 2015, [Ross Williams](mailto:gunzy83au@gmail.com)


