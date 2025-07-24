---
layout: page
title: "Machine Learning Platform"
permalink: /machine-learning-platform/
---

# Machine Learning Platform

## Overview

The _Machine Learning Platform_ at _a major financial institution_ was an idea to unify adhoc tools in the model development space and create a unified platform to enhance the user experience and, ultimately, speed up the process of getting models into production. In a highly regulated industry model governance rules differed depending on business intent which often times led to extended and unecessary cycles of back and forth between model developers, data scientists, platform teams, and model risk officers. The platform was intended to solve this.

## Getting Started

At the start of the project, three products existed already:

* Experimentation - A visual tool for spinning up infrastructure to run Jupyter Notebooks (this product was to be replaced)
* Features - A visual / API tool for browsing and registering available Features (data) within the company
* Serving - An API tool for serving models in production

In development were:
* Progression - a tool that read a YAML file within the model repository in order to progress a model to production
* Model Catalog - a visual / API tool that allowed model developers to publish information about their built models to the enterprise

My team of 6 was formed to create, initially, the UI that would replace the Experimentation tool and also act as the eventual home for the unified UI for all of the related tools. I worked directly with product and design leadership to establish a delivery plan that met enterprise compliance and design standards, accomplished a major demo for a company-wide event within 60 days, and establish key success indicators for the project as a whole.

I started the initial repo and established the organizational patterns we would follow to get the team going. I facilitated discussions between the UI team and backend teams that were building APIs to ensure consistency, understanding, and establish contracts between systems. I assigned roles within the team for managing the day-to-day agile ceremonies (we rotated through responsibilities to empower the team to bias towards action and increase empathy). I setup our team to mostly self-assign work and communicate externally what our timeline and deliverables were. As an organization, we followed SAFe agile practices.

## Design Thinking

I engaged with the design research and product teams to start and lead sessions with 2 distinct groups of customers - ML Engineers/Data Scientists (the primary customer), and Model Risk Officers (the people who ultimately approve a model's deployment to production). This customer engagement led to 3 critical insights:

* There absolutely existed a specific, required model development lifecycle within the org
* The model risk officers individually could tell you ~90+% of the process from memory
* The model developers collectively could identify the process, but on their own had no clue

This exposed a need in our information architecture to ensure that we were correctly guiding users naturally, while also giving them access to the right tools at the right time (and restricting access to tools that they couldn't use yet). I influenced the decision with product and design to get this implemented, which created a high level of speed and clarity for users.

## Further Technical Pieces

There are many other examples I could dive into of technical involvement, such as sitting on the enterprise machine learning architectural council, identifying opportunities for team members to contribute to open-source projects in a way that further unified platforms and the user experience, or empowering other teams to be able to deploy micro-experiences within our application to speed up the deployment process. I will instead shift to more managerial / leadership topics.

## Growth & Performance Management

Eventually the success of my team led to more responsiblities, and I was given the green light to hire 3 Senior Managers reporting directly to me with their own teams across UX, API, and SDK (collectively the "DX Group").

I was a key contributor and "Bias Ambassador" for our organization's performance management process, participating in 9 different cycles over 4.5 years with other people managers. I hired ~25 people, including 4 college grads from our internal transition program. I performed regular 1:1's with direct reports, skip-levels, peers, and other key individuals across the organization where it made sense. I promoted 5 people within my direct organization.

## Critical Conversations

### Cross-team Collaboration

The team building the new Experimentation tool made several unilateral decisions that had an large impact on multiple teams. Some of the public conversations between teams became heated and created tension. I met with key members and leaders of the teams to push everyone towards resolution (some was through concession, some was through "disagree and commit," some was through agreement). I proposed the idea that all of this was "healthy friction," which everyone agreed, and was able to publicly acknowledge the friction and resolution in a way that go everyone on the same page and back to great collaboration and teamwork again.

### Individual Contributors

There were, unfortunately, a few individuals within the organization that were having an overall negative impact. Here are some of those and how I addressed them:

* Three members of my direct team were severely underperforming in their roles as engineers.
  * I moved one of the engineers into a role within a new team and everyone absolutely flourished. This was just a case of being in the wrong seat on the bus.
  * 2 of the engineers I had to have several conversations with before ultimately putting them on a PIP. One left voluntarily later, while the other had to be let go after continuing to under perform. I would like to note that the one who voluntarily left needed to leave, while the one who continued to underperform still pulls at my heartstrings because they really did try their best and I felt like I failed at helping them succeed. Both of these cases were the wrong people being on the bus.
* One member of a sister team was habitually making unilateral decisions that were negatively impacting other teams. I spoke with this person directly to address the issues, candidly, and eventually worked with them and their manager to develop better practices. This person turned it around and was later promoted.

Two individuals, one on my team and one on a sister team, experienced repeated high levels of personality clash with each other. Individually and within their respective teams, both were highly regarded and top contributors, but they were unable to collaborate together. I met with them individually to get context and a better assessment of the real issues. Ultimately the decision was to reduce, as much as possible, any requirement for the two of them to have to collaborate, and after any collaboration I would give them both an opportunity to vent (scream) at me (or each other, once) in private to not disrupt the team and get everyone focused on delivering value. Both members were eventually promoted and had successful careers, being force-multipliers within their respective teams.

### Managing Managers

One of the senior managers reporting to me was, as reported by their direct reports, struggling to connect with their team. While the output of the team was, from a metrics perspective, above the metrics of peer teams, the morale of the team was incredibly low. I was not able to get this senior manager to correct their patterns that were causing negativity on the team, so I eventually moved them into a more hands-on role with other engineers that would work well in that environment, while moving the negatively affected engineers to a different team where there would be a better fit. The ultimate result was significantly increased morale, sustained productivity, and positive feedback from everyone on the team.

Another senior manager reporting to me had a direct report who was severely underperforming. I worked together with this manager and supported them through developing a coaching plan for the individual, as well as documenting the issues. The manager was able to successfully get the engineer back on track and contributing at the expected level.

### Managing Up

A key non-technical product manager overhead a very influential customer say the phrase "I don't want a UI, I want an SDK." The product manager took this literally and began to advocate for the dismantling of what my team had built. I reached out to the customer for more context and discovered that what they were referring to was wanting an SDK to use while building the model, not while spinning up infrastructure. They loved the UI. I approached the PM with context, humbly, to educate them on the model development lifecycle within our org, where the UI fit in, and where the SDK fit in. The end result was my team owning the UI, the API, and the SDK.

### Managing Delivery (and Hype)

At the scale of this organization, it was critical to have alignment on timelines, priorities, and contracts as early and often as possible. The process, as I'm sure everyone in tech knows, is one of the least enjoyable experiences for development teams. After seeing the first iteration of this planning turn south quickly, I offered to be the "Hype Man" for the next one, and bring some of my personal brand of entertainment to the equation. We had the most active and engaging sessions among peer organizations within the company. Our commitments and plans began hitting the metrics we needed for predictability and successful delivery.
