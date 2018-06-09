# Archsible
![Travis build status](https://travis-ci.org/DasFranck/Archsible.svg?branch=master)

This is an ansible deployment playbook used for setup my archlinux workstations.  
This playbook is tested via Travis-CI using a docker container without aur flagged steps, the Dockerfile is in the travis folder.

If you are looking for my dotfiles, [it's here](https://github.com/DasFranck/DasDotFiles).

### Some example commands
- Launch ansible playbook for laptop  
`ansible-playbook -v ./playbook.yml -i ./localhost`

- Launch ansible playbook for desktop  
`ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop"`

- Launch ansible playbook for desktop without aur  
`ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop,aur"` 