# Rule: Generating a Task List from a PRD or FRD

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list in Markdown format based on an existing Product Requirements Document (PRD) or Feature Requirement Document (FRD). The task list should guide a developer through implementation.

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/tasks/[n]-[feature-name]/` (same directory as the FRD)
- **Filename:** `tasks-[document-file-name].md` (e.g., `tasks-0001-frd-user-profile-editing.md` or `tasks-0001-frd-authentication-system.md`)

## Process

1.  **Receive Document Reference:** The user points the AI to a specific PRD or FRD file
2.  **Analyze Document:** The AI reads and analyzes the document contents:
    - **For PRD:** Focus on functional requirements, user stories, goals, and success metrics
    - **For FRD:** Focus on technical architecture, implementation plan, database changes, API specs, and task breakdown
3.  **Assess Current State:** Review the existing codebase to understand existing infrastructure, architectural patterns and conventions. Also, identify any existing components or features that already exist and could be relevant to the document requirements. Then, identify existing related files, components, and utilities that can be leveraged or need modification.
4.  **Phase 1: Generate Parent Tasks:** Based on the document analysis and current state assessment, create the file and generate the main, high-level tasks required to implement the feature:
    - **For PRD:** Derive tasks from functional requirements and user stories (likely ~5 high-level tasks)
    - **For FRD:** Use the existing task breakdown section if available, or derive from the implementation plan phases
    Present these tasks to the user in the specified format (without sub-tasks yet). Inform the user: "I have generated the high-level tasks based on the [PRD/FRD]. Ready to generate the sub-tasks? Respond with 'Go' to proceed."
5.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".
6.  **Phase 2: Generate Sub-Tasks:** Once the user confirms, break down each parent task into smaller, actionable sub-tasks:
    - **For PRD:** Infer technical implementation steps from functional requirements
    - **For FRD:** Use the detailed technical specifications, API specs, database changes, and deployment plans to create granular sub-tasks
    Ensure sub-tasks logically follow from the parent task, cover the implementation details, and consider existing codebase patterns where relevant without being constrained by them.
7.  **Identify Relevant Files:** Based on the tasks and document:
    - **For PRD:** Identify potential files based on feature scope and existing patterns
    - **For FRD:** Use the technical architecture section, file paths mentioned, and component names to identify specific files
    List these under the `Relevant Files` section, including corresponding test files if applicable.
8.  **Generate Final Output:** Combine the parent tasks, sub-tasks, relevant files, and notes into the final Markdown structure.
9.  **Save Task List:** Save the generated document in the same directory as the FRD: `/tasks/[n]-[feature-name]/tasks-[document-file-name].md`, where `[document-file-name]` matches the base name of the input document file (e.g., if the input was `/tasks/0001-user-profile-editing/0001-frd-user-profile-editing.md`, the output is `/tasks/0001-user-profile-editing/tasks-0001-frd-user-profile-editing.md`).

## Output Format

The generated task list _must_ follow this structure:

```markdown
## Relevant Files

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main component for this feature).
- `path/to/file1.test.ts` - Unit tests for `file1.ts`.
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `another/file.tsx`.
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts`.

### Notes

- Unit tests should typically be placed alongside the code files they are testing (e.g., `MyComponent.tsx` and `MyComponent.test.tsx` in the same directory).
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.

## Tasks

- [ ] 1.0 Parent Task Title
  - [ ] 1.1 [Sub-task description 1.1]
  - [ ] 1.2 [Sub-task description 1.2]
- [ ] 2.0 Parent Task Title
  - [ ] 2.1 [Sub-task description 2.1]
- [ ] 3.0 Parent Task Title (may not require sub-tasks if purely structural or configuration)
```

## Interaction Model

The process explicitly requires a pause after generating parent tasks to get user confirmation ("Go") before proceeding to generate the detailed sub-tasks. This ensures the high-level plan aligns with user expectations before diving into details.

## Target Audience

Assume the primary reader of the task list is a **junior to mid-level developer** who will implement the feature with awareness of the existing codebase context.

## Document Type Considerations

### Working with PRD:
- Tasks will be more exploratory and require inferring technical details
- Focus on translating user-facing requirements into technical tasks
- May need to make architectural decisions not specified in the PRD
- File paths and component names will be estimated based on existing patterns

### Working with FRD:
- Tasks will be more prescriptive and implementation-ready
- Leverage existing technical specifications, file paths, and code snippets
- Follow the phased implementation plan outlined in the FRD
- Use the FRD's task breakdown section as a starting point
- Include specific database migrations, API endpoints, and component names mentioned in the FRD
