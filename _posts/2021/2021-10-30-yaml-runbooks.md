---
permalink: /posts/6-yaml-runbooks.html
title: YAML Runbooks
layout: post
---

<p>
    If you have worked in IT for  any length of time you have heard that you need
    to document your projects. Great! At the very least some documentation
    exists but nobody really does this. Documentation is tough and developers
    do not really enjoy writing it.
</p>

<p>
    However, what if a format existed the would encourage developers to write
    documentation? I am not talking about documentation such as user manuals or
    reference guides. I am talking about runbooks. Similar to how unit tests
    define the boundaries for a system, runbooks defines how it operates.
    In my opinion they are a form of systems documentation.
</p>

<blockquote>
    <p>
        You need to have runbooks for the operation of your systems. If you do
        not then you are relying upon the membership and collective memory of
        the team. Eventually, both of the things will change. Having a set of
        runbooks will help define the boundaries of your system.
    </p>
</blockquote>

<p>
    Runbooks should start as structured documentation. This format needs to
    be a text based format. The days of runbooks as Word documents are long
    gone (Confluence maybe but never Word or similar binary formatted
    document). Current trends are for wikis or other online formats to be
    used. I am suggesting a raw format of YAML files contained within a git
    repository. This ensures the runbooks are accessible to developers. The
    YAML is easily readable and can be followed.
</p>

<blockquote>
    <p>I have worked on systems that stored the runbook information as structured JSON documents. These documents were translated by a script into XHTML and published to Confluence. This setup allowed us have an editable format but online presentation. The JSON was tedious and not conducive to writing text.</p>
</blockquote>

<p>
    If you were to create a sample runbook that used the suggested format you
    would have something along the lines of what follows:
</p>

```yaml
title: Sample Runbook
summary: |
    This runbook is just a sample to demonstrate how to format the source in YAML.
    It is not meant to perform any actions. This is really just a sample. Any text
    block can formatted as *Markdown*.
note: |
    You can use the `$(...)` syntax to reference variables in any text block within
    the runbook. The file `default.yml` will be included within each runbook as it
    processed.

author: Enter Team Name
contact: team@domain.com

steps:
- name: First Step
  summary: |
    This steps does nothing but it is the first. Remember, this is a sample
    runbook and is designed to accomoplish nothing.
  note: Notes can be added but are not required.
- name: Variables
  summary: |
    This runbook references the `$(Team)` and `$(Email)` variables. The
    variables can be defined in the `default.yml` file contained in the root
    directory in addition to the command line.
- name: Mardkdown
  summary: |
    All runbook YAML source files compile to Markdown files for reading. This
    is the first step for readability. This functionality is included in the
    compiler by default.
```

<p>
    Next up we will look into how to compile this into a Mardown files for easy
    viewing.
</p>
