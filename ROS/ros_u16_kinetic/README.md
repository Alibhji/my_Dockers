# ROS Kinetic with SSH

 

Build docker file:
```
sudo docker  build  -t "alibhji/ros_u16:kinetic" .

``` 
Run it:
``` 				
nvidia-docker run -ti --rm -p 1022:22 alibhji/ros_u16:kinetic
```


To ssh to the docker open a new terminal and run:
```
ssh root@localhost -p 1022
```

Error in ssh connection:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Please contact your system administrator.
Add correct host key in /home/scott/.ssh/known_hosts to get rid of this message.
Offending key in /home/scott/.ssh/known_hosts:15
RSA host key for 1.2.3.4 has changed and you have requested strict checking.
Host key verification failed
```

solution --> [https://support.rackspace.com/how-to/ssh-remote-host-identification-has-changed/]