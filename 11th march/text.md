need of container

types of container runtime
1. high level runtimes
   1. used by user and developers
   2. eg kubernetees





2.low level runtimes
    1.directly itrcats with the -linux kernal 
                                -namespaces(purpose of namespces is a standrad lib basically some special files which are predefine which we use for our project   eg -p its port number ,-t ,-v,etc ) //perocess isolation is achieved using linux namespaces

                                -cgroups
    2.



           ------------//real world analogy//-------------- 

container image - paked lunch box
container runtime-person who open it ,serves food and clean up


//some more points
-containers isolate the process
they can get the isdea of presence using networking



namespace used in cintainer

1.pid namespace(process isolation)
    . each container has its own process tree
    . process id inside container strt from 1
    . a container cannot see host or other container process

senario - web applicaion container


2.network namespace 
    each container gets
     -its own ip adress
     -its own ports
    . container can run app on the same port withour conflict 
  example-nagix

3.mount namespace 
    .each container has its own filessystem view
    . file chanegs inside container do not affect hsot

4.uts namespace 
    .allow each container to have its own hostname
5.user namespace (advance)
    .maps container used to non-root useer on host
    . improve security

