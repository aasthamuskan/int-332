layering system - only work for the blue print 
image layering system
            -os
            -application
            -runtime envirnment
            -dependecies

network layring system
    face os
    bin lib
    application depencencies
    runtime dependencies



-----------container image vs container------------
container - only contains writable layers 



------image registry------------------ 
 it is a centralised repo used to store manage ,version, and distribute container image
 it enables:
        - sharing image across teams and envirnment
        - consteint deployment in development and testing and production
        - integration with ci/cd pipeline
- in devops an image registry plays the same role as:
        - gihub - sourc code
        - maven central - java libraries



---------why image registy is required----------

without a registry :
        -each system must build image idependently
        -manual software installation
        - no version control of application envrinment
        - high incosistency across envirnment
with a registry
            -build once deploy everywhere
            -faster deployment
            - version controlled envirnments
            - rollback capabality
  

  --------types of image registries-----------

 1. public image registries
        it allows open access to images

  charecteristics:
        images are publically visible

2. private image registery
    it restrict acess using auhtentication and autherization

    charectrictics:
        secure and controlled acess
        used in enterprises
        stroes proprietary application
        integrateed with iam and rbac
    examples:
        aws  elastic container registru(ecr)
        azure continer registry(acr)
        github container registry



        -------iamge naming convention-----------

        format : <registry>/<namespace>/<iamge>:<tag>

        eg: docker.io/aastha/webapp:v1

        registry-location of imahe
        namespace - user or organizaion
        iamge - application anme
        tag - version or label

---------taging and versioning-----------
 
 tags identify diffrent version of the same image
    common tagging strategies

    tag                      purpose





----------image distribution process--------------
it refer to how image move from developer to production system

distribution flow


pull and push opreation
    push - uplaod iameg layer from local system to registru
         - requires authentication'
         - only new layer are pushed
 - pull
       - downloads images layer from registry
       - uses caching to avoid re -downlaading existing layer
     - 
- -------------role of images registeris in ci/cd pipelines------------------
    
    in moder devops pipelines:
        code is commited to git
        ci system build the container image
        image is pushed to registru
        cd system pull the image

        -------------------conparision btw public and pricate registry-------------


  