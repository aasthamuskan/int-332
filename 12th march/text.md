real worlf analogy behind namespaces

basically irts like seprate cabins in a trsin
    - same engine(kernal)
    - diffret passengers
    - no visibility betw cabins



-----------control groups(cgroups) for the resources limits(basically it is a typr of controller)---------------

cgroups are the linux kernal features thet limit , contril and the monitor resources usages of processes.

they ensures -
            -n container can monopolize system resourse(fairness)
            -fair sharing of cpu ,memory and i/o

            **namespace isolates control groups in the form of controler**
----------need of cgroup-----
    without cgrp
        -one container consume all the cpu or ram
        -host and other container could crash


        ------types of resources controlled by cgroups

1.cpu   limit cpu usages
        assign cpu shares
2.memory
    set maximum memort useages
    kill contaner if limit exceeded
3.disk i/o

4.network(indirectly)
        through trafic


real world ananlogy
    basiclly its like a electricity meters in a apartment 
        -each flat - limit
        -one tenant != all power


without cgrpus                                           withcgrps
(problem scenario)                                       (controlled)

       host system                                           host system  
    cpu: 100% | memory:  16gb                         cpu: 100% | memory:  16gb

       container a                                           container a(Cgrp) 
        (no limit)                                             cpu limit : 30%
                                                               ram limit 4 gp










task 1. a company uses containers for microservises. one faulty container crashes the host dur to high memory usages.
        -which container feature was misconfigured or missing?  -kubernetees 
        -which krnal mecanism showuld have preventd this?    c-grps
        -would namespaces alone solve this issues?why?    no (namespaces is in the form of isolation alone cant handle this it do not care about crahing)


task2- a server is running three containers:
        -containersa runs a cpu intensive task
        - container b runs a web server
        - container c runs a database
  - ques. which linux feature prevent container a from consuming all cpu ----cgrp
        - which feature ensure container b  can not see process of container c?   -- pid namespaces
        - which namespaces allows all the three container to use port 80 intenally?    -- network namespaces (hint where ever the port no is mentiond just say network namespace)



---------------container images-----------------
it is
    a read only blueprint
    containers:
            -base os(minimal)
            -application code
            -libraries and dependencies
            -runtimes
            -configrations
        images are immutables once made cant change

    eg -python:3.11-slim is the image
        this image includes
                linux os
                python 3.11
                standard python lib
            