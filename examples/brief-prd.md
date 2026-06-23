# Brief PRD Example

## Product

TaskPilot is a lightweight Web app for small teams to create, assign, track, and review weekly tasks.

## Goal

Help a team lead quickly turn scattered work requests into visible tasks, assign owners, and understand what is blocked before the weekly sync.

## Core Flow

1. User opens the team workspace dashboard.
2. User clicks "New Task".
3. User enters title, description, priority, due date, and owner.
4. User can attach up to 5 files.
5. User submits the task.
6. App validates required fields and shows success.
7. User can find the task in the task list.
8. User can filter by owner, status, priority, and due date.
9. User opens task detail to update status or add a comment.

## Rules

- Title is required.
- Owner is required before publishing.
- Due date cannot be earlier than today.
- Attachments are optional and limited to 5 files.
- Status values: draft, todo, in progress, blocked, done.
- Priority values: low, medium, high.
- Deleting a task requires confirmation.
- Drafts should be recoverable after refresh.

## States And Exceptions

- Empty task list: show a useful first-task prompt.
- Filter has no result: show clear reset-filter action.
- Missing required fields: show inline validation.
- Attachment upload failure: keep the task content and allow retry.
- Save failure: keep edits as a local draft and allow retry.
- Permission denied: explain that only workspace admins can delete tasks.

## Review Needs

The prototype should be responsive, low fidelity, and useful for product/design/engineering/QA review.
