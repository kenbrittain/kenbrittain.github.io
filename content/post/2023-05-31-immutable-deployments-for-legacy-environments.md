---
title: Immutable Deployments for Legacy Environments
date: 2023-05-31
postindex: 52
url: /post/52/immutable-deployments-for-legacy-environments
---

One of the ideas that stop people from adopting a full-on DevOps mindset of automation is immutability. Immutable deployments are where the contents of the deployment do not change with each deployment.

Legacy server based deployments involve deploying only changes, or deltas, to the runtime environment. There are teams that have been doing this for decades. It is a process they know and trust. They do not redeploy files that have not changed.

Docker has removed that choice by redeploying a single immutable artifact, the container. Docker, the company, has been around for 10 years. The technology used for containers longer. Teams deploying deltas even longer.

We have created a simple zip file and manifest model used to package these legacy applications for deployment. The manifest provides us a location for the git commit id. The package itself is immutable. These artifacts are simply unzipped onto a runtime server in the proper location as a deployment.

The caveat is that this package contains all of the files for the deployment. Even the files that did not change.

The biggest push back that we encountered is centered upon redeploying files that have not changed. Legacy teams with a long history do not feel comfortable with deploying a file that has not changed. They push back on this concept. They push hard!

I think that deploying the same binary file is just computer time. What takes longer is my time figuring out if it should be deployed. It takes less time to copy a file than it does to figure out if I should copy it.

That is the difference. I have accepted the challenge and am working toward a framework to allow the legacy teams to change their minds.
