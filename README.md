# UiPath_Code_Review_Checklist
-------------

UiPath Code Review Checklist is a comprehensive list of items that can be used to review UiPath code for quality and best practices. This checklist is designed to help UiPath developers and reviewers ensure that their code is of high quality, maintainable, and meets industry standards.

The checklist is divided into several categories, each containing a list of items that should be reviewed during a code review. These categories include Process Architecture, Best Practices, Conventions & Annotations & Documentation, Security, Logging & Reporting, Dev Ops.

## License

[MIT](https://github.com/seymenbahtiyar/UiPath_Code_Review_Checklist/blob/main/LICENSE)

-------------
## Process Architecture

- [x] Use REFramework for transaction based processing
- [x] Ensure workflows are unit testable
- [x] Use configuration file accessible by the robot
- [x] Avoid unnecessary external dependencies
- [x] Implement REFramework stucture correctly
- [x] On exception messages, output at least Message, StackTrace, Source, Inner exception, if an exception is encoutered
- [x] Use BusinessRuleExceptions and SystemExceptions properly
- [x] Ensure the process flow and workflows are easy to read and understand
- [x] Avoid big workflows, with more than 30-50 activities
- [x] If an workflow is big, break the implementation in smaller workflows with more specific scope
- [x] Implement/review transaction retry mechanism in accordance with the process and code. (Auto Retry property in Orchestrator Queue)
- [x] Adapt transaction reference information to the process. Care should be taken to observe the string character limit of the reference, which is 128 characters. (Enforce unique references property in Orch. Queue and Reference property in Add Queue Item activity in Studio)
- [x] Handle fatal errors encountered in the Framework Init state, and transition the process to a faulted state (if necessary, send an error email to the process owner).
- [x] Transition the process to a faulted state if all transactions encounter system exception type errors. (This can be important to view it as faulted to prevent a transaction-based error.)

## Best Practices

- [x] Use folders with an appropriate naming to store the relevant xaml files for a part of a process
- [x] Workflows can be ran without launching the entire process (by modifying arguments/conditional loading/using a test workflows xaml)
- [x] Selector based activities are used when possible (i.e. less usage of Image automation)
- [x] Workflows are designed to be reusable
- [x] No more than 2 nested If activities, if the logic is more complex, try using a switch/else if/flowchart instead.
- [x] SendWindowMessages and Simulate interactions are used
- [x] Avoid nested Try Catches (difficult to see where the exception comes from; if required, add an annotation with the reason)
- [x] Static delays are not used
- [x] Exception messages are meaningful
- [x] Replace delay activities with exception handling method: Element Exists/On element appear/Pick branches or similar
- [x] Code is clean - unused workflows, activities, variables/arguments are removed
- [x] No selector with idx (if they are needed, an annotation should be added with the reason)
- [x] Selectors do not have overly specific information
- [x] Use partial selectors when several activities are executed in the same window (usage of containers)
- [x] Hardcoded values should not be used in the code (use config file or a variable suitable for the code)
- [x] The code should not contain structures that may cause an infinite loop. (This can be checked using the Workflow Analyzer in Studio.)
- [x] The transaction processing speed, CPU usage and RAM usage should be observed and optimized during runtime.


## Conventions & Annotations & Documentation

- [x] Arguments follow naming convention (prefixed with `in_`/`out_`/`io_`, A combination of snake and camel case in_Written_Like_This)
- [x] Variables should follow naming convention (A combination of snake and camel case var_Written_Like_This)
- [x] Workflows follow naming conventions
- [x] Workflows have a top level annotation
- [x] Each activity has a meaningful name and/or annotation
- [x] Each workflow has a meaningful name and a meaningful annotation
- [x] Each variable has a meaningful name, and a specific scope
- [x] Complex or unintuitive parts of the process documented


## Security

- [x] Queue items do not store sensitive data
- [x] No credentials stored in workflows or config file (use assets and config file)
- [x] No hardcoded sensitive data inside workflows or config file
- [x] No sensitive data is logged or stored inside workflows/logs


## Logging & Reporting

- [x] Avoid excessive logging during runtime to prevent performance bottlenecks and ensure proper database usage
- [x] Use logs at the beginning and end of a workflow to track the current process status
- [x] Log errors appropriately
- [x] Use appropriate log levels
- [x] Generate reports that provide details on bot executions

## Dev Ops

- [x] All code is contained in source control (GitHub, GitLab, Fileserver etc.)
- [x] CI/CD is configured for this automation






