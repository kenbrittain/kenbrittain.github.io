---
title: Running the Same Job Again Ain't Gonna Fix It
date: 2023-06-01
postindex: 53
url: /post/53/running-the-same-job-again-aint-gonna-fix-it
---

The first time you ran the job, and it failed, is because it was broken. The second time you ran it and it worked was because you did something to the system that allowed it to succeed. Your job is still broken.

You need to find out why the job is broken. Do not follow the \*run it again\* pattern and hope for the best.

First, locate any logs that are available. Development tools produce logs. Your job is to locate them so you can move on to to second step.

Second, look at the logs. Search for errors and warnings. You are looking for clues. Look at the logs. 99% of all emails we receive for errors can be resolved using the logs. I am not saying that build platforms do not have issues. What I am saying is that 99% of the time you have an error.

Your DevOps teams can help you debug an issue but they do not have magic powers. They have no idea what your SQL job is doing. That fact that it is running at all proves the deployment code is working. If it hangs in the database get in touch with a DBA.

Build failures are because of errors in your project. Most errors are in missing or incorrect dependencies. You should be explicit when defining your dependencies. Transitive dependencies will break your project. Be specific.

Finally, you have have found the logs, look into them, and verified there are no errors. Go ahead contact the DevOps team. Tell them what you have done already. Trust me, they will appreciate what you have done and then they will help you. We love solving problems.
