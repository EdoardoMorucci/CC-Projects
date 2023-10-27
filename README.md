
# Docker: Health Monitoring System

Developed a system for the continuous monitoring of the health of a group of Docker hosts.

Project completed for the “Cloud Computing” exam.



## Short Description

The objective of this project is to create a system for the continuous monitoring of the health of a group of Docker hosts. Each **Docker host** is equipped with an agent, which is a software responsible for periodically assessing the well-being of the containers running on the same host. More specifically, at regular intervals (every x seconds), the agent sends requests to all containers listed for monitoring and calculates the level of packet loss experienced. If a container is found to be offline or if it encounters a packet loss exceeding a specific threshold, the agent is tasked with terminating and automatically restarting that container.

The list of containers to be monitored and the threshold values are configured by the system administrator, who interacts with the system through a REST interface. This interface is made accessible via a control module running on one of the Docker hosts, specifically on the machine with IP address 172.16.3.201.

Additionally, the same docker hosts the RabbitMQ broker service within a container. This setup allows for communication between various system components, including the agents and the Swagger server.

To verify the system's proper operation, we have undertaken the following actions:

1. Deployed "dummy" containers on each Docker host, each of which will be monitored by the respective agents.
2. Created the "antagonist," a small program running on each Docker host, with the role of intermittently halting containers or intentionally causing simulated packet loss.

**Functional Requirements:**

1. Agent Module: This module runs on each host and monitors the containers on that host. It performs periodic tests to ensure container well-being, automatically restarting containers if they fall below a defined threshold. It also facilitates communication with the Controller module through RabbitMQ.
2. Controller Module: The Controller module offers container control functions to the system administrator via a REST interface. Administrators can retrieve lists of running containers, set packet loss thresholds, specify containers for monitoring, and remove containers from the monitoring system.
3. Antagonist Module: This module simulates real-world system behaviors by randomly halting containers and inducing packet loss and network delays.


**Non-Functional Requirements**:

In large-scale containerized environments, fulfilling these requirements is reliant on dedicated cloud-native monitoring tools and automation. Failing to achieve observability can lead to operational and scalability challenges. These include poor visibility for both developers and operations teams, making it difficult to understand system performance and troubleshoot issues. Scalability challenges can arise from the inability to gauge demand and user experience, potentially resulting in poor performance, scalability problems, and resource wastage.




# Page Rank

Implemented the PageRank algorithm, calculating the "importance" of various Wikipedia pages.

Project completed for the “Cloud Computing” exam.


## Short Description

PageRank serves as an evaluation of web page quality by considering the **hyperlink graph's structure**. While Google's search algorithm takes into account numerous features, PageRank stands out as one of the most renowned and extensively studied.

To vividly illustrate PageRank, envision a **random web surfer**: this surfer lands on a page, randomly selects a link, and repeats this process endlessly. PageRank quantifies how frequently a page would encounter this tireless web surfer. More precisely, it's a probability distribution across nodes in the graph, indicating the likelihood of a random walk within the link structure arriving at a specific node. Nodes with high in-degrees tend to possess elevated PageRank values, as do nodes linked to by other nodes with high PageRank values. This behavior aligns with our expectations: high-quality pages are anticipated to have numerous endorsements from other pages in the form of hyperlinks. Likewise, if a high-quality page links to another, the second page is likely to be of high quality too.

The comprehensive PageRank formulation introduces an additional component. The web surfer doesn't click links randomly. Instead, a biased coin is flipped before each move. If it's heads, the surfer clicks on a random link, but if it's tails, the surfer ignores the page's links and teleports to a completely different page.

PageRank's recursive nature leads to an iterative algorithm structurally akin to parallel breadth-first search. This program works with pages from the Simple English Wikipedia, calculating the "importance" of various Wikipedia pages based on the PageRank metric and presenting them in descending order of importance. The data source is a pre-processed version of the Simple Wikipedia corpus, stored in XML format.
