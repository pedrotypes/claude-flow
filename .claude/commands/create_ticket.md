# Create ticket

You are tasked with creating a ticket based on the input of the user. 

## Initial Setup:

When this command is invoked:

1. **Check if parameters were provided**:
   - If a ticket description was provided, skip the default message.

2. **If no parameters provided**, respond with:

```
I'm ready to open the ticket. Please describe your issue in detail.
```

Then wait for the user's ticket description.

## Steps to follow after receiving the ticket description:

1. **Determine the ticket number**
    - Find the highest numbered document in the `thoughts/shared/tickets/` directory
    - If no document is present, ticket number is 1.

2. **Synthesize title and summary**
    - Summarize the user's input to no more than three sentences
    - Further boil it down to a short title of a few words max

3. **Define a file name**
    - Use the directory `thoughts/shared/tickets/`
    - Use a filename like `{NUMBER}-{title}.md` 
    - {NUMBER} comes from step 1 and looks like `ENG-XXX`.
    - {title} comes from step 2 and should be in `kebab-case`

4. **Analyse and decompose the ticket description**
    - Break down the user's description into a problem statement and a desired outcome

5. **Compose and present the ticket**
    - Compose it with YAML frontmatter followed by content:
```markdown
---
date: [Current date and time with timezone in ISO format]
requester: [Requester name from git config]
topic: "[The title defined above]"
status: open
last_updated: [Current date in YYYY-MM-DD format]
last_updated_by: [Requester name from git config]
---

# TICKET: [title]

## Summary

[A summary of the problem and desired outcome in max 1-2 short sentences]

## Problem
[The problem statement]

## Desired outcome

[The desired outcome]

```
    - Present the ticket contents to the user
    - Ask if they want to accept, or change the ticket contents

6. **Handle follow-ups**
    - If the user wants to make changes to the ticket, run Steps 2 through 5 again.
    - If the user says they want to accept, continue to the next step.

7. Save the document to the file name defined in step 3, 
