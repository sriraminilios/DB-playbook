### How to connect to EC2 servers from WSL 

1. Download the private key file and store it a centralized directory.
2. Change the permission of th keyfile.
```bash
chmod 400 "keyfile.pem"
```
3. Create a bash script to store the ssh command.
```bash
vi server-name
```

```bash
#!/bin/bash
ssh -i "keyfile.pem" username@ec2-00-00-00-00.xx-south-0.compute.amazonaws.com
```

This ssh command can be obtained from AWS EC2 instance console.

5. Change the script to be executable.

```bash
chmod u+x server-name
```