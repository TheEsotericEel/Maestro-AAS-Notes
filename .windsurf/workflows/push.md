---
description: Commit and push all changes to GitHub with an auto-generated commit message
---

1. Run `git status` to see what files have changed
2. Stage all changes with `git add -A`
3. Generate a commit message based on the changes:
   - If there are changes to course notes (Week files, course directories), use format: "Update [Course] [Week/Topic] notes"
   - If there are changes to workflows or configuration, use: "Update workflows/config"
   - If there are new files added, use: "Add new notes/content"
   - If no specific pattern is detected, use: "Quick save" or "First push" (if it's the first commit)
4. Commit with the generated message: `git commit -m "your message"`
5. Push to GitHub: `git push`
