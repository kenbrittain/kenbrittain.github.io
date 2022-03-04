---
permalink: /posts/25-understanding-publish-errors-for-net6-single-file-executables.html
title: Understanding Publish Errors for .NET 6 Single File Executables
layout: post
---

The following command line got the job done. At this point it produced an 18MB
(18,790,195 bytes) executable for Linux.


14MB (14010634) compressed

```shell
dotnet publish -c=Release -r=linux-x64 -p:PublishSingleFile=true --self-contained=true -p:PublishReadyToRun=false -p:UseAppHost=true -p:PublishTrimmed=true
```

> error NETSDK1031: It is not supported to build or publish a self-contained
> application without specifying a RuntimeIdentifier. You must either specify
> a RuntimeIdentifier or set SelfContained to false.

Some searching for a solution turned up this [issue][1] on GutHub.

> error NETSDK1102: Optimizing assemblies for size is not supported for the
> selected publish configuration. Please ensure that you are publishing a 
> self-contained app.

Depending upon the options chosen I was occasionally getting this error. The
runtime id was clearly being passed on my command line. The documentation
clears this up with the follow [notice][4].

> error NETSDK1031: It is not supported to build or publish a self-contained
> application without specifying a RuntimeIdentifier. You must either specify
> a RuntimeIdentifier or set SelfContained to false.



[1]:https://github.com/dotnet/sdk/issues/2484
[2]:https://docs.microsoft.com/en-us/dotnet/core/deploying/trimming/trim-self-contained
[3]:https://devblogs.microsoft.com/dotnet/announcing-net-6/#single-file-apps
[4]:https://docs.microsoft.com/en-us/dotnet/core/compatibility/sdk/6.0/runtimeidentifier-self-contained

