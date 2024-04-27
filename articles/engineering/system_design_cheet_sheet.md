## How to system design a problem statement
System design is a very broad problem, There is no right or wrong answer, with modern technologies and tools everything can be build with following very simple to complex patterns. Interviewers expections is to gaze how much expreince you have from this kind of questions. Here you can talk about 0 to z but it's timed. Hence it's easy to miss many aspects. Hence
follow this structured 5 step approach you will be able to cover most of your thought process.

### Follow a simple 5 step process for your design interviews

(Act as he/she is your product manager and you are an expert in this field)

1. Define the requirement - ask questions
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
2. Do some estimation
    - how many users are going to use the service ( Daily Active User )
    - Per second is DAU / 100k ? 1 mil / 100,k = 10
    - how long will you store the data ( TTL )

3. Define some API
   - CRUDS Services
   - Extra feature specific
     
4. Design the Data Models
     - DB Tables
     - User Table
     - Order Table etc
       
5. Final - Draw the design
    - Start with simple
    - add components as you talk
    - Deep dive one component if you have done something similar
    - MAKE SURE DO A DRY RUN FROM START to END FOR IMP FUNCTIONAL REQUIREMENTS
      
## Generic pattern
![system_design_sheet](https://github.com/sandipsahoo2k2/my/assets/5547869/1d8ab7a1-6978-48c2-bae4-ce81bdc2bc7a)

## AWS example
![aws_design](https://github.com/sandipsahoo2k2/my/assets/5547869/85063839-5cc0-4e86-93f8-ffae01490747)

## Design a Event driven system with Microservices ( TikTok )
<img width="828" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/60320ed5-4998-4a79-a002-f919008a6a78">

## References
* [https://aws.amazon.com/blogs/architecture/how-sonar-built-a-unified-api-on-aws](https://aws.amazon.com/blogs/architecture/how-sonar-built-a-unified-api-on-aws)
* [https://aws.amazon.com/blogs/architecture/top-architecture-blog-posts-of-2023](https://aws.amazon.com/blogs/architecture/top-architecture-blog-posts-of-2023)
* [https://aws.amazon.com/blogs/architecture/](https://aws.amazon.com/blogs/architecture/)
* https://www.hiredintech.com/system-design/
* https://www.youtube.com/playlist?list=PLJo-rJlep0EDFw7t0-IBHffVYKcPMDXHY

1. Design a Parking lot : https://youtu.be/rl_FPNCgbYA
