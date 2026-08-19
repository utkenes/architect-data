
## Architecture Communication Canvas

When asked to create an architecture communication canvas, you use the following rules:

Help me fill out the Architecture Communication Canvas by Gernot Starke for my project. Ask the right questions to gather information about my architecture. Enter the information found in the appropriate place on the Canvas. Use PlantUML for diagrams. Ask me the questions one by one, consecutively.

# Value Proposition
Answer at least on of the following 	questions:

* What are the systems’ major objectives?
* What value does the system deliver to the customer?
* What are the major business goals of the system?
* Why is the system build and operated?
* What is its core responsibility?

# Key Stakeholder
Identify the most important stakeholders of the system:

* For whom are we creating value?
* Who is paying for development?
* Who is paying for operations?
* Who are our most important customers?
* Who are our most important contributors?

# Core Functions

* What are the most important functions, features or use-cases of the system?
* What activities or processes does it offer?
* What is the major use-case?
* Which of the functions generates high value for stakeholders?
* Which functions are risky, dangerous or critical?

# Quality Requirements
What are the important quality goals and requirements, like speed, scalability, reliability, usability, security, safety, capacity or similar.

# Business Context
Which external systems, interfaces or neighbouring systems…

* are the most important data sources?
* are the most important data sinks?
* determine our reliability, availability, performance or other critical quality requirements?
* are highly volatile or risky?
* have high operational cost (e.g. pay-per-use)?
* are difficult to implement, operate or monitor?

# Core Decisions - Good or Bad
Which decisions…

* lead to the current state of the system?
* are you especially proud of?
* turned out to be dubious, wrong or painful?
* can’t you understand from todays’ perspective?

# Components / Modules
What are the major building blocks of the system (e.g. modules, subsystems, packages, components, services)?


# Technologies
What are the most important technologies used for development and operation of the system?

For example:

* programming languages and technologies
* frameworks (like SpringBoot, .NET, Flask, Django)
* database or middleware
* technical infrastructure like physical hardware, server, datacenter, cloud provider, hyperscaler or similer
* operating technologies and environment
* monitoring and administration technologies and environment

# Risks and Missing Information

* What are known problems?
* Which parts of the system are known to cause problems during implementation, test or operation?
* Which processes (requirements, architecture/implementation, test, rollout, administration, operation) cause problems?
* What hinders development or value-generation?
* What would you like to know about the system, but cannot currently find out?
* What is hindering the team from delivering better value faster?

The result should be an asciidoc document following the given template:

<canvas-template>
++++
<style>
.canvas ul {
    margin-left: 0px;
    padding-left: 1em;
    list-style: square;
}
.canvas tr:nth-child(1) td:nth-child(1),
.canvas tr:nth-child(1) td:nth-child(2),
.canvas tr:nth-child(2) td:nth-child(1),
.canvas tr:nth-child(3) td:nth-child(1),
.canvas tr:nth-child(4) td:nth-child(1)
{
    background-color: #8fe4b4;
    border: 1px solid black;
}

.canvas tr:nth-child(1) td:nth-child(3),
.canvas tr:nth-child(1) td:nth-child(4),
.canvas tr:nth-child(4) td:nth-child(2)
{
    background-color: #94d7ef;
    border: 1px solid black;
}

.canvas tr:nth-child(5) td:nth-child(1),
.canvas tr:nth-child(5) td:nth-child(2)
{
    background-color: #ffc7c6;
    border: 1px solid black;
}
</style>
++++

== Architecture Communication Canvas

Designed for: [System Name] +
Designed by: [Author Name]


[.canvas]
[cols="25,25,25,25"]
|===

a| 
*Value Proposition* +

[Value Proposition]

.2+a| *Core Functions* +

[Core Functions]

.3+a| *Core Decisions - Good or Bad* +

Good:

[Core Decisions Good]

Bad:

[Core Decisions Bad]

Strategic:

[Core Decisions Strategic]

.3+a| *Technologies* +

[Technologies]

.2+a| *Key Stakeholder* +

[Key Stakeholder]

a| *Quality Requirements* +

[Quality Requirements]

2+a| *Business Context* +

[Business Context]

2+a| *Components / Modules* +

[Compontents / Modules]

2+a| *Core Risks* +

[Core Risks]

2+a| *Missing Information* +

[Missing Information]

|===

https://canvas.arc42.org/[Software Architecture Canvas] by Gernot Starke, Patrick Roos and arc42 Contributors is licensed under http://creativecommons.org/licenses/by-sa/4.0/?ref=chooser-v1[Attribution-ShareAlike 4.0 International]

</canvas-template>

