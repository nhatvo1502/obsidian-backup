### 1. Purpose:

GitHub Actions is a CI/CD tool built into GitHub that allows automating workflows like testing, building, and deploying applications directly from GitHub repo.

---
### 2.Components:

1. Events - Triggers that start workflow( `push`, `pull_request`, `schedule`)
2. Jobs - A series of task executed within the workflow
3. Steps - Individual commands with a job
4. Runners - Virtual machines when jobs ( Ubuntu, macOS, Windows)

---

### 3. Workflows

1. Create a subdirectory .github/workflows
2. Create a github action workflow file 
	1. Choose trigger type (push, pull_request, schedule)
	2. Choose runner type (Ubuntu, macOS, Windows)
	3. Create steps
3. Run trigger

