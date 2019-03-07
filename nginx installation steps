update your system
 # yum update
Download Nginx latest version. version we use here is :

download latest version of nginx from http://nginx.org/en/download.html website

 # cd /opt
 # wget http://nginx.org/download/nginx-1.15.4.tar.gz
 # tar -zxvf nginx-1.15.4.tar.gz
 # mv nginx-1.15.4 /opt/nginx 
In order to compile our source code we need to install dependences.
  # yum groupinstall "Development Tools"
  # yum install pcre pcre-devel zlib zlib-devel openssl openssl-devel
Run /opt/nginx/configure file with below parameters
	# cd /opt/nginx 
	# ./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf  --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-pcre --pid-path=/var/run/nginx.pid --with-http_ssl_module
Now compile and install nginx
 # make 
 # make install 
Check nginx version and start service to use.
 # nginx -V
 # nginx 
Setup nginx as a system servicecreate a file /lib/systemd/system/nginx.service and copy below URL content into that and modify according to your file path locations.
Ref URL : https://www.nginx.com/resources/wiki/start/topics/examples/systemd/

# vi /lib/systemd/system/nginx.service
copy below contant in to nginx.service file by changing PIDFile location

[Unit]
Description=The NGINX HTTP and reverse proxy server
After=syslog.target network.target remote-fs.target nss-lookup.target

[Service]
Type=forking
PIDFile=/var/run/nginx.pid 
ExecStartPre=/usr/bin/nginx -t  
ExecStart=/usr/bin/nginx 
ExecReload=/usr/sbin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
Start nginx and test
# systemctl start nginx
# systemctl enable nginx
# ps aux | grep nginx
