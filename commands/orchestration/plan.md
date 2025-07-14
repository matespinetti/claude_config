---
description: Plan development tasks with professional git workflow in mind
---

What I want to accomplish: $ARGUMENTS

Please create a professional development plan:

1. **Requirement Analysis**: What exactly needs to be built?
2. **Context Integration**: How does this fit with existing code/patterns?
3. **Technical Approach**: What's the best approach for this project's stack?

4. **Working Unit Breakdown**: Organize work into logical, complete units:
   - Each working unit should represent complete, testable functionality
   - Units should be safe to commit (won't break the build)
   - Each unit should be reviewable as a logical change
   - Format:
     ```
     ## Development Plan

     ### Working Unit 1: Backend Foundation
     **Goal**: Complete backend API that can be tested
     - [ ] Create data models and schemas
     - [ ] Implement core API endpoints
     - [ ] Add input validation and error handling
     - [ ] Write unit tests for backend logic
     - [ ] Test API endpoints manually/with tests
     **Commit Point**: When backend is working and tested

     ### Working Unit 2: Frontend Implementation
     **Goal**: Complete UI that integrates with backend
     - [ ] Create UI components and forms
     - [ ] Implement API integration
     - [ ] Add error handling and loading states
     - [ ] Style components appropriately
     - [ ] Test user interactions
     **Commit Point**: When frontend is working and integrated

     ### Working Unit 3: Integration & Polish
     **Goal**: Feature is complete and production-ready
     - [ ] End-to-end integration testing
     - [ ] Performance optimization if needed
     - [ ] Documentation updates
     - [ ] Code review preparation
     - [ ] Final testing and edge cases
     **Commit Point**: When feature is complete and ready for review
     ```

5. **Quality Standards**: Testing and review expectations
6. **Integration Strategy**: How this affects the broader codebase

**IMPORTANT**: After creating this plan, ask me if I want you to:
- Implement all working units with appropriate commits
- Implement one working unit at a time with my approval  
- Just provide the plan for manual implementation

Each commit will represent a complete, working piece of functionality.
