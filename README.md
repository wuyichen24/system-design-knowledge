# system-design-knowledge

[![License: CC BY-NC-ND 4.0](https://licensebuttons.net/l/by-nc-nd/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

## Overview
Accumulate system design knowledge (concepts, patterns, technology choices, etc.) from different resources (books, essays, web, etc.).

## Concepts

- [Scalability](concepts/Scalability.md)
- [Availability](concepts/Availability.md)
- [Consistency](concepts/Consistency.md)
- [CAP Theorem](concepts/CAP_Theorem.md)
- [Transaction](concepts/Transaction.md)
- [Network](concepts/Network.md)
- [Communication](concpets/Communication.md)
- [Service Discovery](concepts/Service_Discovery.md)

## Components
- [Domain Name System (DNS)](components/Domain_Name_System.md)
- [Load Balancer (LB)](components/Load_Balancer.md)
- [Content Delivery Network (CDN)](components/Content_Delivery_Network.md)
- [Database (DB)](components/Database.md)
- [Cache](components/Cache.md)
- [Message Queue](basics/Message_Queue.md)
- [Reverse Proxy](components/Reverse_Proxy.md)

## Patterns
- [**Overview**](patterns/README.md)
- [**Data Management Patterns**](#data-management-patterns)
   - [Command Query Responsibility Segregation (CQRS)](patterns/data_management_patterns/Command_Query_Responsibility_Segregation.md)
   - [Event Sourcing (ES)](patterns/data_management_patterns/Event_Sourcing.md)
   - [API Composition](patterns/data_management_patterns/API_Composition.md)
- [**Transaction Patterns**](#transaction-patterns)
   - [Two-Phase Commit (2PC)](patterns/transaction_patterns/Two_Phase_Commit.md)
   - [Three-Phase Commit (3PC)](patterns/transaction_patterns/Three_Phase_Commit.md)
   - [Saga](patterns/transaction_patterns/Saga.md)
   - [Try-Confirm/Cancel (TCC)](patterns/transaction_patterns/Try_Confirm_Cancel.md)
- [**External API Patterns**](#external-api-patterns)
   - [API Gateway](patterns/external_api_patterns/API_Gateway.md)
   - [Backends for Frontends (BFF)](patterns/external_api_patterns/Backends_For_Frontends.md)
- [**Resiliency Patterns**](#resiliency-patterns)
   - [Circuit Breaker](patterns/resiliency_patterns/Circuit_Breaker.md)
   - [Bulkhead](patterns/resiliency_patterns/Bulkhead.md)
   - [Fallback](patterns/resiliency_patterns/Fallback.md)
   - [Retry](patterns/resiliency_patterns/Retry.md)
   - [Timeout](patterns/resiliency_patterns/Timeout.md)
- [**Messaging Patterns**](#messaging-patterns)
   - [Claim Check](patterns/messaging_patterns/Claim_Check.md)
   - [Publishing Events Using Local Transactions](patterns/messaging_patterns/Publishing_Events_Using_Local_Transactions.md)
   - [Transaction Log Tailing](patterns/messaging_patterns/Transaction_Log_Tailing.md)
- [**Legacy System Patterns**](#legacy-system-patterns)
   - [Anti-Corruption Layer (ACL)](patterns/legacy_system_patterns/Anti_Corruption_Layer.md)
   - [Strangler](patterns/legacy_system_patterns/Strangler.md)
- [**Cache Patterns**](#cache-patterns)
   - [Cache-Aside](patterns/cache_patterns/Cache_Aside.md)
   - [Cache-As-SOR](patterns/cache_patterns/Cache_As_Sor.md)
- [**Container Patterns**](#container-patterns)
   - Single-node, multi-container patterns
      - [Sidecar](patterns/container_patterns/Sidecar.md)
         - [Ambassador](patterns/container_patterns/Ambassador.md)
         - [Adapter](patterns/container_patterns/Adapter.md)
   - Multi-node patterns
      - [Leader Election](patterns/container_patterns/Leader_Election.md)
      - [Work Queue](patterns/container_patterns/Work_Queue.md)
      - [Scatter/Gather](patterns/container_patterns/Scatter_Gather.md)
- [**Configuration Patterns**](#configuration-patterns)
   - [External Configuration Store](patterns/configuration_patterns/External_Configuration_Store.md)
- **Security Patterns**
   - [Valet Key](patterns/security_patterns/Valet_Key.md)
- [**Other Patterns**](#other-patterns)
   - [Health Check API](patterns/other_patterns/Health_Check_API.md)
