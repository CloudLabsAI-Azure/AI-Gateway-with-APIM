# Operationalize and Save Cost with AI Gateway Capabilities in Azure API Management

### Overall Estimated Duration: 4 Hours

## Overview

This hands-on workshop focuses on leveraging Azure API Management (APIM) as the central control plane to operationalize and manage AI services in a scalable, cost-efficient, and secure manner. The lab is designed for participants who want to integrate Large Language Models (LLMs) and Model Context Protocol (MCP) servers into production-grade solutions while optimizing for performance and cost.

## Objective 

This lab is designed to provide participants with hands-on experience in classifying, protecting, monitoring, and investigating organizational data using Microsoft Purview. By completing this lab series, participants will gain practical skills in data classification, DLP policies, insider risk management, and security awareness simulations.

- **Load Balancing and Model Routing:** This lab guides participants through distributing LLM requests efficiently across multiple AI resources. Participants will learn to configure load balancing across AOAI resource pools, set up model routing to direct requests to specific models, and implement session affinity to maintain consistent AI agent interactions. 

- **Managing LLM Traffic**: This lab provides practical experience in monitoring and controlling LLM usage to optimize performance and reduce costs. Participants will capture token usage metrics, apply rate limiting policies, and monitor consumption patterns to prevent overuse. 

- **Exposing MCP Tools via API Management**: Participants will explore securely exposing MCP servers and REST APIs through Azure API Management. This exercise focuses on centralized control, authentication, and secure API exposure. 

- **Semantic Caching for Performance Optimization**: 
This lab introduces participants to semantic caching to improve AI response times and reduce token consumption. Participants will learn caching principles and configure semantic caching in the AI Gateway environment. 

- **Content Safety & Filtering**: This exercise teaches participants to enforce content safety rules to ensure responsible AI interactions. Participants will configure filters for both inputs and outputs, apply enforcement rules, and monitor compliance.

## Prerequisites

Participants should have: Basic knowledge and understanding of
the following
 
 - Azure Portal
 - AI foundary portal 

## Architecture

This architecture flow demonstrates the end-to-end lifecycle of operationalizing, securing, and optimizing AI services using Azure API Management. It begins with exposing Large Language Models (LLMs) and Model Context Protocol (MCP) servers through a centralized API gateway. Requests are routed efficiently using load balancing and model routing, while session affinity ensures consistent responses for agent interactions. Semantic caching reduces repeated AI requests, improving performance and lowering token consumption. Content safety and filtering policies enforce responsible AI interactions. Monitoring and telemetry track usage, token consumption, and performance metrics, while rate limiting and quotas optimize costs. Finally, secure API exposure and client authorization ensure that AI services are safely consumed, providing a scalable, cost-efficient, and compliant AI solution.

## Architecture Diagram:

![](../media/arch01.png)

## Explanation of Components

- **Azure API Management (APIM):** Serves as the centralized gateway for exposing and managing AI services. APIM enforces security, policies, rate limits, and monitoring while providing a unified interface to consumers of AI services.

- **Large Language Models (LLMs):** AI models that handle natural language requests. LLMs are distributed across multiple instances for load balancing and routed based on the request type. Token usage is monitored to control operational costs.

- **Model Context Protocol (MCP) Servers:** Specialized AI tools or microservices exposed via APIs. MCP servers provide additional functionality and are secured through APIM with client authorization and controlled access.

- **Load Balancing & Model Routing:** Ensures AI requests are efficiently distributed across multiple LLM or MCP instances. Session affinity is maintained to provide consistent responses for conversational AI interactions.

- **Semantic Caching:** Stores previous AI responses for repeated or similar queries to reduce token consumption and improve response times.

- **Content Safety & Filtering:** Applies rules to screen user inputs and AI outputs, preventing unsafe or non-compliant interactions. Policies can be configured dynamically using request headers.

- **Monitoring & Telemetry:** Tracks token usage, request patterns, and performance metrics. Provides insights for optimizing AI workloads and controlling costs.

- **Rate Limiting & Quotas:** Controls AI traffic by setting limits on token consumption or API calls to prevent overspending and maintain reliable performance.

- **Client Authorization & Secure Access:** Ensures that only authorized users or applications can access MCP tools or LLM endpoints, maintaining secure and compliant AI operations.

## Getting Started with the Lab
 
Welcome to your Operationalize and Save Cost with AI Gateway Capabilities in Azure API Management workshop! We've prepared a hands-on environment for you to explore and understand how Azure API Management can be leveraged to manage, secure, and optimize AI services including Large Language Models (LLMs) and Model Context Protocol (MCP) servers.

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.

![](../media/mp-01.png)

## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Exploring Your Lab Resources

To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

 ![](../media/develop-ai-overview-3.png)

## Utilizing the Split Window Feature

For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

 ![](../media/develop-ai-overview-4.png)

## Managing Your Virtual Machine

Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

   ![Manage Your Virtual Machine](../media/develop-ai-overview-5.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![Zoom In/Zoom Out](../media/develop-ai-overview-2.png)  

## Lab Validation

After completing the task, hit the **Validate** button under the Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task; if not, carefully read the error message and retry the step, following the instructions in the lab guide.

![](../media/Purview-hol-image77.png)

## Steps to Proceed with MFA Setup if the "Ask Later" Option is Not Visible [Optional]

1. If you see the pop-up **Stay Signed in?**, click **No**.

1. If **Action required** pop-up window appears, click on **Next**.

   ![](../media/dpg11.png)

1. On **Start by getting the app** page, click on **Next**.

1. Click on **Next** twice.

1. In **android**, go to the play store and Search for **Microsoft Authenticator** and Tap on **Install**.

   ![Install](../media/dpg12.png)

   > **Note:** For iOS, open the App Store and repeat the steps.

   > **Note:** Skip if already installed.

1. Open the app and tap on **Scan a QR code**.

1. Scan the QR code visible on the screen **(1)** and click on **Next (2)**.

   ![QR code](../media/dpg13.png)

1. Enter the digit displayed on the Screen in the Authenticator app on your mobile and tap on **Yes**.

1. Once the notification is approved, click on **Next**.

   ![Approved](../media/dpg14.png)

1. Click on **Done**.

1. If prompted to stay signed in, you can click **"No"**.

1. Tap on **Finish** in the Mobile Device.

   > **NOTE:** While logging in again, enter the digits displayed on the screen in the **Authenticator app** and click on Yes.

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **Cancel** to skip the tour.

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

  Learner Support Contacts:

   - Email Support: cloudlabs-support@spektrasystems.com
   - Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next** from the lower right corner to move on to the next page.

   ![](../media/Purview-hol-image76.png)

### Happy Learning!!
