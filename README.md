Playbooks for setup and teardown Minecraft server on Digital Ocean.

# Run

1. Login to DO administration panel and run droplet:
    - Ubuntu 14.04.3 x64
    - $10/m0 (1 GB/1 CPU)
    - Amsterdam 3
    - [ ] Michal SSH key
    - Hostname: minecraft
    - Create!

2. Find out IP address of newly created Droplet and create file `do/hosts` in
   form like:

    aaa.bbb.ccc.ddd

    [minecraft]
    aaa.bbb.ccc.ddd

3. Bootstrap Minecraft server and run it:

    ansible-playbook minecraft_do.yml -i do/hosts

   During this step your last saved Minecraft data will be copied to remote
   server. If you don't want it, run playbook like:

    ansible-playbook minecraft_do.yml -i do/hosts --skip-tags=data


# Stop

After game is over, archive data dir and stop Minecraft:

    ansible-playbook minecraft_do_stop.yml -i do/hosts

Don't forget to destroy Droplet on DO admin panel!


# TODO

- schovat ansible do docker kontose (protoze zavisim na 1.7.4 verzi a ta za 
  par dni nebude)
- mozna to upgradnout i na 2.0 verzi ansiblu...
