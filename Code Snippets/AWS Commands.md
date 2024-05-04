
Commands used in the AWS ec2 server using putty

### 1.AWS AMI Apache vhost config path
AWS Apache virtual host path `/etc/httpd/conf/httpd.conf`

### 2.AWS AMI Apache service commands
Commands to control the Apache server in AWS Amazon Linux ec2

To start the Apache service:
```sh
sudo systemctl start httpd
```

To restart the Apache service:
```sh
sudo systemctl restart httpd
```

To check the Apache service status:
```sh
sudo systemctl status httpd
```

### 3.PM2 commands in node server

To add a next js app to pm2 service list:
```shell
pm2 start npm --name app-name -- run start -- -p 3000
```

