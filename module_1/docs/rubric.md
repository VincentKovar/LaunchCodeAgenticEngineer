

# 1. Quality Rubric

## 1.1 Dimensions

### 1.1.1 Build Result Accuracy

Measures whether the agent correctly identified the final outcome of the Docker build. A high score requires the stated result, success or failure, to match the actual exit status of the build command.

### 1.1.2 Warning and Error Coverage

Measures whether the summary fully captured all errors at any level. A high score requires capturing all errors and warnings, missing minor warnings = partial credit, missing major errors = failure. 

### 1.1.3 Command Traceability

Measures if the agent correctly reported all three elements necessary for full credit: identified the command, named its source, as well as confirmed the build fully executed. 

### Alternatives considered: 
A binary pass/fail checklist with one item per acceptance criterion. Ruled out because it cannot distinguish a near-miss from a complete failure, and cannot capture partial credit. 

Also consdiered pass/fail subtasks beneath each numbered dimension where all must be pass to make the top level pass. Ruled out because it added unnecessary nesting and complexity without adding any functionality the graduated dimension didn't already provide.