# Documenting Project 8

Step 1: Launched an Ubuntu ec2 and named it load balancer
Step 2: Opened tcp port 80 on load balancer 
![tcp port 80 opened](./Project-8%20images/tcp%20port%2080%20opened%20on%20lb.PNG)
Step 3: Installed apache load balancer on lb and configured it to point incoming traffic to the webservers
`sudo apt update`
`sudo apt install apache2`
![apache installed](./Project-8%20images/apache2%20installed.PNG)
`sudo apt-get install libxml2-dev`
![apache dependency](./Project-8%20images/apache2%20dependency%20installed.PNG)

`sudo a2enmod rewrite`
`sudo a2enmod proxy`
`sudo a2enmod proxy_balancer`
`sudo a2enmod proxy_http`
`sudo a2enmod headers`
`sudo a2enmod lbmethod_bytraffic`

`sudo systemctl restart apache2`
`sudo systemctl status apache2`

`sudo vi /etc/apache2/sites-available/000-default.conf`
![lb configured](./Project-8%20images/lb%20configured.PNG)

`sudo systemctl restart apache2`
Step 4: Verified my configuration
[accessing lb from browser](http://18.215.178.187/index.php)
![lb accessed from browser](./Project-8%20images/load%20balancer%20accessed%20from%20browser.PNG)
Step 5: Two git terminals were opened for my web servers, and their access log files opened
`sudo tail -f /var/log/httpd/access_log`
![server1 log file](./Project-8%20images/web%20server1%20access%20log%20file.PNG)
![server2 log file](./Project-8%20images/web%20server2%20access%20log%20file.PNG)
Step 6: Browser page (for load balancer) was refreshed severally, and the access log file pages compared
![server1 log file populated](./Project-8%20images/web%20server1%20access%20log%20file%20populated.PNG)
![server2 log file populated](./Project-8%20images/web%20server2%20access%20log%20file%20populated.PNG)
Step 7: Configured local dns name resolution on my load balancer
`sudo vi /etc/hosts`
![configuring dns resolution](./Project-8%20images/ip%20add%20configured%20to%20domain%20name.PNG)
Updating load balancer configuration file
![updating lb config file](./Project-8%20images/updating%20lb%20config%20file%20with%20mapped%20domain%20name.PNG)
Step 8: Web servers accessed locally from load balancer
`curl http://Web1`
![web1 curl from lb](./Project-8%20images/web1%20curl%20from%20lb.PNG)
`curl http://Web2`
![web2 curl from lb](./Project-8%20images/web2%20curl%20from%20lb.PNG)  
