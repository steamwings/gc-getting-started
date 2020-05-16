# Welcome to the Green Curtain Development Team! #

You can read this document with [VSCode](https://code.visualstudio.com/), which you're going to need anyway.

![View Markdown with VSCode](vscode-markdown.png)

This document will introduce you to our general software development practices.

## Principles ##
1. **Security is everyone's responsibility.** (see [Security Practices](#security-practices))
2. Do better than "industry standard".
3. Commit often. ([Git](https://git-scm.com/doc) good. :wink:)

## Specific Guides ##

Check out one of these more specific guides after you've read the general information in this one.

* [Front-end guide](frontend.md)
* [API guide](api.md)
* Backend - **TODO**

## Workflow ##

You need accounts for
- **[Keybase](https://keybase.io)** - Our primary communications and file-sharing platform because it's end-to-end encrypted and free. (We may re-evaluate since [Zoom bought Keybase](https://keybase.io/blog/keybase-joins-zoom).)
- **[Github](https://github.com)** - It's convenient that the tools we use are also based on GitHub (mainly [NativeScript](https://github.com/NativeScript)).
- **[Azure DevOps](https://dev.azure.com/greencurtain/)** - Includes all our CI/CD including builds, automated testing, and deployments.

### Tasks ###
<a name="tasks"></a>
VSCode offers [tasks](https://code.visualstudio.com/docs/editor/tasks) which can be configured to run when a workspace folder is open (see [Run behavior](https://code.visualstudio.com/docs/editor/tasks#_run-behavior)). See a specific dev guide for more info.

## Security Practices ##
<a name="security-practices"></a>

Nothing is secure. There's always a way in, whether it's [cryptanalysis](https://en.wikipedia.org/wiki/Cryptanalysis) or [social engineering](https://en.wikipedia.org/wiki/Social_engineering_(security)). (A basic understanding of those terms is strongly recommended.) 

It is _your_ job, regardless of your position, to be vigilant and minimize risk to the company and consumers. Ask questions. Raise concerns. Learn from other companies' mistakes and do better than 

Other notes
- Do not attempt [security through obscurity](https://en.wikipedia.org/wiki/Security_through_obscurity).
- It is not safe to assume that the Azure services we use cannot be compromised.
- TLS/SSL is good, but it's a weak guarantee of data privacy and/or security. If the data is at all sensitive, another layer of encryption should be used. We want to add general encryption for customer data for security and privacy sooner than later.

## FAQ ##
> Why aren't we using Slack?

[This article](https://keybase.io/blog/slack-incident) summarizes it.

> Is our code really safe on GitHub?

Hard to say. Our current setup is not preferable, though, since at the least our code is being transferred with only TLS encryption. (This is an example where relying on TLS is a _bad idea_).

> What about Keybase encrypted git repos?

Well, they're awesome, but 
1. It helps to have a GUI interface for diffs and PRs. (This could be done through GitHub Desktop.)
2. We need Azure DevOps integration. (Keybase bot maybe?)

As soon as we can meet those criteria (maybe with something customizable like GitLab), we can make the switch.