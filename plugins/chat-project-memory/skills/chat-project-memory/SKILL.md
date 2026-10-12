---
name: chat-project-memory
description: Use when the user is working on one or more projects in the current chat and wants proactive progress tracking, idea capture, milestone confirmations, recaps, or next steps.
---

# Chat Project Memory

Help the user keep project context easy to resume inside this conversation. Work only from the conversation and files or results the user provides in it. Do not add external storage, service connections, or AI API calls for the tracking workflow itself, and do not claim to remember information from a different chat. This restriction does not prohibit tools or services the user explicitly authorizes for actual project work; summarize their results when available. Respond in the user's language.

## Track project progress proactively

While this skill is active in the current chat, check each project-related message for progress, changed plans, decisions, and blockers. Do not wait for the user to say "update checkpoint" before incorporating a meaningful change.

1. Identify the project and goal from the conversation. If several projects are active, keep a separate record for each and use the one the current message refers to.
2. Read the latest checkpoint in this conversation, then incorporate newer messages and confirmed tool results.
3. Classify work as confirmed done, in progress, planned, blocked, or awaiting confirmation. Do not present assumptions as facts. Examples, quoted text, hypothetical questions, suggestions from the assistant, and negated statements are not evidence of actual progress or an adopted idea. Record an example only when the user adopts it for their project.
4. Mark work done when the user clearly says it is done or the conversation provides direct evidence that its acceptance condition was met. If code or a plan was produced but not run or reviewed, record that distinction (for example, "implemented; awaiting playtest").
5. When a meaningful milestone is reached, update the working checkpoint and briefly tell the user what changed. Do not emit a full checkpoint after every small exchange; refresh the full checkpoint after a milestone, when several updates accumulated, when asked, or when a long pause makes a recap useful.
6. Suggest the next one to three useful actions when the user finishes a step or asks what to do next.
7. Apply the user's latest explicit correction before relying on an older checkpoint. If a completed task regresses or is reopened, update its current status and capture what remains; do not continue reporting it as fully complete.

## Capture ideas and things the user wants to do

Notice ideas and future wishes expressed naturally, such as "I want to add co-op," "later I should make a shop," or "เพิ่มระบบเควสต์ไว้ก่อน". The user does not need to use a special command.

- Add each relevant idea to a separate **Ideas / later** backlog for the correct project, then acknowledge it briefly. Merge repeated mentions of the same idea instead of creating duplicates. Preserve uncompleted, undropped ideas in later checkpoints; brevity is not a reason to silently discard them.
- Keep ideas separate from current work, committed next steps, and completed items. Mentioning a wish does not automatically make it the active task.
- Do not interrupt brainstorming to demand priority, estimate, or details. Preserve the user's wording and clarify only when the project or idea itself is ambiguous enough to risk recording it incorrectly.
- Move an idea into planned or in-progress work only when the user indicates they want to prioritize or start it. If the wording could mean either "save for later" or "start now," ask a short choice question.
- If the user says an idea is no longer wanted, remove it from the backlog or mark it dropped. When an idea is implemented and confirmed, move it to confirmed done.
- When suggesting what to do next, consider the backlog but do not choose a future idea over the current goal without explaining the tradeoff or asking the user.

Examples of natural instructions include "เพิ่มไอเดีย: ระบบสัตว์เลี้ยง", "เอาไอเดียร้านค้ามาเริ่มทำ", and "ไม่เอาระบบ PvP แล้ว". These are examples, not required syntax.

## Ask lightweight completion confirmations

When the conversation makes it plausible that a task has been completed but does not confirm the result, ask one concise question before marking it done. Ask about one fact at a time. For example: "ระบบเก็บเหรียญทำเสร็จแล้วใช่ไหม?" Track implementation and validation separately; confirmation of implementation does not confirm a successful playtest.

- Ask only about the uncertain completion, not for a general status report.
- Keep the task as awaiting confirmation until the user answers. Associate the pending question with its project, task, and the exact fact being confirmed. A short answer such as "yes" or "ใช่" confirms only the most recent unambiguous pending question. If several questions or projects could match, ask which one instead of changing multiple statuses.
- If the user confirms, move it to confirmed done and update the checkpoint without requiring another request.
- If the user says it is not done or failed, keep it in progress or blocked and capture the issue.
- Do not ask again about the same task unless new evidence changes its status.
- Do not ask for confirmation when the user has already clearly confirmed completion.

If the evidence shows implementation but not validation, state that precisely and ask a short check-in only if knowing the validation result would affect the next step. For example: "สร้างระบบแล้ว เหลือทดสอบใน Roblox Studio — ลองแล้วหรือยัง?"

## Be proactive without interrupting

Acknowledge routine small updates naturally and fold them into the project record. Ask a confirmation only at a likely milestone or when an ambiguity changes whether work is complete. If no useful status change occurred, answer the user's immediate request without repeating the whole checkpoint.

This workflow runs when the assistant receives a message and this skill is active. It does not observe Roblox Studio, files, or other work between messages, and it is not a background monitor. Do not imply otherwise.

## Respond to progress requests

For requests such as "where did I get to?", "what have we done?", or "what should I do next?":

- Give a short recap first.
- List confirmed completed work, the current focus, and the next one to three actionable steps.
- Include decisions, ideas, and blockers when they affect what happens next.
- Separate confirmed facts from assumptions.
- If the conversation lacks enough evidence, say what is unknown and ask one focused question.

## Checkpoint format

Use this compact format and omit empty sections:

### Project checkpoint — <project name>
- **Goal:** <what the user is building>
- **Done:** <confirmed work>
- **In progress:** <current task>
- **Next:** <one to three concrete actions>
- **Ideas / later:** <future ideas, separate from committed work>
- **Needs confirmation:** <only likely completed work that remains unconfirmed>
- **Decisions:** <choices that should persist>
- **Blocked / unknown:** <what is preventing progress or needs confirmation>
- **Last updated:** <date, only when reliably available>

Keep the checkpoint concise and current. Replace stale details instead of accumulating a diary. Add links, file paths, or exact names only when they are present in the conversation. For game projects such as Roblox, useful context may include the gameplay loop, mechanics, scripts, assets, UI, playtest status, and publishing status.

## Returning after a long pause

Use the latest checkpoint still present in the conversation and any newer messages. If it is not available in the current conversation context, explain briefly that you cannot see it and ask the user to paste the latest checkpoint. Do not invent continuity across chats. The checkpoint itself is the portable handoff the user can copy into a new chat if needed.

