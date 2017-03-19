---
layout: post
title: "DevOps Dashboards with Hygieia"
excerpt: "All the stats that fits on a dashboard"
tags: [Clouds, IoT, Metrics]
shorturl: "https://goo.gl/rmZ9PX"
image:
# pic silver robot white skin handshake 1900x500
  feature: https://cloud.githubusercontent.com/assets/300046/14622149/306629f0-0585-11e6-961a-dc8f60dadbf6.jpg
  credit: 
  creditlink: 
comments: true
---
<i>{{ page.excerpt }}</i>

[![Gitter](https://badges.gitter.im/wilsonmar/wilsonmar.github.io.svg)](https://gitter.im/wilsonmar/wilsonmar.github.io?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

{% include _toc.html %}

Hygieia (pronouced hi-GEE-ya, the name of the <a target="_blank" href="https://www.wikiwand.com/en/Hygieia">
daughter of the Greek god of medicine and personification of hygiene and prevention of illness</a>.

The name is adopted for an open-source software project created at CapitalOne (the credit card company) 
which displays in a single <strong>dashboard</strong> the various statistics of a software delivery pipeline.

## Demos and videos

<a target="_blank" href="https://www.youtube.com/watch?v=WuPQOBMmzSE">
https://www.youtube.com/watch?v=WuPQOBMmzSE</a> [4:01] May 10, 2016

<a target="_blank" href="https://www.youtube.com/watch?v=SoNTA78j0tc">
Introducing Hygieia</a> [4:53] Jul 17, 2015 on CapitalOne's GitHub

<a target="_blank" href="https://www.youtube.com/watch?v=Iq8M3llEp0k">
https://www.youtube.com/watch?v=Iq8M3llEp0k</a>

<a target="_blank" href="https://www.youtube.com/watch?v=WZ3S1xOn8Wg">
https://www.youtube.com/watch?v=WZ3S1xOn8Wg</a> (music, no narration)

https://www.spreaker.com/user/pureperformance/012-automating-performance-into-the-capi

## Info

<a target="_blank" href="https://developer.capitalone.com/opensource-projects/hygieia/">
https://developer.capitalone.com/opensource-projects/hygieia</a>

https://gitter.im/capitalone/Hygieia/

<a target="_blank" href="https://www.youtube.com/watch?v=6Q0mtVnnthQ">
DOES16 San Francisco - DevOps at Capital One: Focusing on Pipeline and Measurement
IT Revolution</a> by Topol Pal, Director, Engineering Fellow, Capital One.
mentions these 16 gates in the pipeline (10 Commandments in octal):

0. Source code version control
0. Optimum branching strategy [Git and GitHub or GitLab, etc.]
0. Static analysis [SonarQube]
0. > 80% code coverage
0. Vulnerability scan
0. Open source scan [Black Duck]
0. Artifact version control [Nexus or Artifactory]
0. Auto provision [Puppet or Chef]
0. Immutable servers
0. Integration testing
0. Performance testing
0. Build, Deploy, Testing automated for every commit
0. Automated Change Order
0. Zero downtime release


<a name="TeamDashboard"></a>

## Team Dashboard Widget View

<a target="_blank" href="https://cloud.githubusercontent.com/assets/300046/24074613/8b7f7f62-0be2-11e7-9c78-867c0343fd00.jpg">
<img width="400" alt="hygiea-screenshot-2848x1666" src="https://cloud.githubusercontent.com/assets/300046/24074613/8b7f7f62-0be2-11e7-9c78-867c0343fd00.jpg"><br />(Click for pop-up full image)</a>

   * Features and items in progress

   * Code repo (commits per day) -- from GitLab

   * Builds from Jenkins

   * Quality of code from scans for compliance to rules for security and other aspects of coverage -- from SonarQube

   * Unit/Functional tests 

   * Deployments to servers -- from Jenkins<br />
   with server status

PROTIP: Have computer programs monitor servers and take automatic actions.


## Program-level Pipeline Dashboard

   commit > build > DEV > QA > INT > PERF > PROD

![hygieia-pgm-shift-left-600x219](https://cloud.githubusercontent.com/assets/300046/24074674/af146176-0be3-11e7-9eac-358a0a657ba7.png)
<a target="_blank" href="https://www.dynatrace.com/blog/scaling-continuous-delivery-shift-left-performance-to-improve-lead-time-pipeline-flow/">*</a>

PROTIP: Symptoms of health should also include:

   * <strong>Cycle time</strong> from idea to production

   * Man-Months of backlog in innovations and defect fix effort

   * Man-Months of "Technical Debt"

   * Percent of work <strong>unplanned</strong>.


## Trends over time 

Displays of <strong>trends</strong> over time are important to keep numbers in perspective,
both to keep from over reacting to momentary anomalies and 
from under-reacting to underlying patterns that need to be fixed.

PROTIP: So it's better to have a set of <strong>rotating dashboards</strong> 
(showing trends) than having just a number on a dashboard <strong>without context</strong> 
to whether that number is "good" or "bad".

PROTIP: Have a <strong>projection</strong> of what was expected at each point in time,
especially in the future.

Having an arbitrary <strong>target number can be counter-productive</strong> unless 
individual employees have a coherent
approach that balances the many conflicting needs.

For example, an insistance on "100% all the time" can lead staff to prioritize caution 
over <strong>innovation</strong>.




## For Executives

<strong>Executives and business managers</strong>
typically focus on <strong>financials</strong> :

   * Total cost per transaction ratio
   * Total cost as percent of revenue
   * Total revenue per employee

They favor <strong>trends</strong> over time that reflect <strong>customer experience</strong>:
(not just internal processes)

   * Availability of the system 
   * Productivity of end-users using the system being developed, such as<br />
   purchases, invoices, or other business transactions processed during a <strong>peak hour</strong>.

   * Customer Net Promoter Score
   * Employee satisfaction
   * Employee turnover rate


## Architecture

Hygieia was written to store data in a MongoDB database.

The Hygieia server exposes REST APIs.


## Install server

0. Fork <a target="_blank" href="https://github.com/capitalone/Hygieia/">
https://github.com/capitalone/Hygieia</a>
   to your own account.

0. Create a container folder to hold several related repositories.

   git clone https://github.com/ <em>My GitHub Acct</em> /Hygieia

   At the time of writing, this took up 131.1 MB of disk space.

   git clone https://github.com/ <em>My GitHub Acct</em> /Hygieia --depth=1

   At the time of writing, this took up 114.2 MB of disk space.

0. Download and build via maven using pom.xml file:

   <pre><strong>mvn clean install package</strong></pre>

   PROTIP: If you enjoy reading the deluge to the console, expand the Terminal width to avoid wrapping.

   The response:

   <pre>
[INFO] Total time: 08:34 min
[INFO] Finished at: 2017-03-18T21:11:46-04:00
[INFO] Final Memory: 108M/1581M
   </pre>

   At the time of writing, after install is 1.23 GB of disk space.

0. Install MongoDB for the API data store
0. Run collectors with properties to connect to CI tools
0. Seteup Dashboard widgets & Visualize

   QUESTION: Can only have one dashboard?

