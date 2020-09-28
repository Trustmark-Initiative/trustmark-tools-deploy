
# Trustmark Policy Authoring Tool - Deployer
This repository holds the Docker configuration to standup a copy of the tool for anyone interested in running their own copy of the TPAT.

## How to Use

1. Clone this repository onto the server you intend to run docker (or more specifically docker-compose, you could deploy your custom docker image to a remote location).

2. You will need to install docker-compose: https://docs.docker.com/compose/
   - This is available within most Linux distributions as a package and doesn't need to be installed via this website.

3. Update ``tpat_config.properites``.  While not all fields must be updated, the following should be:
    * ``tf.base.url`` - This must be the URL where you intend to host this tool (it could be things like http://localhost:8080/tpat/ if you intend to simply run it locally).
    * ``tf.org.user`` and ``tf.org.pswd`` - The username and password used to login.  This software is functionally a two user application.  One user is an admin that can upload, edit, and manage data.  The other user is simply the public and doesn't login at all.  When using this software in a private environment, the user and password matter very little, but it's imperative that an appropriately strong username and password is specified if hosting the site at a publicly accessible URL. 
    * ``tf.org.organization`` - This is the title of the tool as seen on pages and within browser windows.  It's recommended that the title be something like "Your Org's TPAT". 

    There are numerous other fields that can editted to set default values, but only the above are absolutely critical to get started with using the tool.

4. If you are hosting the TPAT at a url that doesn't include a "/tpat/" at the end of the URL, you will need to update the ``Dockerfile`` to change the path location the tool runs at within docker.  The following four lines must be updated so that the path in the ***base.url*** matches the sub-directory of webapps where the tool is posted.  In the default files all four of these paths are **tpat**):

> RUN unzip -d /usr/local/tomcat/webapps/**tpat** /tmp/tpat.war   
> COPY tpat_config.properties /usr/local/tomcat/webapps/**tpat**/WEB-INF/classes   
> COPY ./images/banner.png /usr/local/tomcat/webapps/**tpat**/assets/tmi-header-6c6f1a43dfc14aaab266274bdaac780b.png
> COPY ./images/favicon.ico /usr/local/tomcat/webapps/**tpat**/


5. You may wish to update the header/banner image of the tool or the favorite icon.  Do this by simply replacing the ``banner.png`` or the ``favicon.ico`` file within the images directory.  

6. Build the docker image by running ``docker-compose build`` from the directory containing this project.

7. While the method for running the tool may vary if running a public facing site, if running locally, you can typically start it up by simply running ``docker-compose up -d`` from the directory you downloaded this repository.

8. Typically docker is proxied with a webserver that will provide TLS if you intend for your TPAT to be Internet accessible.  There is plenty of documentation available on how to do this, but if you need help with this, you can contact help@trustmarkinitiative.org.

