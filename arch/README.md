# Arch Skill Bundle

A set of skills about refactoring and scalability.

They are:

- `!arch move`: Move requested part to somewhere. Usually happens when abstract structure changes.
- `!arch sop`: Write a SOP skill based on the abstract structure and your design. 
- `!arch extern`: Do extension following to existed SOP skill.

I only consider architectural extensions that can be explicitly identified in advance as safe and controllable changes. These extension points should also be reflected in the abstract structure of the codebase, making the intended boundaries and constraints clear.

With these boundaries established, a Code Agent can implement such changes with minimal risk and without requiring excessive human supervision.

After carefully evaluating an extension point, I use !arch sop to turn the design into a reusable extension skill that tells agents how to implement the change within the intended architectural boundaries.

They will be very useful in collabration too.

---

> Sega Lee
> 
> Oct. 15th 2026
