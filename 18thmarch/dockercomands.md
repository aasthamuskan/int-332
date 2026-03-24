docker pull nginx
docker run -d -p 80.80:80 --name mynginx nginx  //Run an nginx container in background and expose it to my laptop browser”
                                                 //purspose of -d is -d ka use container ko background (detached mode) me run karne ke liye hota hai, taaki terminal free rahe. or stating the egine
                                                //purpose of -p is defining the port no and networking
                                                //--name for defining the port name
                                                //iamge is in nginx

doker ps //give the information related to ps
docker stop mynginx    //stop the container
docker start containerid //for starting the container

docker rm -f mynginx //rm is remoing the container
                    // forced remove (also remove if ots running)

doker rmi nginx


//docker exec -it<container id> bash ->Opens terminal inside a runnig container

docker logs<container id> ->show container output
docker inspect<container id> ->display details configration in json format


------volume commans--------

docker volume create myvolume  -create a persistent storage volume
docker volume ls -lists all the volume
docker volume inspect myvolume -shows volume details
docker volume rm 