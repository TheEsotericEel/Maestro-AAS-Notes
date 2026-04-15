---
description: Create directory structure and placeholder markdown files for a course
---

When the user runs `/class` followed by raw curriculum data (course structure with weeks, dates, and lessons):

1. Parse the curriculum data to extract:
   - Course code (e.g., CS102)
   - Week numbers with date ranges
   - Week titles
   - Lesson numbers and titles for each week

2. Determine the correct term number by checking existing structure:
   - If course code starts with CS, FE, BE, AI → likely Term 2
   - If course code is PY101, PSYC100, MATH100, etc. → likely Term 1
   - Check if course folder already exists in Term 1 or Term 2 to confirm

3. Check if files already exist before creating them:
   - If a file with the exact name already exists, skip it (do not overwrite, do not duplicate)
   - Only create files that don't exist yet
   - This allows partial completion - if you have some lessons done, it will only create the missing ones

4. Sanitize titles for filenames:
   - Replace colons (:) with dashes (-) or remove them
   - Replace other invalid Windows filename characters (<>:"/\|?*) with safe alternatives
   - Example: "The atomic age and the rise of technological America: 1945 to 1970" becomes "The atomic age and the rise of technological America - 1945 to 1970"

5. Create the directory structure:
   - `Term [N]/[COURSE_CODE]/` (course folder)
   - `Term [N]/[COURSE_CODE]/Term [N] - [COURSE_CODE] - Week [N] - [Sanitized Week Title]/` (week folders)

6. Create empty placeholder markdown files for each lesson:
   - Format: `[NN] - [Sanitized Lesson Title].md` (zero-padded lesson number)
   - Example: `13 - Edge cases and reliability in array operations.md`
   - Files must be completely empty (no content)

6. Report success with a summary of what was created (course code, term, number of weeks, total lessons created, total lessons skipped).

## File Naming Conventions

Based on existing repo structure:

**Week folder format:**
- `Term [N] - [COURSE_CODE] - Week [N] - [Week Title]`
- Example: `Term 2 - CS102 - Week 1 - Foundations of data structures`

**Lesson file format:**
- `[NN] - [Lesson Title].md` (zero-padded lesson number)
- Example: `13 - Edge cases and reliability in array operations.md`

**Full path example:**
- `Term 2/CS102/Term 2 - CS102 - Week 1 - Foundations of data structures/13 - Edge cases and reliability in array operations.md`

**Special lesson types:**
- Review lessons: `Weekly review: [week title]` or `Review: [course summary]`
- Challenge lessons: Include "Challenge:" in the title
- Graded/Retake: Keep original titles
