# Claude flow

Add these directories to your project:

```
./.claude   # agents and commands
./thoughts  # storage for tickets, research and plans
```

This is taken and slightly modified from:
https://github.com/humanlayer/humanlayer

## Workflow

0. OPTIONAL: Open a ticket

- Start new session
- Run `/create_ticket`

It's going to help you structure the issue you have or the feature you want to build a little bit.

1. Research the codebase

- Start new session
- Run `/reseach_codebase`
- Answer its questions

You're basically trying to figure out how certain things are done, or where your next feature might logically have to live. You'll be able to refer to this research later.

2. Make a plan

- Start new session
- Run `/create_plan`
- Answer its questions
- Iterate until you're happy with the plan

This is where you describe the feature that you want to build, or the change you want to make. Reference any tickets or research files that are relevant.

This should be an iterative process where the LLM asks you questions, you answer, you review, and iterate until the plan looks good.

The resulting plan will be very tedious and detailed. It's a step by step description of changes to the code. It's meant for the LLM to be able to follow without thinking or screwing things up too much.

3. Implement the plan

- Start new session
- Run `/implement_plan @plan_file`

This reads the plan and gets to coding.
If your context is getting used up, pause, ask it to take the learnings from the session and incorporate them into the plan so it wouldn't make the same mistakes next time, compact and continue.

The idea is that you should be able to do a git restore, run the revised plan, and get to where you are in one go without all the trial and error and re-prompting.
