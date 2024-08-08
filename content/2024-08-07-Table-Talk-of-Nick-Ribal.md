---
categories: ["meta"]
date: "2024-08-07"
title: "Table Talk of Nick Ribal"
---

Who wrote [these articles](https://medium.com/@elektronik).

All the misinterpretations are my own.

## Styling web components

- HTML was originally designed for documents.  

- For documents, the cascading styles of CSS makes sense: you want uniform styling across the global environment, with fall-backs as necessary.

- But for web apps, the document model doesn't make sense.  You want separate components for different things (buttons, menus etc).  For a component, you want all the styles to be confined to the component itself: you don't want a situation where the overall style sheet may affect the look of a button.

- CSS modules is one solution to the problem.  CSS in JS is another.

- Tailwind is a great tool for beginners and people who need to work on web styling without deep knowledge of CSS.  For that target audience, it is a great tool.  

- But for people who already knows CSS well, it is just an additional layer of abstraction they need to learn, and an artificial constraint on their toolbox.

## Javascript

- Javascript is special because it was designed for and has to continue work on the browser.  

- Backward compatibility is non-negotiable: otherwise vast numbers of seldom-maintained websites will break.

- Python 3 (with great cost) introduced breaking changes: but that is possible only because Python is usually run on the local machine, not client-side.

- This means Javascript will just get more and more complicated.  In a way, studying it will be similar studying the history of the web.

## Software mutability

- The reason why "software is eating the world" is because it is so easy to change and fix.  Faulty software can be fixed with an update via the web.  Not so for hardware.

- So for most things, it is just cheaper to do things by a general computer and software, not specific hardware.

- This also means that no software is ever truly "finished": they can always be one better.

## Rewriting / refactoring

- Much as programmers dream of it, it is very seldom that a large project can be rewritten from scratch.

- For the business to continue, a team will need to maintain the existing version, with improvements constantly being made.

- Which means the new version will always be chasing a moving target.  And man-years of work would have gone into the old version, giving it a huge head start.

- So the best one can realistically do is to refactor individual parts, while keeping the whole thing going.