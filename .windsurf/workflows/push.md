---
description: Auto-commit and push all changes to GitHub repository
---

# Push Command Workflow

This workflow will automatically commit all changes and push them to the GitHub repository at https://github.com/TheEsotericEel/Maestro-AAS-Notes.git

## Steps:

1. **Stage all changes** - Add all modified and new files to git staging area
   ```bash
   git add .
   ```

2. **Commit changes** - Create a commit with current timestamp
   ```bash
   git commit -m "Auto-commit changes $(date '+%Y-%m-%d %H:%M:%S')"
   ```

3. **Push to remote** - Push changes to the main branch
   ```bash
   git push origin main
   ```

## Usage:
Run this workflow using the `/push` slash command in your IDE.

## Notes:
- This will commit ALL changes in the repository
- Uses current timestamp for commit message
- Pushes to the 'main' branch by default
- Make sure you have proper Git credentials configured
