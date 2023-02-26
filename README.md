# UiPath_Code_Review_Checklist



## Process Architecture

- [ ] Use REFramework for transaction based processing
- [ ] Ensure workflows are unit testable
- [ ] Use configuration file accessible by the robot
- [ ] Avoid unnecessary external dependencies
- [ ] Implement REFramework stucture correctly
- [ ] On exception messages, output at least Message, StackTrace, Source, Inner exception, if an exception is encoutered
- [ ] Use BusinessRuleExceptions and SystemExceptions properly
- [ ] Ensure the process flow and workflows are easy to read and understand
- [ ] Avoid big workflows, with more than 30-50 activities
- [ ] If an workflow is big, break the implementation in smaller workflows with more specific scope
- [ ] Implement/review transaction retry mechanism in accordance with the process and code. (Auto Retry property in Orchestrator Queue)
- [ ] Adapt transaction reference information to the process. Care should be taken to observe the string character limit of the reference, which is 128 characters. (Enforce unique references property in Orch. Queue and Reference property in Add Queue Item activity in Studio)
- [ ] Handle fatal errors encountered in the Framework Init state, and transition the process to a faulted state (if necessary, send an error email to the process owner).
- [ ] Transition the process to a faulted state if all transactions encounter system exception type errors. (This can be important to view it as faulted to prevent a transaction-based error.)

## Best Practices

- [ ] Use folders with an appropriate naming to store the relevant xaml files for a part of a process
- [ ] Workflows can be ran without launching the entire process (by modifying arguments/conditional loading/using a test workflows xaml)
- [ ] Selector based activities are used when possible (i.e. less usage of Image automation)
- [ ] Workflows are designed to be reusable
- [ ] No more than 2 nested If activities, if the logic is more complex, try using a switch/else if/flowchart instead.
- [ ] SendWindowMessages and Simulate interactions are used
- [ ] Avoid nested Try Catches (difficult to see where the exception comes from; if required, add an annotation with the reason)
- [ ] Static delays are not used
- [ ] Exception messages are meaningful
- [ ] Replace delay activities with exception handling method: Element Exists/On element appear/Pick branches or similar
- [ ] Code is clean - unused workflows, activities, variables/arguments are removed
- [ ] No selector with idx (if they are needed, an annotation should be added with the reason)
- [ ] Selectors do not have overly specific information
- [ ] Use partial selectors when several activities are executed in the same window (usage of containers)
- [ ] Hardcoded values should not be used in the code (use config file or a variable suitable for the code)
- [ ] The code should not contain structures that may cause an infinite loop. (This can be checked using the Workflow Analyzer in Studio.)
- [ ] The transaction processing speed, CPU usage and RAM usage should be observed and optimized during runtime.


## Conventions & Annotations & Documentation

- [ ] Arguments follow naming convention (prefixed with `in_`/`out_`/`io_`)
- [ ] Variables should follow naming convention
- [ ] Workflows follow naming conventions
- [ ] Workflows have a top level annotation
- [ ] Each activity has a meaningful name and/or annotation
- [ ] Each workflow has a meaningful name and a meaningful annotation
- [ ] Each variable has a meaningful name, and a specific scope
- [ ] Complex or unintuitive parts of the process documented


## Security

- [ ] Queue items do not store sensitive data
- [ ] No credentials stored in workflows or config file (use assets and config file)
- [ ] No hardcoded sensitive data inside workflows or config file
- [ ] No sensitive data is logged or stored inside workflows/logs


## Logging and Reporting

- [ ] Avoid excessive logging during runtime to prevent performance bottlenecks and ensure proper database usage
- [ ] Use logs at the beginning and end of a workflow to track the current process status
- [ ] Log errors appropriately
- [ ] Use appropriate log levels
- [ ] Generate reports that provide details on bot executions

# Dev Ops

- [ ] All code is contained in source control
- [ ] CI/CD is configured for this automation






