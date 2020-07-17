# Terraria Server Setup

This uses [kaysond's docker-compose file](https://github.com/kaysond/docker-terraria) to setup a Terraria server in an AWS EC2 instance. 

Environment:
* minimum t2.small ec2 (will not work with free tier t2.micro)
* Ubuntu 18.04
* Security group must have the following inbound rule:
    * Type: Custom TCP
    * Port range: 7777
    * Source: {IP of all players}

Installation:
* ssh into ec2
* `git clone https://github.com/dc4505/terraria-setup.git`
* `cd terraria-setup`
* `./start.sh`
* locate the desired Terraria world file on local machine
*  `scp` it to `/home/ubuntu/world/.` on the ec2
* back on the ec2 instance, rename the copied world file to `World.wld`
    * alternatively, in `~/config/serverconfig.txt` you can change `world=/world/World.wld` to `world=/world/{your-world}.wld`
* `cd ~/terraria-setup`
* `docker-compose up`
* If everything is done correctly, you should see:
`Listening on port 7777`
* Once you see that, you can connect to the server in Terraria using the IP address 
