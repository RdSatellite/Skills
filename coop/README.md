# Co-op Skill Bundle

A set of basic AI–human cooperation skills that I use most of the time.

They are all invoked through the single `!coop` prefix so every command stays in one obvious, restricted scope:

- `!coop do`: Mark a specific place in the code and ask AI to implement it for you.

> I usually write the pseudo-code myself and ask AI to translate it when I forget some language-specific details via `!coop do`, or for some insignificant changes.

- `!coop try`: Give AI a known requirement and let it try to implement it for you. You review the result before applying any changes.
- `!coop check`: Make some changes yourself and ask AI to review them.
- `!coop diag`: Identify a problem at a specific place and ask AI to investigate it and provide diagnostic advice, without implementing anything.

Notice that every command is intentionally scoped to a small problem. This is because I don't want code changes to take control away from me. **You should know every line of your repository**.

If you prefer vibe coding, this skill bundle is probably not for you.

The trade-off is control: you can gradually master the entire repository instead of letting it become a black box. At the same time, these commands tend to give faster responses because every operation is constrained by a specific context and a clear scope.

For code that implements an already-identified requirement—meaning you have already expected the change and built the necessary abstract structure beforehand, such as creating a class and later implementing a method—you can let AI handle the implementation more freely.

See also the `Abstract Structure Bundle`.
