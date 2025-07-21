# major-projects-overview
A walk-through of major projects I've worked on that are worth discussing.

> Note: Due to the public nature of this repository, I will need to keep certain company and product names confidential

## Summary
Over 4 1/2 years at _a major financial institution_, I led two major AI/ML initiatives:
1. **Model Explainability Tool** - a web-based application that allowed model developers a better way to keep track their experimentation runs and results during the model development phase. On this project I was the UI tech lead.
2. **Machine Learning Platform** - a enterprise platform with web, CLI, API, & SDK interfaces that sped up the process of getting a model to production by providing compliant tooling for model experimentation, training, serving, monitoring, and re-fitting. On this project I was the Senior Manager of the UI team, and eventually acting director over the developer experience group.

Throughout my tenure I played a critical role in architectural decisions, performance management, project management, program management, customer engagement, incident management, as well as varying levels of individual contribution when necessary.

## Project - Model Explainability Tool

### Role & Tech
I was brought to the organization to lead the UI team as a tech lead (manager level IC). The back-end of the application was Python, with the front-end being React. PostgreSQL and Cassandra were leveraged at the data layer. Our SDK was a python package that model developers could import and call to record metrics and metadata about the results of their experimentation runs. The UI communicated with the Python back-end via a RESTful API.

### Notable Contributions
Upon joining the organization, my first order of business was to understand the architecture of the application and address performance bottlenecks. I idenfied the following:
* The majority of our screens followed one of three patterns, but no libraries/utilities/common components existed to make the process of creating new screens (which would follow the same patterns) faster
* The UI did not adhere to any of the (7!?!?!?) corporate design systems
* One call to the DB was taking 40+ seconds (often timing out) to respond, and consisted of individual queries that had already been ran to populate other parts of the UI
* While the CI/CD pipeline was already defined by the enterprise, our monitoring and alerting were not yet in compliance (there was none)
* Our enterprise access control integration was out of compliance (anybody could access anything), and integrating with it was going to create the worst user experience possible based on how our customers used our application

Our application was not yet in production, but needed to check several boxes before it could be. I put together a plan for what I could tackle and executed on the following changes:

#### Simplification and Consolidation of Front-end Code
I implemented patterns, reusable components, and best practices to address our inability to add features quickly. This brought our time to implement a new screen down from days to hours. I was able to present the changes to the other team members in a way that was well recieved and followed with very little to no pushback. The team and stakeholders were ultimately happy with the changes.

#### Design System
I was able to implement one of the corporate design systems, and task other team members with implementing the changes across the board.

#### Slow DB Calls
The slow DB call was a calculation ran across the entire dataset for a given project, which required all of the data to be queried, calculations ran, and large datasets returned. When several customers used our system at the same time, this caused massive bottlenecks. I was able to re-write the feature leveraging queries that had already been ran previously when loading the screen, and moving the calculations to the client in a web worker to allow the application to perform better all around. (Note - there are much better ways to handle this today).

#### Monitoring & Alerting
I set our team up with Pagerduty and integrated Datadog into our backend in order to monitor application performance and notify team members when issues arose, typically before customers were experiencing them. (Note - ask me about the "Service Unavailable" incident that our monitoring did not capture, and the lessons learned!)

#### Access Control
This could have been it's own project, and I'll spend a bit of time explaining this. My work on this ultimately led to a promotion.

Our enterprise access control system controlled users' access to everything through RBAC / entitlements. In order to access any application, a user had to have the appropriate role(s) (entitlements). The entitlements followed some naming convention similar to:

`our-product-access`

For our product, users had one entitlement, but that meant every user could access everything. We were allowed to build our own access control system as long as it was integrated with the enterprise solution, which ours was not. Our users could sometimes spin up 100 projects in a day, which means they would have to get an entitlement for each project, which was not feasible.

I came up with the idea of introducing a Teams construct that users could get entitlements for, which would allow them access to any projects owned by teams they were a part of, and they only had to get new entitlements when they joined a new team. I assigned the work for this to our backend engineers to implement.

One problem that arose, however, was the difficulty for users to find the entitlements they needed. Aws, for example, with it's 2.7 trillion cloud products (I counted them last week), might have entitlement structures that look like this:

`aws-a32-user-ADMIN-245Aq-ALLOW_S3`

The access control system had an interface where users could search for entitlements and request them. For many entitlements, such as the made-up AWS entitlement above, it was nearly impossible to know exactly which entitlement you needed. Often times requesting an entitlement (and then waiting 24-48 hours for approval) would result in a rejection because you didn't request the right one. Or sometimes it would be approved, but you still wouldn't have access to the thing you needed because it was the wrong entitlement.

Bananas.

When logging into any application through SSO, the application would know 2 things: A) your ID and B) the entitlement you need but don't have. The user would know 3 things: A) their ID B) the ID of the person who needs access, which is usually theirself, and C) why they need access. In order to make an entitlement request, 4 pieces of information were needed:

* The ID of the requester
* The ID of the person who needs the entitlement
* The business justification for why the entitlement should be granted
* The exact name of the entitlement

I realized that applications know, inherently, the first and last requirements. The authenticated user knows the other two. So instead of sending our users to a separate website to request an entitlement they aren't confident they even know they need, why not just prompt the user for "who is this for?" and "what is your business justification?" Our app knows the rest, we can collect the info and pass it along to the access control system's API!

Brilliant! Except the access control system would sometimes respond with a 200, and it worked. Sometimes it would timeout. Sometimes it would error. Sometimes it would respond with a 200 but it actually timed out.

More bananas.

So I instructed the backend team to build a proxy service that would store the request details, continuously make the request until the service responded with "already created," and our problems were solved.

> Note - We leveraged this same implementation for the other project, the Machine Learning Platform, and when we presented this specific feature during a demo at an internal conference, the room erupted with a standing ovation. This solved one of the most painful experiences in the entire company.

### Post Production Launch
After our product went to production, everyone was happy, but I wasn't happy with customer adoption. We had people within our department who weren't even using our tool. I reached out to several customers to have them walk me through how they did their job, specifically the part where our app would normally benefit them. I discovered that our information architecture was backwards (we had the metadata and experiment data display mixed up). After implementing this change, our product adoption skyrocketed. I was asked to lead a larger team on a larger project, our product was granted a patent, we won the company-wide Tech Excellence award, and we eventually open-sourced the product.
