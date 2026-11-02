---
name: rubber-duck
description: the agent explains the code aloud and looks for problems in the logic using it.
---

### Rubber Duck
If a bug can't be caught and fixed, create a file named rubberduckdebug.md, and go in-depth explaining the logic, how each piece interacts, what it's meant to do, what's breaking, etc.
Specifically, in this format for readability:
```md
---

**Bug**: [small one-line summary of the bug]
**RubberDuck**: [the in-depth logic explanation]
**Review**: [what you found, what you changed / are going to change, etc.]
---
```

Once you're done, look back over it, look how things realistically would interact, what can be changed, what will break, and optionally what can be optimised. If found, proceed to act upon that and fix the bug, and put what you found into the Review.
You don't necessarily need to delete the file when done — you can just leave it and add another to it whenever you must speak to the duck again, unless your user wants you to delete it.

### When To Use
Specifically, use whenever a bug you've tried to fix isn't fixing and/or is getting worse each time.
Although, emitting such in-depth logic can use many tokens and therefore eat usage fast, so explicitly ask the user whether or not you should consult the rubber duck to fix the bug, unless the user explicitly has told you not to.

### Examples
In this Skill, there's an `example_rubberduckdebug.md` with two fictional bug examples.
