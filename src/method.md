# Methodology

We have built a number of 10.10.0 applications for enterprise and share our methodology here. This is our method
and serves only as a suggestion.

In 10.10.0 applications, a squad of engineers engage with a client product owner to understand a business problem.
There are no layers of consultants, analysts, etc between the engineers and product owner. Engineers must
understand the business problem and challenge any proposed solutions.

Once the problem and solution approach are defined, the engineering team will use Vision to spin up a project and
test environment within a day. The engineers will deliver a small set of features by the end of the week and
start a process of weekly feature demos with the client product owner, iterating the solution weekly and getting
the application into production and in business use as soon as possible.

Engineers are responsible for writing unit tests and modifying the end-to-end tests as part of their development workflow. By thinking about testing at the start, engineers can write more testable code which is generally higher quality and provides better automated test coverage and lower defects.

Once the application meets its requirements, development can stop and the engineering team can move on to another
project. If the product owner needs further features built, the team and pick it up ad hoc. There will be no need
for large complex and expensive upgrade projects the next time the codebase needs to be extended.

An example timeline is shown below:

- Week 1:

  - Meet the users / product owner, and understand the business problem to be solved
  - Explain the journey to the users, with specific emphasis on the demands on users time
  - Develop a view of the functionality and create an initial set of standalone (no integration) feature tickets
  - Bootstrap the frontend and backend code using a template
  - Deploy a demo environment in the cloud
  - Develop the initial set of frontend and backend tickets
  - At the end the week demo the application to the users. Users will be able to 'touch and feel' the system, and will start to develop a view on how the system could be used.
  - Refine and prioritise tickets for week 2, including core business logic and integration tickets

- Week 2:

  - Access to integration testing environments
  - Raise any requests for the production environment
  - Engage any required operational teams
  - Setup CD to production
  - Tickets
  - End of week demo
  - Users get access to test environment to test
  - Define UAT tests

- Week 3-7:

  - Tickets
  - End of week demo
  - Refine and prioritise tickets for next week

- Week 8:

  - UAT
  - Defect fixing

- Week 9:

  - Final user testing and defect fixes
  - Complete any acceptance into service steps

- Week 10:
  - System is live
  - live support
