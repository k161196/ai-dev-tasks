# Rule: Generating a Feature Requirement Document (FRD)

## Goal

To guide an AI assistant in creating a detailed Feature Requirement Document (FRD) in Markdown format, based on an initial user prompt. The FRD should be technical, implementation-focused, and actionable for developers to build the feature.

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the FRD, the AI *must* ask clarifying questions to gather technical and implementation details. The goal is to understand the "what," "why," and "how" of the feature. Make sure to provide options in letter/number lists so I can respond easily with my selections.
3.  **Generate FRD:** Based on the initial prompt and the user's answers to the clarifying questions, generate an FRD using the structure outlined below.
4.  **Save FRD:** Save the generated document in a nested directory structure: `/tasks/[n]-[feature-name]/[n]-frd-[feature-name].md`. (Where `n` is a zero-padded 4-digit sequence starting from 0001, e.g., `/tasks/0001-user-authentication/0001-frd-user-authentication.md`, `/tasks/0002-dashboard/0002-frd-dashboard.md`, etc.)

## Clarifying Questions (Examples)

The AI should adapt its questions based on the prompt, but here are some common areas to explore:

*   **Problem/Goal:** "What problem does this feature solve? What is the business/technical rationale?"
*   **Target User/System:** "Who/what will interact with this feature? (end users, internal systems, APIs, etc.)"
*   **Core Functionality:** "What are the key technical components required? What actions should the system perform?"
*   **User Stories/Use Cases:** "Can you provide user stories or use cases? (e.g., As a [user], I want to [action] so that [benefit])"
*   **Technical Stack:** "What technologies, frameworks, or services should be used? (e.g., React, Node.js, PostgreSQL, Redis)"
*   **Data Requirements:** "What data models/schemas are needed? What are the data sources?"
*   **Integration Points:** "Does this feature need to integrate with existing systems/APIs/services?"
*   **Performance Requirements:** "Are there specific performance, scalability, or latency requirements?"
*   **Security/Privacy:** "Are there authentication, authorization, or data privacy requirements?"
*   **Error Handling:** "What error scenarios should be handled? What are the fallback behaviors?"
*   **Testing Strategy:** "What testing is required? (unit, integration, e2e, performance)"
*   **Deployment:** "How should this be deployed? Any environment-specific considerations?"
*   **Monitoring/Logging:** "What metrics, logs, or alerts should be implemented?"

## FRD Structure

The generated FRD should include the following sections:

1.  **Title & Overview:** Feature name and brief description (1-2 paragraphs) of what it does and why it's needed.
2.  **Critical Issues/Background:** Context about the problem this solves. Link to related tickets, PRs, or documentation if applicable.
3.  **Goals & Success Metrics:** Specific, measurable objectives and how success will be measured.
4.  **User Stories/Use Cases:** Detailed user narratives describing feature usage and expected behaviors.
5.  **Implementation Plan:** Phased breakdown of development work:
    *   **Phase 1:** Core functionality (MVP)
    *   **Phase 2:** Enhancements and additional features
    *   **Phase 3:** Optimization and polish (if applicable)
6.  **Technical Architecture:**
    *   System architecture diagram (ASCII/text or link to diagram)
    *   Component breakdown
    *   Data flow description
    *   Technology stack
7.  **Database Changes:**
    *   New tables/collections
    *   Schema modifications
    *   Migration scripts
    *   Indexes required
8.  **API Specifications:**
    *   Endpoints (method, path, description)
    *   Request/response schemas
    *   Authentication/authorization requirements
    *   Rate limiting considerations
9.  **Frontend Requirements:**
    *   UI components needed
    *   State management approach
    *   User interactions and workflows
    *   Responsive design considerations
10. **Error Handling & Edge Cases:**
    *   Expected error scenarios
    *   Validation rules
    *   Fallback behaviors
    *   User-facing error messages
11. **Testing Strategy:**
    *   Unit tests (what to test)
    *   Integration tests
    *   E2E test scenarios
    *   Performance/load testing (if applicable)
12. **Monitoring & Logging:**
    *   Metrics to track
    *   Logs to capture
    *   Alerts to configure
    *   Dashboard requirements
13. **Security Considerations:**
    *   Authentication/authorization
    *   Data validation
    *   Sensitive data handling
    *   Potential vulnerabilities
14. **Performance Considerations:**
    *   Expected load/traffic
    *   Caching strategy
    *   Database query optimization
    *   CDN usage
15. **Task Breakdown:** Numbered, actionable tasks for developers:
    *   [ ] Task 1: Create database migrations
    *   [ ] Task 2: Implement backend API endpoints
    *   [ ] Task 3: Build frontend components
    *   etc.
16. **Dependencies:**
    *   External libraries/packages
    *   Third-party services
    *   Internal services/modules
    *   Infrastructure requirements
17. **Deployment Plan:**
    *   Environment configuration
    *   Feature flags
    *   Rollout strategy
    *   Rollback plan
18. **Open Questions:** List any remaining questions or areas needing further clarification.
19. **Status:** Current state (e.g., Draft, In Review, Approved, In Progress, Completed)
20. **Versioning:** Document version and change history

## Target Audience

Assume the primary reader is a **developer** (junior to mid-level). Requirements should be technical, specific, and implementation-ready. Include:
- File paths and directory structure
- Class/function/component names
- Code snippets (TypeScript, SQL, Bash, etc.)
- Configuration examples
- Command-line instructions

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/tasks/`
*   **Filename:** `[n]-[feature-name]/[n]-frd-[feature-name].md`

## Final Instructions

1. DO NOT start implementing the FRD
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the FRD
4. Include code snippets, file paths, and technical details throughout the document
5. Ensure the FRD is detailed enough that a developer can start implementation immediately
