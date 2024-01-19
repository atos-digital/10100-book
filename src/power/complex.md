# Avoid complex functions

We like Nasa's rule 4 (Restrict functions to a single printed page) but we're worried
someone will take it literally ([Elon Musk!](https://www.reddit.com/r/OutOfTheLoop/comments/yjhw2o/whats_up_with_the_elon_musk_code_printing_thing/)). So lets go with limiting [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) to 10 (warning), and 15 (critical defect). Setup a [linter](https://golangci-lint.run/usage/linters/) to show this early on.
