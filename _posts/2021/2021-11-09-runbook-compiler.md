---
permalink: /posts/7-runbook-compiler.html
title: Runbook Compiler
layout: post
---

<p>
    In this <a href="2021-10-30-yaml-runbooks.md">post</a> I recommended storing your
    runbooks in the YAML format. The idea was to keep the system documentation,
    and runbooks are a form of system documentation, in a developer friendly
    format. This simple step would enable document changes to be committed along
    with the source code being modified.
</p>

<p>
    The primary goal of using a structured document format is to have the ability
    to process them electronically. This means parsing. For lack of a better name
    let’s call the program the runbook-compiler. The compiler will process the
    YAML documents into an object model that can be used to generate individual
    and summary documents.
</p>

<blockquote>
    Think along the lines of a static website generator but for runbooks. I
    toyed with the idea of using Jekyll for this project but quickly decided I
    wanted a single executable distribution model. After having built many CI/CD
    pipelines, on virtual machines, in containers, and even on physical machines,
    actually having a single executable to perform an operation was, in a word,
    heaven.
</blockquote>

<h2>Markdown</h2>

<p>
    The runbook-compiler command will process all of the runbook source files found in a directory. The compiler will have multiple phases:
</p>

<ul>
    <li>collect all files to be processed into an object model</li>
    <li>ensure minimum viable runbook format for all files</li>
    <li>generate markdown files in the output directory</li>
</ul>

<p>
    The runbook-compiler uses the Microsoft.Extensions.FileSystemGlobbing NuGet
    package so all of the file globbing uses the wildcard patterns defined by
    the library. You can find all of the supported patterns defined
    <a href="https://docs.microsoft.com/en-us/dotnet/core/extensions/file-globbing#pattern-formats">here</a>:
</p>

<p>
    The goal of the initial implementation is to produce Markdown files. This
    was chosen was the minimum viable product because having a collection of
    Markdown runbooks is easily accessible, and should be readable by any
    technical person.
</p>

<h2>Minimum Viable Compiler</h2>

The MVC for this project will produce markdown files from source YAML files. It
will include any file in the runbooks source directory matching the wildcard
<code>*.yml</code>.

```bash
runbook-compiler compile-runbooks [--output-directory=&lt;DIR&gt;] [--output-format=&lt;FORMAT&gt;] [--source-directory=&lt;DIR&gt;]
```

<p>
    All parameters are required. There are no default values. This is by design
    as it is better to get an error than have implied behaviour determine a
    pipeline decision. In this case, that would be directory names, etc. By
    forcing the parameters you can support any crazy naming scheme a developement
    team dreams up. No requirements from the tool makes it a better tool.
</p>

<table>
    <tr>
        <th>Option</th>
        <th>Summary</th>
    </tr>
    <tr>
        <td>--output-directory</td>
        <td>Name of the root directory to write generated files.</td>
    </tr>
    <tr>
        <td>--output-format</td>
        <td>Name of the document format to generate files.</td>
    </tr>
    <tr>
        <td>--source-directory</td>
        <td>Name of the root directory for runbook YAML source files.</td>
    </tr>
</table>

