# Shinobi CCTV Docker

Shinobi is an open source CCTV server written in node.js. I've been running it for several years and have yet to find anything as performant as it for the price.

## Getting Started

### Docker-Compose
1. `git clone https://github.com/fahcsim/shinobicctv.git`
2. `cd shinobicctv`
3. Modify the values in `.envShinobi` and `.envMysql` to match your environment
4. `docker-compose up -d`
5. Go to `http://<server-ip>:8080` to see if it's workng
#####  Import existing install
1. If you already have a Shinobi server and want to migrate to this, you can migrate your whole install pretty easily. Start by doing a mysql dump of your existing database
2. Create a directory named "dbDump" under the same directory as the docker-compose.yml file
3. Copy the database dump to the dbDump directory
3. Uncomment the `- ./db/:/docker-entrypoint-initdb.d` line under the volumes secion of the MySql configuration in the docker-compose.yml file
4. The MySQL container will initialize with the SQL dump that you provided. If everything works, it should start right up with the existing users and monitors configured.


### Ansible
1. `git clone https://github.com/fahcsim/shinobicctv.git`
2. `cd shinobicctv`
3. Modify the values in `.envShinobi` ,`.envMysql`,`vars.yml`, and `inventory` files to match your environment.
4. `ansible-playbook -i inventory main.yml` 
5.  Go to `http://<server-ip>:8080` to see if it's workng


#####  Import existing install
1. If you already have a Shinobi server and want to migrate to this, you can migrate your whole install pretty easily. Start by doing a mysql dump of your existing database
2. Create a directory named "dbDump" under the same directory as the docker-compose.yml file
3. Copy the database dump to the dbDump directory
3. Uncomment the `- /srv/shinobi/db/:/docker-entrypoint-initdb.d` line under the volumes secion of the MySql configuration in the main.yml
4. The MySQL container will initialize with the SQL dump that you provided. If everything works, it should start right up with the existing users and monitors configured.
