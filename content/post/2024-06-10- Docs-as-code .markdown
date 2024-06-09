---
categories: meta
date: "2024-06-10T00:00:00Z"
title: Docs-as-code in theory and in practice
---

In this Write-the-Docs London talk on 2 May 2024, speakers shared their experiences with using software tools to automate the publication of their companies’ documentation. 

Because these software tools are also used by programmers for computer code, this approach is also known as the “Doc-as-Code”.

[Vladimir Izmalkov](https://www.izmalk.com/) gave the first presentation.  He gave a broad overview of common software tools for Doc-as-Code, including (amongst others):-

-	[Git](https://docs.github.com/en/get-started/using-git/about-git) for version control
-	[Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for formatting text
-	[Hugo](https://github.com/izmalk/hugo_quickstart) for deploying a static website

Vladimir then shared VK Private Cloud’s experience with migrating documentation from Confluence to Git in a short time frame, and in the processing changing the underlying document format from Microsoft Word to AsciiDoc.

Highlights include finding and mastering a free open-source tool called Pandoc, where users has fine-grain control over many aspects of document-format conversion; and the huge difference in workflow once it became possible to use branches and merging to manage different versions of the documentation.

[Ian Selwyn-Smith](https://www.linkedin.com/in/ian-selwyn-smith-6b4baa/?original_referer=https%3A%2F%2Fwww%2Egoogle%2Ecom%2F&originalSubdomain=uk) gave the second presentation.  He explained Caplin Systems’ experience of migrating and publishing documentation in web format.  Highlights include weighing pros and cons in choosing the relevant technology stacks, bringing the management and the developers on board with these choices, and liaising with the design team to make sure the new website has the right look and feel.

Finally, [Polina Zaichkina](https://www.linkedin.com/in/polina-zaichkina/?locale=en_US) shared Codat’s experience with migrating into Doc-as-Code.  Highlights include liaising with developers for input and technical help; the decision to make the entire documentation open source; the processes that needed to be set up to handle pull requests (i.e. suggested edits) by the public; and how some clients cited the superior documentation as a factor that makes Codat’s products stand out from its competitors.

The evening concluded after a brief Q&A with audience going deeper into the topics covered by the speakers.
