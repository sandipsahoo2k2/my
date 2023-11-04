## Why do companies ask irrelevant questions ?

I was talking to a friend the other day at the Winter Cafe at the south station. We were discussing about the interview questions and relevance to our day today job. Yeah you guessed right intersection is a Fi. No relevance to what so ever, we were interviewed for. Truly speaking I think the only thing a person should know is how to count money and some basic mathematics to run a big business. No need of Integration and derivatives all math puzzles etc.
I feel like many of us wasted so much of energy solving puzzles by Shakuntala Devi, haven’t you? Now also some like to ask brainteasers and puzzles in interviews but I hate it when some one judge you on your ability to solve a brainteaser, btw Google says they use to ask before but now they don’t anymore.

What am I trying to convey here ? It will be very clear once we read next three para of my experience with building the [links] for my articles at interviewdose.com .

**The challenge was clear:** I needed to list all the files in a given folder at interviewdose.com, even if it contained subfolders within subfolders.
So you can imagine we need to run a loop but the structure is same for folders/files hence, what we can do for one folder, can be applied to folders within it. 
The solution? A recursive algorithm! Now, you might wonder when and why you’d need a recursive method in your job. It’s a rare but powerful tool that comes in handy when dealing with complex structures. In my case, it was the key to tackling a task that seemed almost impossible. So, if you ever find yourself in a similar situation, remember this article as a valuable reference.
So on the server side I had to write a DFS ( Depth First Search ) algo to list all the files and return a tree to my angular articles page and in the front end I wrote a wrapper to get all files and ran a *ngFor loop.

getFiles(givenFolder) -> Directory Object -> a DFS program to Flatten the tree to array of files -> run *ngFor loop and build link/href tags.

<img width="100%" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/52ae8456-0814-4a70-878f-ee193be21573">


You can say you could have returned the flattened structure from the backend to avoid extra processing ? yes but I didn’t as I will have the luxury of traversing the n-array tree when I need to traverse the path to go to a link right ! Anyway I don’t want to deep dive into few utilities methods that I wrote to list the file names and files with folder names too as the screenshot above.

*What did we learn from this article ?* Yes you may have to write a recursive algo to solve a problem in interview when you are appearing a big tech org like maang .. Does it make sense now ?

**Your Next Role :** Like wise many of the behavioral and googlyness questions might sound irrelevant to you, but they make sense and they actually connect to a future role for you. How you communicate and answer a situational questions tells an interviewer which role you are fit for. So definitely preparation is a must for your next interview but prepare in future tense always, which means at times questions are asked for your next role not for the role that you are working or you have worked.

By transforming a seemingly daunting task into an elegant solution, I hope to inspire and empower fellow enthusiasts like you. Share this with your friends and colleagues, and let’s see my MVP interviewdose.com nuts abd bolts while I build and learn from here. 
