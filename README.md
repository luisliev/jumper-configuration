# Jumper Configuration on Amazon Linux
This is a repo to document the configuration of a different port for the ssh

1.  Create the jumper instance
2.  Connect to the instance on port 22
3.  Promote to root and edit /etc/ssh/sshd_config
4.  Edit line 17 (usually 17) #port 22. You'll need to un-comment the line and change the port to whatever you like. Example: port 2222
5.  Save changes and exit
6.  Restart sshd

```bash
/etc/init.d/sshd restart
```
If error try:

```bash
/etc/init.d/network restart
```

7.  Make sure the new port is added to the INBOUND rules for your security group. The example above I would add a new TCP connection for 2222 for 0.0.0.0/0, after testing is over I would then lock down the source address to something more specific. 
8.  Connect to your instance on port 80. That's all!
