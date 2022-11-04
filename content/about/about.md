+++
title = "About Carbonaut"
weight = 3
+++

## Carbon Hack 2022

We started developing Carbonaut during the [Carbon Hack 22](https://taikai.network/gsf/hackathons/carbonhack22). 

### Our Pitch

### Problem Statement

Data centers around the world consume a lot of energy, and research reports indicate that this trend will continue. This is a problem because most of the world's energy production is still based on fossil fuels, and if we switch to green energy, this will quickly become scarce. In order to take further action to reduce carbon and energy consumption, there is a lack of data level and observational capabilities. Due to the heterogeneous aspect of distributed systems, many different systems need to be integrated to build this data layer. This is where Carbonaut comes in. 

While many modern systems and architectures assume that software can be shifted and scheduled without issues, major enterprises and small and medium businesses (SMBs) still need to fulfill this trend. Hence most used services in cloud service providers (CSP) are still classic virtual machines due to a lack of knowledge, governance, and the overall missing competency of managing cloud infrastructure [1]. Yet a trend to container and Kubernetes is noticeable, not only in the clouds but on the ground at private DCs, too, as the vast majority of computation workloads are running on-premises. 

Gathering information and making data-driven decisions is highly complex today. The CSP provided insight into power consumption and caused carbon emissions that could be more precise and often delayed by 3-5 months. On prem, you may have some insights about your contracted energy supply, by you need to be made aware of the energy mix and its caused CO2 output and a detailed mapping between power consumption per node to the services running on it. In short, the link between all relevant data is missing to drive and decide as an organization to change your ICT for Green KPIs.

### Carbonaut - The Cloud Native Carbon Control Center

Carbonaut is a portmanteau of Carbon and Astronaut - because it discovers the void (missing data clearance) and helps you to bring the carbon out.

Carbonaut integrates interfaces from public cloud providers (AWS so far), Kubernetes and, in the future, self-managed infrastructure to identify IT infrastructure in use and combines this with carbon and energy data providers to provide estimates of specific energy consumption and carbon emissions.  

We calculate this for CPU, Memory and Storage. 

Overall, Carbonaut shows the following data as visualizations:
* Dashboard - giving an overview of the overall relevant data
    * Cumulated CO2e in tons over time
    * Cumulated kWh in tons over time
    * Cumulated Cloud Spend/Costs over time
    * List of regions (data centers) in use 
    * Map of regions (data centers) in use 
    * Month-by-month KPI over three months
* Resources - Details on different resources and their impact
    * Resources per CO2e tons or emissions per dollar
    * List of Accounts or Products/Projects (requires label)
    * Table/list of all resources
* Discovery - Provide insights of decision-relevant data for architects and decision taker 
    * Carbon/Energy Mix per region/DC, comparable to other months, weeks, and year
    * Comparison of resource types per region
* Kubernetes - Simplifies the complex view of many moving K8s resources and helps them to analyze
    * Resource Utilization per Node
    * CO2e per deployment/pod

We enrich the visualizations with recommendations. Carbonaut, in the end, helps to gain precise information about your infrastructure and services and optimize them on CO2 data.

### API/SDK Utilization

The Carbon Aware SDK is used as one of the data providers in the Carbonaut agent. The Carbonaut agent takes the average resource utilization and calculates an estimated value of power consumption. Based on this, the SDK then makes a location-based request to the WattimeAPI to gather the CO2e information.

### Carbonaut Impact

Visualizing actual data is simple but powerful and missing on various cloud and computing service providers. Carbonaut is building a trustful foundation to make decisions by optimizing, reducing, or eliminating resources causing unnecessary CO2e output. From the ground up, Carbonaut can be integrated into any cloud provider and can read Kubernetes based workloads anywhere (Cloud, hypervisor, bare metal) through various standardized options. Having this transparency on time allows Solution Architects to take Green/Environmental principles into their solution design. This helps to make an impact now and make even more impactful decisions for the future. With similar development within FinOps, we can tell that an initial CO2e reduction of between 25-40% is realistically feasible and that you can achieve an 80-90% effectiveness of CO2e optimization in the long run.

### Feasibility

The feasibility is given, also it may take some while till all required data is in a good quality shape available. Yet the biggest issue is the measurement of power usage. For some implementations, we have thought about integrating with hypervisors or reading it directly from the host via IPMI/RedFish. However, on a cloud provider, that is challenging. We, therefore, thought of having a labeling system that shows if the data is either an estimation, prediction, projection, or original.

### Vision

Open source can be a crucial driver for creating an environmentally friendly ICT. Throughout its multiplicity, open source can positively impact CO2e output. Leading by example, we will implement a tool that can be adapted by anyone to start their environmental change. We are thinking of a control center where all the IT-related carbon, and in future other waste, data lives, gets analyzed and acted on. Through public and editable rule sets, we will recommend changes and other tools for optimization and deliver pre-defined policies to implement them immediately.

We are thinking of weather forecast-oriented overnight workload shifting based on if this is, in the end, saving more than it “costs” CO2e. We are thinking of integrating into CI/CD pipelines to collect early on new infrastructure deployments and predict their CO2e intensity. We are thinking of having applications within load tests and being more precise about their energy demands. We are thinking of having Carbonaut as an admission controller to automate all this knowledge and make decisions.