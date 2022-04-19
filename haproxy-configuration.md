haproxy configuration
haproxy configuration using the purpose for load balancing and high availability and proxy functionality
haproxy is particularly suited for very high traffic websites and is therefore often used to improve web service reliability and performance for multi-server configurations

Installing haproxy using below commands
sudo add-apt-repository ppa:vbernat/haproxy-1.7
update our source list using below command
apt update
haproxy installation using below command
sudo apt install -y haproxy
version checking below command
haproxy -v
Configuring Load balancer on Layer 1
sudo vi /etc/haproxy/haproxy.cfg
update this below file to configuration
frontend http_front
   bind *:80
   stats uri /haproxy?stats
   default_backend http_back

backend http_back
   balance roundrobin
   server <server1 name> <private IP 1>:80 check
   server <server2 name> <private IP 2>:80 check
  layer 4 load balancer with a front-end name http_front listening to the port number 80, which then directs the traffic to the default backend named http_back
  The additional stats URI /haproxy?stats enables the statistics page at that specified address.
    
  After making the configurations
  sudo systemctl restart haproxy
  Testing the setup
    
 http://<public IP>/haproxy?stats
