# Mountkirk Games

**Company Overview -**

Mountkirk Games makes online, session-based, multiplayer games for the most popular mobile platforms. They build all of their games using some server-side integration. Historically, they have used cloud providers to lease physical servers.
Due to the unexpected popularity of some of their games, they have had problems scaling their global audience, application servers MySQL databases, and analytics tools.
Their current model is to write game statistics to files and send them through an ETL tool that loads them into a centralized MySQL database for reporting.

**Solution Concept -**

Mountkirk Games is building a new game, which they expect to be very popular. They plan to deploy the game's backend on Google Compute Engine so they can capture streaming metrics run intensive analytics, and take advantage of its autoscaling server environment and integrate with a managed NoSQL database.

**Business Requirements -**

Increase to a global footprint
Improve uptime `" downtime is loss of players
Increase efficiency of the cloud resources we use
Reduce latency to all customers

**Technical Requirements -**

Requirements for Game Backend Platform

1. Dynamically scale up or down based on game activity
2. Connect to a managed NoSQL database service
3. Run customize Linux distro
   Requirements for Game Analytics Platform
4. Dynamically scale up or down based on game activity
5. Process incoming data on the fly directly from the game servers
6. Process data that arrives late because of slow mobile networks
7. Allow SQL queries to access at least 10 TB of historical data
8. Process files that are regularly uploaded by users' mobile devices
9. Use only fully managed services

**CEO Statement -**

Our last successful game did not scale well with our previous cloud provider, resulting in lower user adoption and affecting the game's reputation. Our investors want more key performance indicators (KPIs) to evaluate the speed and stability of the game, as well as other metrics that provide deeper insight into usage patterns so we can adapt the game to target users.

**CTO Statement -**

Our current technology stack cannot provide the scale we need, so we want to replace MySQL and move to an environment that provides autoscaling, low latency load balancing, and frees us up from managing physical servers.

**CFO Statement -**

We are not capturing enough user demographic data, usage metrics, and other KPIs. As a result, we do not engage the right users, we are not confident that our marketing is targeting the right users, and we are not selling enough premium Blast-Ups inside the games, which dramatically impacts our revenue.
