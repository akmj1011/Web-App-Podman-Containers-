# Deploying A Web App On A Nginx Server Using Podman Containers #

## PODMAN INSTALLATION ##
 	 	 	 	 	 	 	 	 	 	 	 	      
$ sudo dnf install podman 	 	 	 	 	 	 	 	 
 	               
 
 	                                                                                                                                      
## PODMAN CONFIGURATION ## 	 	 	 	 	 	 
 	 	    	 	 	 	 	 	 	 	 	                   
$ podman version 	 	 	 	 	 	 	 	 	 
 	 
  
## PULLING A CONTAINER IMAGE ## 
$ podman pull nginx  	 
 	 	 	 	 	 	 	 	 	 
  
 
 
 
## RUNNING THE WEB SERVER ##
$ podman run -d -p 8080:80 nginx 
  
## STATUS OF NGINX CONTAINER ## 
$ podman ps 
  
## VERIFICATION OF WEB SERVER (NGINX) CONTAINER ## 
$ curl -k http://localhost:8080 
  
 
 	 	 	 	 	 	 	 	 	 	 	 	 
## ALLOWING PORT 8080 THROUGH FIREWALL ## 
$ sudo firewall-cmd --permanent --add-port=8080/tcp --add-port=80/tcp                                                                $ sudo firewall-cmd –reload 
 
 
  
## CUSTOMIZING THE WEB SERVER ##
### DIRECTORY CREATION ###
$ mkdir html_files 	 	 	 	 	 	 	 	 
 
  
### HTML FILE CREATION ###	 	 	 	 	 	 	 	 	      
$ vim html_files/index.html 	 	 	 	 	 	 	 
 
  
### HTML FILE ###
```cadence 	 	 	 	 	 	 	 	 	 	            
<!DOCTYPE html> 
<html lang="en"> 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <title>My Website</title> 
</head> 
<body> 
    <header> 
        <h1>Welcome to My Website</h1> 
    </header> 
    <nav> 
        <ul> 
            <li><a href="#">Home</a></li> 
            <li><a href="#">About</a></li> 
            <li><a href="#">Services</a></li> 
            <li><a href="#">Contact</a></li> 
        </ul> 
    </nav> 
    <main> 
        <section> 
            <h2>About Us</h2> 
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p> 
        </section> 
        <section> 
            <h2>Our Services</h2> 
            <ul> 
                <li>Service 1</li> 
                <li>Service 2</li>                 <li>Service 3</li> 
            </ul> 
        </section> 
        <section> 
            <h2>Contact Us</h2> 
            <p>Email: info@example.com</p> 
            <p>Phone: 123-456-7890</p> 
        </section> 
    </main> 
    <footer> 
        <p>&copy; 2024 My Website. All rights reserved.</p> 
    </footer> 
</body> 
</html>
```
## REMOVING EXISTING CONTAINER ##
$ podman ps 	 	 	 	 	 	 	 	 	 	 
$ podman stop cool_grothendieck; podman rm e92bf61f9b8a 
  
## MOUNTING NEWLY CREATED HTML FILE ## 
$ podman run -d -p 8080:80 -v $(pwd)/html_files:/usr/share/nginx/html:Z nginx 
 
 
 	 	 	 	 	 	 	 	 	 	 	 
 	 	 	 	 	 	 	 	 	 	 	              
## CHECKING THE STATUS OF THE CONTAINER ##  	 	 
 	 	 	 	 	 	 	 	 	 	                          
$ podman ps 	 	 	 	 	 	 	 	 	 
 
 
 	 	 	 	 	 	 	 	 	 	 	              
## VERIFICATION OF THE WEB SERVER ## 	 	 	 	 
 	 	 	 	 	 	 	 	 	 	 	 	      
$ curl -k http://localhost:8080 	 	 	 	 	 	 	 
 
 



