# Stability and simplicity vs. features and complexity

_"Everything should be made as simple as possible, but not simpler." Einstein_

Stability and simplicity apply to the functionality of the system, the internal structure and code, as well
as the externals of the system such as the execution environment and dependencies.
Lets cover these in reverse order:

- _The externals_ - Avoid trivial externals. Before getting to the nub of this question, which is
  the definition of "trivial", let me explain the idea. These days we have components and libraries for just about
  everything. It may be tempting to use one of these for a UI component you don't want to write, to handle
  a file manipulation that would be irritating to code, but what happens when the authors of that component
  decide to stop supporting it, or even worse they don't manage their vulnerabilities as well as you and then
  introduce a supply chain attack into your software? Using externals leaves you with a codebase that needs constant upgrading. However, it also doesn't make sense to write everything yourself. You don't write your own operating system
  or database software. But where do you draw the line? We consider this to be a question of judgement but as a rule of thumb, if you
  can write the features you need from a dependency in 1-2 weeks, then you should consider it trivial and you really shouldn't be using it.

- _Internal structure and code_ - Write code to meet your known requirements. Attempting to cater for future
  scenarios that are uncertain and subject to change anyway will lead a team to over-engineer software, making it
  more complex, slower to extend and usually more brittle. This problem
  can be exacerbated by senior engineers who are trying do the right thing to avoid problems they may have
  experienced on another codebase,
  but instead end up introducing unnecessary complexity. We love Eric Lau's [hello world](https://github.com/eric19960304/hello-world-overengineering) that uses a complex class hierarchy and the factory design pattern
  to decouple everything from everything else and bring it back together to print "hello world".

- _Functionality of the system_ - Famously 80% of features in software systems are rarely or never used, or even worse
  they can have a negative effect. For example at Google and Bing 80%-90% of features have a negative impact on metrics.
  Business users and even some product owners will ask for features, describing the final solution, instead of helping
  developers understand the actual problem and work together to find a simple solution. Developers should always make an
  effort to understand and challenge the business problem before accepting the feature request.
