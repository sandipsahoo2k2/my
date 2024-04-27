## Generic pattern
![system_design_sheet](https://github.com/sandipsahoo2k2/my/assets/5547869/1d8ab7a1-6978-48c2-bae4-ce81bdc2bc7a)

## AWS example
![aws_design](https://github.com/sandipsahoo2k2/my/assets/5547869/85063839-5cc0-4e86-93f8-ffae01490747)

## Design a Event driven system with Microservices ( TikTok )
<img width="828" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/60320ed5-4998-4a79-a002-f919008a6a78">

## Follow a simple 5 step process
(Act as he is your product manager and you are an expert in this field)

* Define the requirement - ask questions
  - Functional Requirements
  - in the scope
    1. - create / add
    2. - update
    3. - delete
    4. - read - heavy ? Mostly all systems - ( except some financial systems )
  - out of scope
    - ?
    - ?
  - > Non Functional Requirement ( This can add estimation ) 
    1. Availibility - HA - 99.999% - ( talk about cost / saving if you can )
    2. Latency - which service needs what - read / write overall heavy ? 
    3. Scale - go to estimation ->
* Do some estimation
  - how many users are going to use the service ( Daily Active User )
  - Per second is DAU / 100k ? 1 mil / 100,k = 10
  - how long will you store the data ( TTL )

* Define some API -> for API Gateway CRUD + extra feature specific
* Design the Data Models - DB Tables - User Table - Order Table etc
* Final - Draw the design
  - Start with simple
  - add components as you talk
  - Deep dive one component if you have done something similar
  - MAKE SURE DO A DRY RUN FROM START to END FOR IMP FUNCTIONAL REQUIREMENTS

## References
* [https://aws.amazon.com/blogs/architecture/how-sonar-built-a-unified-api-on-aws](https://aws.amazon.com/blogs/architecture/how-sonar-built-a-unified-api-on-aws)
* [https://aws.amazon.com/blogs/architecture/top-architecture-blog-posts-of-2023](https://aws.amazon.com/blogs/architecture/top-architecture-blog-posts-of-2023)
* [https://aws.amazon.com/blogs/architecture/](https://aws.amazon.com/blogs/architecture/)
* https://www.hiredintech.com/system-design/
* https://www.youtube.com/playlist?list=PLJo-rJlep0EDFw7t0-IBHffVYKcPMDXHY
