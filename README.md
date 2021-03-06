[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![CodeFactor](https://www.codefactor.io/repository/github/fresearchgroup/collaboration-system/badge)](https://www.codefactor.io/repository/github/fresearchgroup/collaboration-system)
[![Build Status](https://travis-ci.org/fresearchgroup/Collaboration-System.svg?branch=master)](https://travis-ci.org/fresearchgroup/Collaboration-System)

COLLABORATION SYSTEM

        Requiremnets -

                Django - 1.11.7 LTS
                python - 3.6
                Django Rest API
                Mysql

        Django pakages installed - 
		
		Django Rest Framewo
		Widget Tweaks
		Django Reversion
		Reversion Compare
		MPTT
		Haystack
		Django Machina
		Django-cors-headers
		Django-role-permission
		Django_comments_xtd
		Django_comments
		Django_wiki
		PyEtherpadLite

For development installation - 

  1. Install virtualenv 

	        sudo pip3 install virtualenv 

  2. Clone the project from github

           git clone https://github.com/fresearchgroup/Collaboration-System.git 

3. Create a virtual env --- 

		 virtualenv collab -p python3 

4. Activate the virtual environment -- 

	      source collab/bin/activate 

 5. Install the requirements.txt -- 

	       pip3 install -r Collaboration-System/requirements.txt

5. Install mysql server --

            $sudo apt-get update
            $sudo apt-get install mysql-server
            $sudo apt-get install libmysqlclient-dev
            $mysql -u root -p
            
            Enter password=root

	    mysql> create database collaboration;
            mysql> use collaboration;
            mysql> source collab.sql   
            

6. Create a .env inside CollaborationSystem and paste the following -

            sudo nano .env
            
                SECRET_KEY=myf0)*es+lr_3l0i5$4^)^fb&4rcf(m28zven+oxkd6!(6gr*6
                DEBUG=True
                DB_NAME=collaboration
                DB_USER=root
                DB_PASSWORD=root
                DB_HOST=localhost
                DB_PORT=3306
                ALLOWED_HOSTS= localhost
                GOOGLE_RECAPTCHA_SECRET_KEY=6Lfsk0MUAAAAAFdhF-dAY-iTEpWaaCFWAc1tkqjK
                EMAIL_HOST=localhost
                EMAIL_HOST_USER=
                EMAIL_HOST_PASSWORD=
                EMAIL_PORT=25
                EMAIL_USE_TLS=False
                DEFAULT_FROM_EMAIL=collaboratingcommunity@cse.iitb.ac.in
                SOCIAL_AUTH_GOOGLE_OAUTH2_KEY=735919351499-ajre9us5dccvms36ilhrqb88ajv4ahl0.apps.googleusercontent.com
                SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET=I1v-sHbsogVc0jAw9M9Xy1eM
                APIKEY=
	            NODESERVERURL=Your IP address
				 NODESERVERPORT=9001

            
7.Clone etherpad-lite from https://github.com/ether/etherpad-lite

		git clone https://github.com/ether/etherpad-lite

8. Clone the following directory and place the contents of `etherpad-lite` folder in `etherpad-lite(Node Application)` root directory.

		git clone https://github.com/fresearchgroup/Community-Content-Tools/
		
9. Install Node JS from https://nodejs.org/

10. Run the following commands
	
		./bin/run.sh

11. Place the `APIKEY` in `.env` folder of `Collaboration-System`

		cat APIKEY.txt
		cd path/to/collaboration-communities
		vi .env
			
9. Do all the migrations going back to `Collaboration Communities` directory--

	      python3 manage.py migrate 

10. Runserver --

	      python3 manage.py runserver  
                
For manual installtion -- https://fresearchgroup.github.io/docs-collaboration-system/

For automated installation using nginx and gunicorn- https://github.com/abhisgithub/django-nginx-installation-script


Steps for Docker -- 

1. Install Collaboration Communities from https://github.com/fresearchgroup/Collaboration-System/
		
		git clone https://github.com/fresearchgroup/Collaboration-System/
		
2. Clone etherpad-lite from https://github.com/ether/etherpad-lite

		git clone https://github.com/ether/etherpad-lite

3. Clone the following directory and place the contents of `etherpad-lite` folder in `etherpad-lite(Node Application)` root directory.

		git clone https://github.com/fresearchgroup/Community-Content-Tools/
		
4. Install Node JS from https://nodejs.org/
5. Install Docker from https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository
6. Install Docker-Compose form https://docs.docker.com/compose/install/
7. In the `etherpad-lite` folder run the following commands

		sudo docker build -t etherpadlite .
		
8. Setup MySQL Database in Docker
  		 
		 docker-compose build

		 docker-compose up db

		 docker exec -i <container-image-name> mysql -u<username> -p<password> django < collab.sql

9. Setup environment for Django app.
 
		sudo docker run -p 9001:9001 etherpadlite 
		sudo docker ps
		
   Using the container image from above
	
		sudo docker exec -i <image-name> cat APIKEY.txt
	
11. Place the above string in the `.env.docker` in `Collaboration-Communities` folder for `APIKEY` variable.
12. Place the `IP address` of docker in the `.env.docker` in `Collaboration-Communities` folder for `NODESERVERURL` variable.
13. The run the following commands inside the repository --
 

		 docker-compose run web python manage.py migrate

		 docker-compose run web python manage.py createsuperuser

		 docker-compose run web python manage.py loaddata workflow roles faq

		 docker-compose up
		 
