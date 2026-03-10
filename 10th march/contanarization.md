explain what is contanarization?
exaples is pg living 
what exactly containers do
    -they dont carry an entier os. they use bare minimum os.
    -share the host os and only bring what the application need
    -they strt in seconds.also consume minimal resources.
    -can run dozons even hundreds - on the same machine.
    -earlier the app were monolithic , so physical serever were apt(in the form of apply dependencies),
    - later there were components split like backeend ,frontend ,db,so vm took care of hosting;
    - now most of application turns into microservices ,here docker(contanarization tool) will serve the purpose
    - also the prpbality  problem is also solved using the conatiner.
    
------------------need of containers-----------


app1    app1    app1         
bins/libs --   --        app1    app1    app1        
guest os  --    --       bins/libs --   --   
  hyerviser                  docer engine 
  host os                      os
  infrastructure             infrastructure
