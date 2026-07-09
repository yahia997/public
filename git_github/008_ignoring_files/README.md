# Ignoring Files
Often, you’ll have a class of files that you don’t want Git to automatically add or even show you as
being untracked. These are generally automatically generated files such as log files or files
produced by your build system. In such cases, you can create a file listing patterns to match them
named `.gitignore`.

`.gitignore` file has some rules:
- Blank lines or lines starting with `#` are ignored.
- Standard glob patterns work, and will be applied recursively throughout the entire working
tree.
- You can start patterns with a forward slash (`/`) to avoid recursivity.
- You can end patterns with a forward slash (`/`) to specify a directory.
- You can negate a pattern by starting it with an exclamation point (`!`).

The patterns inside `.gitignore` are like a regular expressions:
- An asterisk (`*`) matches zero or
more characters.
- `[abc]` matches any character inside the brackets (in this case a, b, or c).
- a question
mark (`?`) matches a single character.
- brackets enclosing characters separated by a hyphen (`[0-
9]`) matches any character between them (in this case 0 through 9).
- You can also use two asterisks to
match nested directories; `a/**/z` would match `a/z`, `a/b/z`, `a/b/c/z`, and so on.

Here are some examples:
```gitignore
# ignore all .a files
*.a
# but do track lib.a, even though you're ignoring .a files above
!lib.a
# only ignore the TODO file in the current directory, not subdir/TODO
/TODO
# ignore all files in any directory named build
build/
# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt
# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

# Task