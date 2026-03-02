---
title: How Many Times Are You Going to Lock the Database
date: 2023-06-02
postindex: 54
url: /post/54/how-many-times-are-you-going-to-lock-the-database
---

The database is a company wide shared resource. It is big and it is expensive to run. When it has problems people notice. Even in development where there are hundreds of development teams working.

You need to communicate your planned goofy changes to shared resources. I am not talking about approvals. I am talking about sharing your plans and getting feedback.

What kind of things?

Locking or truncating tables. People tend to notice those things.

Have the resource owner review or provide input for your change. They will have the experience to steer you in the proper way to get it done.  
It's called getting feedback. You may not know all aspects of the system. Getting feedback keeps you from blocking other teams when your change goes bad.  
Send an email asking for feedback. Give your time frame and priority. This can only help you later if things get tense.  
This is not a CYA email you hope nobody ever answers. I am talking about actually communicating with the other team or teams. Explain your situation, what you plan on doing, and ask them for their help in planning.

Communicating your change before making it can only help you. The owner or team are more than happy to help. Sometimes you have to truncate tables. I am asking that you communicate that. Then people relying upon it to do their job are not surprised one day when it is no longer there.
