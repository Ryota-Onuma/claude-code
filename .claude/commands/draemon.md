---
allowed-tools:
  - Bash(find:*)
  - Bash(git:*)
  - Bash(gh:*)
  - Bash(grep:*)
  - Bash(find:*)
  - Bash(ls:*)
  - Bash(cd:*)
  - Bash(git:*)
description: Complete workflow to read GitHub issue, implement solution, and create PR with structured task planning
---

# GitHub Issue to PR - Complete Workflow with Task Planning

Complete automated workflow to analyze a GitHub issue, create a structured implementation plan, implement the solution, and create a pull request.

## Pre-execution Context and Setup

### Repository Context Assessment

**First, I will gather the current repository state and issue information:**

1. **Current Repository State**

   - Check current branch: `git branch --show-current`
   - Check repository status: `git status --porcelain`
   - Review recent commits: `git log --oneline -5`

2. **Issue Information Gathering**

   - Extract issue number <ISSUE_NUM> from the provided issue URL: {{issue_url}}
   - Retrieve issue details: `gh issue view <ISSUE_NUM> --json title,body,labels,assignees,state,url,author`
   - Get issue comments: `gh issue view <ISSUE_NUM> --comments`

3. **Environment Verification**
   - Ensure GitHub CLI is authenticated: `gh auth status`
   - Verify repository access: `gh repo view`
   - Check for required tools (git, gh, package managers)

## Workflow Steps

### 1. Issue Analysis and Understanding

**First, I will analyze the GitHub issue #<ISSUE_NUM>:**

1. **Issue Summary**

   - Review the issue title, description, and any labels
   - Identify the problem type (bug fix, feature request, improvement, etc.)
   - Understand the scope and complexity of the required changes

2. **Requirements Extraction**

   - Parse acceptance criteria from the issue description
   - Identify any linked PRs or related issues
   - Note any specific technical requirements or constraints mentioned

3. **Impact Assessment**
   - Determine which parts of the codebase will be affected
   - Identify potential breaking changes or compatibility issues
   - Assess testing requirements

### 2. Comprehensive Codebase Investigation

**I will investigate the relevant code areas using the codebase-investigator:**

1. **Codebase Investigator Integration**

   - **Invoke codebase-investigator sub-agent** with the issue context and requirements
   - Provide investigation focus:
     - Issue description keywords and functionality areas
     - Scope of investigation (frontend/backend/full-stack)
     - Purpose (new feature/bug fix/enhancement)
     - Technology stack (if known)

2. **Investigation Execution**

   - Generate comprehensive codebase analysis report
   - Identify relevant files, patterns, and dependencies
   - Understand existing architecture and conventions
   - Map testing infrastructure and documentation

3. **Investigation Report Review**

   - Review the generated investigation report for accuracy
   - Extract key findings relevant to the issue implementation
   - Identify integration points and potential challenges
   - Note existing patterns to follow and pitfalls to avoid

**Expected Output**: A detailed `codebase-investigation-report.md` file containing:

```markdown
# Codebase Investigation Report for Issue #<ISSUE_NUM>

## Investigation Context

- **Purpose**: Implementation of issue #<ISSUE_NUM>
- **Keywords/Focus**: [Keywords from issue description]

## Executive Summary

[Key findings and recommendations for implementation]

## Relevant File Analysis

### Key Implementation Files

- Existing similar features or patterns
- Integration points for new functionality
- Dependencies and relationships

## Code Patterns and Conventions

- Architectural patterns to follow
- Naming conventions and code style
- Error handling and validation patterns

## Testing Infrastructure

- Existing test patterns and frameworks
- Coverage gaps and testing opportunities
- Mock strategies and test data patterns

## Recommendations

### For This Issue Implementation

- Specific patterns to follow
- Integration strategy
- Testing approach
```

### 3. Structured Implementation Planning

**I will create a comprehensive implementation plan using the project-task-planner:**

1. **Task Planner Integration**

   - **Invoke project-task-planner sub-agent** with the gathered issue information and codebase analysis
   - Provide context about:
     - Issue requirements and scope
     - Existing codebase structure and patterns
     - Technology stack and constraints
     - Work type classification (new feature/enhancement/bug fix/etc.)

2. **Plan Generation**

   - Generate structured `plan.md` file with detailed task breakdown
   - Ensure tasks are appropriate for the work type (Simple/Standard/Comprehensive format)
   - Include specific implementation steps, testing strategy, and deployment considerations

3. **Plan Review and Customization**

   - Review the generated plan for accuracy and completeness
   - Adjust tasks based on project-specific requirements
   - Prioritize tasks for efficient implementation order

**Expected Output**: A `plan.md` file with structured tasks like:

```markdown
# Issue #<ISSUE_NUM> Implementation Plan

## Work Context

- **Type**: [Bug Fix/New Feature/Enhancement]
- **Scope**: [Brief description]
- **Integration Points**: [How this connects to existing features]

## Phase 1: Preparation

- [ ] Create feature branch
- [ ] Set up development environment
- [ ] Review existing related code

## Phase 2: Implementation

- [ ] [Specific implementation tasks from planner]
- [ ] [Code changes needed]
- [ ] [Integration points to address]

## Phase 3: Testing & Validation

- [ ] [Testing tasks from planner]
- [ ] [Quality assurance steps]

## Phase 4: Documentation & PR Preparation

- [ ] [Documentation updates needed]
- [ ] [PR preparation tasks]
```

### 4. Branch Management

**I will set up the working environment following the plan:**

1. **Branch Creation**

   - Create a feature branch with a descriptive name based on the issue
   - Ensure the branch is up-to-date with the main branch
   - Format: `develop/<ISSUE_NUM>/<descriptive-name>`

2. **Environment Setup**
   - Install any new dependencies as specified in the plan
   - Run initial tests to ensure clean starting state

### 5. Plan-Driven Implementation

**I will implement the solution following the structured plan:**

1. **Execute Plan Tasks Systematically**

   - Follow the plan.md tasks in order
   - Check off completed tasks as I progress
   - Update the plan if adjustments are needed during implementation

2. **Core Implementation**

   - Implement the main functionality as planned
   - Follow existing code patterns and style guidelines identified in the plan
   - Add appropriate error handling and edge case coverage as specified

3. **Testing Implementation**

   - Execute testing tasks from the plan
   - Write comprehensive unit tests for new functionality
   - Update existing tests that may be affected
   - Add integration tests as specified in the testing strategy

4. **Documentation Updates**
   - Complete documentation tasks from the plan
   - Update code comments and inline documentation
   - Update README or other documentation files as needed
   - Add or update API documentation as specified

### 6. Validation and Quality Assurance

**I will validate the implementation following the plan's quality gates:**

1. **Code Quality Checks**

   - Run linting and formatting tools
   - Perform type checking (if applicable)
   - Check for security vulnerabilities or code smells
   - Verify all plan tasks are completed

2. **Testing Validation**

   - Run all relevant tests to ensure they pass
   - Verify test coverage meets plan requirements
   - Run manual testing scenarios from the plan

3. **Performance Validation (Optional)**
   - Check for performance regressions as specified
   - Validate memory usage and resource consumption
   - Test edge cases and error scenarios from the plan

### 7. Commit and PR Preparation

**I will prepare the changes for review:**

1. **Commit Strategy**

   - Create logical, atomic commits with clear messages
   - Follow conventional commit format if used in the project
   - Ensure each commit builds and tests pass
   - Reference the plan tasks in commit messages where appropriate

2. **PR Description Generation**

   - Generate comprehensive PR description explaining the changes
   - Include summary of plan execution and completed tasks
   - Link to the original issue
   - Include testing instructions and screenshots if applicable

3. **Final Validation**
   - Ensure all plan tasks are completed and checked off
   - Run final test suite
   - Verify branch is ready for review

### 8. Pull Request Creation

**I will create the pull request:**

1. **PR Creation**

   - Push the feature branch to origin
   - Create PR with generated description that includes plan summary
   - Add appropriate labels and reviewers
   - Include the content of plan.md in the PR body for reviewer reference

2. **PR Enhancement**
   - Add any necessary screenshots or demos, if you can
   - Include a checklist in the PR description based on the plan

## Success Criteria

- ✅ Issue requirements fully understood and addressed
- ✅ Comprehensive implementation plan created and followed
- ✅ All plan tasks completed and verified
- ✅ Clean, well-tested implementation following project patterns
- ✅ All existing tests continue to pass
- ✅ New functionality is properly tested per plan
- ✅ Code follows project style guidelines
- ✅ Documentation is updated as specified in plan
- ✅ PR is ready for team review with plan reference
- ✅ Clear commit history and PR description

## Post-Implementation Notes

After creating the PR, I will:

- Provide a summary of changes made with reference to the completed plan
- Highlight any deviations from the original plan and reasons
- Note any plan tasks that were modified during implementation
- Suggest next steps or follow-up tasks based on plan outcomes
- Note any potential risks or considerations for deployment from the plan

**Implementation Files Generated:**

- `plan.md` - Detailed task breakdown and implementation plan
- Feature implementation files as specified in the plan
- Test files as outlined in the testing strategy
- Updated documentation as specified

**Let's begin by analyzing GitHub issue #<ISSUE_NUM> and creating a structured implementation plan!**
