# Trade-offs

Things that arent trivial involve compromises. Trade-offs represent how we compromise between competing
factors. In software development we have no shortage of these factors and compromises, and in 10.10.0 applications 
we want to call them out explicitly and explain the decision-making behind the choices we made.

## Stability and simplicity vs features and complexity

_"Everything should be made as simple as possible, but not simpler." Einstein_

Stability and simplicity apply to the functionality of the system, the internal structure and code, as well
as the externals of the system such as the execution environment and dependencies. 
Lets cover these in reverse order:

- _The externals_ - Avoid trivial externals. Before getting to the nub of this question, which is
the definition of "trivial", let me explain the idea. These days we have components and libraries for just about
everything. It may be tempting to use one of these for a UI component you don't want to write, to handle
a file manipulation that would be irritating to code, but what happens when the authors of that component
decide to stop supporting it, or even worse they dont manage their vulnerabilities as well as you and then
introduce a supply chain attack into your software? Using externals leaves you with a codebase that needs constant upgrading. However, it also doesnt make sense to write eveything yourself. You dont write your own operating system
or database software. But where do you draw the line? We consider this to be a question of judgement but as a rule of thumb, if you
can write the features you need from a dependency in 1-2 weeks, then you should consider it trivial and you really shouldn't be using it. 


- _Internal structure and code_ - Write code to meet your known requirements. Attempting to cater for future
scenarios that are uncertain and subject to change anyway will lead a team to overengineer software, making it
more complex, slower to extend and usually more brittle. This problem
can be exacerbated by senior engineers who are trying do the right thing to avoid problems they may have
experienced on another codebase,
but instead end up introducing unnecessary complexity. We love Eric Lau's hello world (https://github.com/eric19960304/hello-world-overengineering) that uses a complex class hierarchy and the factory design pattern
to decouple everything from everything else and bring it back together to print "hello world".


- _Functionality of the system_ - Famously 80% of features in software systems are rarely or never used, or even worse
they can have a negative effect. For example at Google and Bing 80%-90% of features have a negative impact on metrics.
Business users and even some product owners will ask for features, describing the final solution, instead of helping
developers understand the actual problem and work together to find a simple solution. Developers should always make an
effort to understand and challenge the business problem before accepting the feature request.


## Community and open source vs suppliers and support contracts

The Open Source Security and Risk Analysis Report (https://www.synopsys.com/software-integrity/resources/analyst-reports/open-source-security-risk-analysis.html) found that 96% of codebases contain open source. It is a misconception
that if you sign a support contract with a big IT supplier, that you have your "bases covered". Too often these suppliers will restrict your options to a
limited set of expensive solutions, that are often the root cause of enterprises' problems. Use stable open source software and join their communities to support and
everage support, instead of relying on a big IT supplier contracts that will cost you an arm and leg but are wholly incapable
of supprorting all the components in your software stack.


## High quality high cost developers vs cost-optimized commodity developers

We are unashamedly developer centered. We love working in well crafted codebases written by skillful
developers who take pride in their craft and their code - these codebases are easy to extend and debug. Conversely we have
experienced the drag of working in poorly written codebases created by commodity developers. Commodity developers may be
cheaper per day, but they take many times longer to write anything so their overall cost is higher, but also the code
they write is a drag on all future developers who need to work on that codebase. Cheap commodity developers are a
false economy. 

