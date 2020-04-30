##this docker compose file contain two container one for wordpress web app and the other one for mysql db <br />
i don't need to start wordpress webapp untill to make sure that mysql db container started and healthy  <br />
i have here two question <br />
1st one : i need to depend on more than one test to make sure that mysql is healthy, in this example i used the below two tests <br />

	test: mysqladmin ping -h 127.0.0.1 -u $$MYSQL_USER --password=$$MYSQL_PASSWORD >> /var/lib/mysql/health.log 
        test: ls -ld /var/lib/mysql/wordpress >> /var/lib/mysql/health.log 
following the file log "everytime i got the result only for the second test not both" why?, and if i should use only one test how the syntax will be to include more than one command ? <br />

2nd one : the docker-compose file doesn't start in the current status because of the below lines, you will got error while starting and if you make them hashed it will be started successfully <br /> 
so what is the wrong with them ? <br />
 
		depends_on:
      			db:
      			condition: service_healthy

