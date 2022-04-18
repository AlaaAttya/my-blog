### Used theme
https://tianqi.name/jekyll-TeXt-theme/docs/en/quick-start


### Deployment
1. Create a new remote machine
2. ssh your remote machine and add your public key to the authorized keys to `~/.ssh/authorized_keys`
3. Create a new ssh user `deployer`
`adduser deployer`
`usermod -aG sudo deployer`
`ufw app list`
`ufw allow OpenSSH`
`ufw enable`
`ufw status`
4. Enable sudo to the newly created user `deployer` by running the following command
 `sudo visudo` then add this line to the end of the file `deployer ALL=(ALL) NOPASSWD: ALL`
5. Add your ssh private key to the server (other alternative is to create a deployment key from github). the is should be added to this file `~/.ssh/id_rsa` 
5. `ansible-playbook ansible/deploy.yaml`


For better performance of your server try to remove any unused software/package that is consuming resources. 

###### Removing snap and snapd
```
sudo rm -rf /var/cache/snapd/
sudo apt autoremove --purge snapd gnome-software-plugin-snap
rm -fr ~/snap
```

After successfully uninstalling snapd, make sure that it doesn't get installed again:
`sudo apt-mark hold snapd`

Credit goes to this super amazing response: https://askubuntu.com/a/1114686 

