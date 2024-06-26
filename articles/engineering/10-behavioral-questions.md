<!-- Draft -->
## 1. Areas of improvement ?

1. **Situation - Delegation**
I believe one area where I have room for improvement is **delegation** skills.

I tend to take on a lot of responsibility to ensure things are done to my standards.
However, I've become increasingly aware of the importance of delegation in maximizing team efficiency and fostering growth.

I've been actively working on my delegation skills by seeking guidance from mentors Udemy..

I've also been practicing delegating tasks in _small increments and providing clear instructions in the Jira.._

There is a saying 0 to 1 is my initiative but 1 to inf is leadership or delegation.

2. **Situation - Removing Ambiguity**
As a senior engineer I always have to deal with a lot of ambiguity. At times when we don't clearly communicate or understand the requirement.

I certainly should be able to provide clear direction and make informed decisions, especially when faced with uncertainty.
Craft a successsheet - Ask questions to Product Managers - 
Estimation, Do you expect some change in UX, Who are our biggest customer, Beta Time line, Migration plan ( Internal,  Paying )
   
3. **Situation - AI integration**
Recently we acquired Armorblox/Splunk. LLM and NLM Security company. We wanted to build AI Tools around security. I see the gap. I am up for learning.

## 2. Time I had disaggretement with stake holders ?
1. **Situation - Automating the creation and maintainance of Version Dependency file for CDO**

Example for ASA Device Team - They wanted us to create a dependency file for our users where as the knowledge is with them. ( Even if we would be able to do it - we still nedded someone to approve the final go )

Cisco has a software download site ( It's secure ) bla bla
We had to present the version information from the image and say what version they should upgrade to go to a new version.
We had this requirement for upgrade devices - Where we would pull the image info and create a JSON and give it to our service so that it can presentable the info in a way that can be used by user to upgrade the image.
It is usually a tediuous process for our team and ASA device team were not ready to do a very simple job from their end.

## 3. Time I had disaggrement with a team member ?
* There was a situation when there was a problem when we were not deleting the Change Log for some devices. I was asked to fix  it.. It was not deleted because we never cerated it in the first place. I found that because of the reason we were deleting the devices references forcible hence the post processors were not called . I fixed it, it was deleted.
  
* Update settings using a framework which was done in the intial phase of the dev, premature lots of lots of unnecessary code. I found a simpler approach and also built and integrated my own framework which uses the one time parsed instance and added the capabilities to easily update the settings.

* Creating a new API for migration was the idea of some people suggestions. Which was not atall a good idea because it adds a lots of extra work. exposing a functional end point of for a feature is not a good idea when its not used after the job is done.
What I did was the use the existing framework but do the batch in backend instead of the UI framework.

* Using DynamoDB instead of the aws scheduler it self for storing the scheduled job information. it's redundant data.

## 4. Time when the project was delayed ?
ASA Shared policy is a perfect example where I am working now.
We had plenty of time and we estimated this to be as equal or less time as another feature called shared settings. 
Similar work - create shared policy, share with other linked devices. Discovery  was not there where we dont have to deal with discoveing the devices with the same ploicy digest. The main problem here is Migartion of older devices to the newer policy.

Upon researhing/spiking I got to know tht its not simple, we are going to affect the bread and butter of CDO. We have to be extra careful. We had to deal with clients with over 1500 devices also devices having thousands of lines of config.

So I setup a plan 
1 - UI migartion ( DO it yourself Migartion )
2 - Internal Clients Migartion
3- Paying customers
4 - Paying customers with Devices more than 1000 devices.

This task is going to be huge. every week we have relase and i have to co-ordinated with ops team for thursday migration.

## Most difficult Task / Bug - Webworkers ( Angular )
Performance Improvement - Hundreds of unnecessary websocket connections getting created with Trade View / 
Removed dependency of EC2 Server instances used for throttling and grouping of various real-time messages for web clients by writing web- workers API, saving cost and turnaround times for Welling ton management.

## Conflict with senior /managements 
Distributed Rate limitter vs Jgroup code embedded in our code

## 1. Tell me a time when you were not able to meet a time commitment
  Above is a greate example..

## 2. Tell me a time when you were stuck and how did you get wayout / unblocked
  - Situation - 
  - Task - 
  - Action -
  - Result  -
    
## 3. Tell me a time when you have team conflicts and how did you resolve it 
  - Situation -
  - Task - 
  - Action -
  - Result -

## 4. Tell me a time when you worked with a difficult team member 
  - Situation -
  - Task - 
  - Action -
  - Result -

## 5. Tell me a time when you recovered from a difficult situation
  - Situation -
  - Task - 
  - Action -
  - Result -

## 6. Tell me a time when you came up with a new approach to a problem
  - Situation -
  - Task - 
  - Action -
  - Result -

## 7. Tell me a time when you came up with a new approach to a problem
  - Situation - Shared Settings / Creating reports 
  - Task - Had to Create my first report in the team
  - Action - Built a framework
  - Result - 100 reports 60% less time

## 8. What's your strength and weakness
  - Situation -
  - Task - 
  - Action -
  - Result -

## 9. Describe a time when you set your sights too high. 
  - Situation -
  - Task - 
  - Action -
  - Result -
    
Chat GPT - I suppose one time I set my sights too high was when I tried to learn several complex subjects simultaneously. I was eager to expand my knowledge across multiple domains all at once—programming languages, advanced mathematics, philosophy, and literature, to name a few. While the ambition was admirable, I found myself overwhelmed and unable to make significant progress in any one area. It taught me the importance of focus and prioritization, as trying to master too much at once can often lead to burnout and frustration. It's better to tackle one thing at a time with full dedication rather than spreading yourself too thin.

## 10. Tell me about a difficult decision you've made in the last year.
 - Situation -
  - Task - 
  - Action -
  - Result -

## Tell me a bit about your professional experience [2-3 minutes]

This question will allow you to get an initial sense of your peer’s experience.
Feel free to ask follow-up questions, for instance, can you elaborate a bit more on your experience with [specific technology] or your responsibilities at [company]? You can also use this opportunity to ask the candidate which of their experiences had the greatest impact on them.

## What are you looking for in your next role?

This is an opportunity to get insight into whether a candidate would be a good culture fit for your company. Is the candidate looking for a company of your size? Do their expectations match the role?

## What’s an example of a difficult problem you solved? Be specific about how the problem was diagnosed and your process for approaching it.

Owner vs participant: Many candidates will claim they led a big project or created significant impact, but if you dig deeper, you’ll find that the candidate only played a participatory role or was involved in just one facet of the project. As an interviewer, it’s your role to uncover the truth. Follow-up questions asking about who was involved, what the candidate personally did, and how they did it will help you make an informed decision about the candidate’s true impact.
Good vs great achievements: Many candidates are good at quantifying their achievements, but you’ll want to know how big of an impact this achievement actually had. Was it a minor success or did it have a significant impact? Were the results due to the candidate’s impact, or would those results have likely occurred without their involvement? You may consider asking follow-up questions here too: try to drill down into the baseline metrics used, such as “What were the projected metrics had you not made this decision?”

## Give me a specific example of a time when you sold your supervisor or team on an idea or concept. How did you convince them? What was the result?

This question is about teamwork and influence. You want to dig into the candidate’s ability to reason and listen to their superior, navigate a difference of opinion, and ultimately, show how they resolved the disagreement.

## Tell me about a time when your work responsibilities got a bit overwhelming. What did you do?

This question allows you to get insight into how the candidate works under pressure and how they manage their time. It’s an opportunity for the candidate to highlight specific examples of working well under pressure. Try to drill down into any examples when it seems that the situation could’ve been prevented, due to procrastination, etc.

## How do you stay up to date with the latest technologies?

This question is about getting a sense of the candidate’s growth mindset – Whether they’re invested in continuous learning and personal improvement. Drill down into how and where they go to stay up-to-date.

