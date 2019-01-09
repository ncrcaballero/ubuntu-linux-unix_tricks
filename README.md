# ubuntu-linux-unix_tricks

Here I will post some problem solutions when developing (in ubuntu/debian/linux/unix) that when searching in google you can not find much info

#### How to Enable automatic Root Login in Ubuntu
tested in ubuntu 16.04, only for testing isolated single-user systems. i know its forbbiden, that why i say its only for testing, greetings.

1. create and enter root password
```
user@ubuntu:~# sudo passwd root
```

2. edit the file with superuser privilegues
/etc/lightdm/lightdm.conf
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
autologin-user=root
autologin-timeout=0
```

3. reboot and there is an error show about tty, you can bypass it by editing the next file, if no error, you are done.
   - enable the view of hidden files, and go to root folder, there, edit .profile file
   
```
# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
  if [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi

if `tty -s`; then
  mesg n
fi
```

4. reboot and done.
 - if u want to start with the greeter and choose the account, add in lightdm.conf `greeter-show-manual-login=true` 


#### More:
[Error 127 when installing package with synaptic or apt-get](https://github.com/ncrcaballero/ubuntu-linux-unix_tricks/blob/master/error-127-dpkg-synaptic.txt)
