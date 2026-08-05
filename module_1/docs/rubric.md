# 1. Quality Rubric

## 1.1 Dimensions

### 1.1.1 Build Result Accuracy

Measures whether the agent correctly identified the final outcome of the Docker build. A high score requires the stated result, success or failure, to match the actual exit status of the build command.

### 1.1.2 Warning and Error Coverage

Measures whether the summary fully captured all errors at any level. A high score requires capturing all errors and warnings, missing minor warnings = partial credit, missing major errors = failure.

### 1.1.3 Command Traceability

Measures if the agent correctly reported all three elements necessary for full credit: identified the command, named its source, as well as confirmed the build fully executed.

### Alternatives considered

A binary pass/fail checklist with one item per acceptance criterion. Ruled out because it cannot distinguish a near-miss from a complete failure, and cannot capture partial credit.

Also considered pass/fail subtasks beneath each numbered dimension where all must be pass to make the top level pass. Ruled out because it added unnecessary nesting and complexity without adding any functionality the graduated dimension didn't already provide.

## 1.2 Scoring Guide

### 1.2.1 Build Result Accuracy

Build result accuracy measures whether the agent correctly identified the final outcome of the Docker build.

Does not meet: Reports the wrong build outcome, or does not report an outcome at all.

Partially meets: Reports the outcome ambiguously or with missing context, e.g., says "the build had issues" without stating pass or fail.

Meets: Correctly identifies whether the Docker image built successfully or failed.

Exceeds: Correctly identifies the outcome and includes supporting evidence, such as the exit code or the final line of build output.

### 1.2.2 Warning and Error Coverage

Warning and error coverage measures how completely the agent captured warnings and errors from the build output in its summary.

Does not meet: The summary omits one or more errors that appeared in the build output. A reviewer reading only the summary would have an incomplete or misleading picture of what went wrong.

Partially meets: The summary captures all errors but omits one or more warnings. The picture is not misleading, but it is incomplete.

Meets: The summary captures all errors and all warnings present in the build output. Nothing material is missing.

Exceeds: The summary captures all errors and warnings, groups or prioritizes them, so the most important issues are immediately visible without requiring the reviewer to read the full log.

### 1.2.3 Command Traceability

Command traceability measures whether the agent's report of the build command it used can be verified and trusted by a reviewer.

Does not meet: Reported nothing or reported incorrect information, such as naming a command not actually in the Dockerfile, reporting execution that didn't happen, or reporting a command location that does not exist.

Partially meets: Reported one or more elements (exact command, cited source, confirmed execution) but omitted others or gestured vaguely. Not misleading but incomplete.

Meets: Included all three elements: identified command, listed exact location, and confirmed execution completion. Nothing material is missing.

Exceeds: Captured all elements completely, with each of the three elements (command, source, execution) clearly tagged or labeled so a reviewer can scan them instantly rather than parse prose. Flags if the documented command differs from what is needed and suggests locations of alternatives.

## Pass Threshold
A run is passing if it scores 3 or higher on all dimensions.
Reasoning: A Docker review agent that gets the build result wrong, or fabricates a command trace, is producing something actively misleading, regardless of how well it performs elsewhere. This dimension floor prevents a strong score on one dimension from masking a failure on another.

## Notes on Threshold Design
Considered an aggregate minimum of 9 out of 12 instead of a dimension floor. Ruled out because it would allow a run scoring 1 on Build Result Accuracy to pass if it scored 4 on the other two dimensions. Reporting the wrong build outcome makes the agent's core function untrustworthy, and no amount of clear reporting or thorough coverage elsewhere can compensate for that.