# Create PRP

## Feature file: $ARGUMENTS

Generate a complete PRP for general feature implementation with thorough research. Ensure context is passed to the AI agent to enable self-validation and iterative refinement. Read the feature file first to understand what needs to be created, how the examples provided help, and any other considerations.

The AI agent only gets the context you are appending to the PRP and training data. Assume the AI agent has access to the codebase and the same knowledge cutoff as you, so it's important that your research findings are included or referenced in the PRP. The Agent has web search capabilities, so pass URLs to documentation and examples.

## Research Process

1. **Codebase Analysis**
   - Search for similar features/patterns in the codebase
   - Identify files to reference in PRP
   - Note existing conventions to follow
   - Check test patterns for validation approach
   - Review build/deployment configurations

2. **External Research**
   - Search for similar features/patterns online
   - Framework/library documentation (include specific URLs)
   - Implementation examples (GitHub/StackOverflow/blogs)
   - Best practices and common pitfalls
   - Language-specific considerations

3. **User Clarification** (if needed)
   - Specific patterns to mirror and where to find them?
   - Integration requirements and where to find them?
   - Technology stack preferences?

## PRP Generation

Using PRPs/templates/prp_base.md as template:

### Critical Context to Include and pass to the AI agent as part of the PRP

- **Documentation**: URLs with specific sections
- **Code Examples**: Real snippets from codebase
- **Gotchas**: Framework quirks, version issues, compatibility notes
- **Patterns**: Existing approaches to follow
- **Dependencies**: Required packages/libraries/tools

### Implementation Blueprint

- Start with pseudocode showing approach
- Reference real files for patterns
- Include error handling strategy
- List tasks to be completed to fulfill the PRP in the order they should be completed

### Validation Gates (Must be Executable based on project tech stack)

**For Python projects:**
```bash
# Syntax/Style
ruff check --fix && mypy .
# Unit Tests
uv run pytest tests/ -v
```

**For JavaScript/Node.js projects:**
```bash
# Syntax/Style
npm run lint && npm run type-check
# Unit Tests
npm test
```

**For Java projects:**
```bash
# Syntax/Style
./gradlew checkstyleMain && ./gradlew spotbugsMain
# Unit Tests
./gradlew test
```

**For C# projects:**
```bash
# Syntax/Style
dotnet format && dotnet build
# Unit Tests
dotnet test
```

**For Rust projects:**
```bash
# Syntax/Style
cargo fmt --check && cargo clippy
# Unit Tests
cargo test
```

**For Go projects:**
```bash
# Syntax/Style
go fmt ./... && go vet ./...
# Unit Tests
go test ./...
```

**Generic fallback (adapt to project):**
```bash
# Syntax/Style
[PROJECT_LINTER] && [PROJECT_TYPE_CHECKER]
# Unit Tests
[PROJECT_TEST_RUNNER]
```

**CRITICAL AFTER YOU ARE DONE RESEARCHING AND EXPLORING THE CODEBASE BEFORE YOU START WRITING THE PRP**

**ULTRATHINK ABOUT THE PRP AND PLAN YOUR APPROACH THEN START WRITING THE PRP**

## Output

Save as: `PRPs/{feature-name}.md`

## Quality Checklist

- [ ] All necessary context included
- [ ] Validation gates are executable by AI for this tech stack
- [ ] References existing patterns
- [ ] Clear implementation path
- [ ] Error handling documented
- [ ] Dependencies and setup requirements specified
- [ ] Language/framework best practices incorporated

Score the PRP on a scale of 1-10 (confidence level to succeed in one-pass implementation using claude codes)

Remember: The goal is one-pass implementation success through comprehensive context.