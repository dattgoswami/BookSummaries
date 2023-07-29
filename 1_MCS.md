# Building Microservices: Chapter 1 Microservices

## 1. Understanding Microservices

- **Definition**: Microservices are small, autonomous services that do one thing well, adhering to the Single Responsibility Principle. They should be manageable by a small team and evolve independently.
- **History**: Microservices are born from concepts such as domain-driven design, continuous delivery, on-demand virtualization, infrastructure automation, small autonomous teams, and systems at scale.

## 2. Key Characteristics

- **Autonomy**: Microservices communicate via network calls, which allows for loose coupling and independent evolution.
- **Decoupling**: A service should change and deploy independently without needing changes in consumers. Service modeling and APIs design play a pivotal role here.
- **Size**: Microservices should ideally be small enough to be managed by a small team.

## 3. Benefits

- **Technology Heterogeneity**: Different technologies can be used for different services as per the requirements.
- **Resilience**: Failures can be isolated to prevent them from cascading through the system.
- **Scaling**: Individual services can be scaled as needed rather than scaling the entire system.
- **Ease of Deployment**: Small changes can be quickly and safely deployed.

## 4. Considerations

- **Increased Complexity**: The number of moving parts increases the system's complexity.
- **Potential Sources of Failure**: New potential failure sources like network, machines need to be addressed.

## 5. Building Microservices: Insights 

- **Team Productivity and Codebase Size**: Small teams working on small codebases increases productivity.
- **Composability and Reusability**: The same service can be reused and consumed differently based on the need.
- **Optimizing for Replaceability**: Services are easier to replace or delete due to their small size.
- **Microservices vs. SOA**: Microservices are a specific approach to SOA, addressing some challenges of SOA implementation.
- **Shared Libraries and Modules**: These have drawbacks such as lack of technology heterogeneity, difficulty in independent scaling, and potential for increased coupling.

## 6. Role of Architect

- **Evolving Role**: With microservices, the architect's role changes significantly, requiring adaptation to a more fluid and dynamic environment.
- **Architect as a Town Planner**: Architects should be more concerned about how services interact rather than enforcing specific structures within each service.
- **Coding Architect**: Architects need to stay hands-on with coding to understand the implications of their decisions and ensure the system is developer-friendly.
- **A Principled Approach**: Establish principles and practices aligning with strategic goals to guide design decisions.

Remember, the success of microservices lies in striking a balance between benefits and complexities. Decoupling services, maintaining small autonomous teams, and having architects with a hands-on coding approach are crucial. It's essential to consider these points before making a strategic decision to shift to a microservices architecture.

# Building Microservices: Chapter 2 The Evolutionary Architect

1. **Principles vs Constraints**: Understand the difference between chosen behaviors (principles) and necessary behaviors (constraints). Know when to challenge constraints.

2. **Practices**: Adopt detailed, technology-specific guidelines that reflect your established principles. Be ready to change these practices as technology evolves.

3. **Principles and Practices Coherence**: While different teams may use different practices, make sure they all align with common principles.

4. **Service Standardization**: Define what constitutes a well-behaved service to maintain system manageability and resilience.

5. **Monitoring Practices**: Standardize how services emit health and other monitoring-related metrics for a cohesive, cross-service view of system health.

6. **Interface Standardization**: Limit the variety of integration styles to prevent confusion and inefficiency.

7. **Architectural Safety**: Design services to protect themselves from unhealthy downstream calls, mitigating system-wide failures.

8. **Code Governance**: Promote adherence to standards through exemplars and service templates. Make it easy to conform to best practices.

9. **Exemplars Usage**: Use real-world services that follow best practices as references for other developers when creating new services.

10. **Service Templates**: Provide ready-to-use code to implement core service attributes, aiding developers in building well-behaved services.

11. **Technical Debt Management**: Be mindful of technical debt that might arise from deviations from the technical vision due to urgent feature deliveries.

12. **Architect's Role**: Maintain a balance between the current and future system structure, manage technical debt, guide teams, and possibly keep a structured log of this debt.

13. **Exception Handling**: Log exceptions to principles and practices, and consider changing them if recurrent.

14. **Technical Governance**: Align technical vision with organizational strategy, foster a positive work environment, stay updated with new technologies, and make informed trade-offs.

15. **Collaborative Governance**: Involve technologists from various delivery teams in governance. Share the workload and make informed decisions collectively.

16. **Team Development**: Foster career growth in team members by involving them in shaping and implementing the vision. Utilize the opportunities microservices offer for individuals to take ownership of individual services.

17. **Core Architect Responsibilities**: Ensure clear technical vision, empathize with customers and colleagues, encourage collaboration, adapt the vision as needed, balance between standardization and team autonomy, and align the implemented system with the technical vision.

18. **The Evolutionary Architect**: Stay flexible and adaptive. Understand that microservices require a balancing capability due to the many decisions they entail.

# Building Microservices: Chapter 3 How to Model Services

1. **Bounded Contexts**: Central to Domain-Driven Design, a bounded context defines the context within which a model operates. Each bounded context has an explicit interface and communicates with others through shared models.

2. **Shared and Hidden Models**: Models within a bounded context can be either exposed to other contexts (shared models) or kept internal (hidden models).

3. **Microservices as Modules**: Use bounded contexts to identify where related business capabilities lie. These could serve as excellent candidates for microservices.

4. **Focus on Business Capabilities**: When considering bounded contexts, focus on the capabilities these contexts offer rather than shared data. These capabilities represent the key operations exposed in a service-oriented architecture.

5. **Nested Bounded Contexts**: Bounded contexts can contain other bounded contexts. These nested contexts can be modeled as separate microservices or kept hidden inside a larger service.

6. **Business Terms for Communication**: Ensure microservices communicate using the same business terms that their interfaces reflect.

7. **Avoid Technical Boundaries**: Avoid modeling services along technical lines instead of business capabilities. This approach can lead to tightly coupled services requiring frequent changes across multiple services.

8. **Integration Technologies**: Choose an integration technology that avoids breaking changes, keeps APIs technology-agnostic, makes services easy to use for consumers, and hides internal implementation details.

9. **Database Integration**: Avoid database integration if possible due to downsides such as loss of strong cohesion and loose coupling, exposure of internal representation, and increased fear of change.

10. **Synchronous vs Asynchronous Communication**: Understand when to use synchronous (blocking until operation completes) versus asynchronous (non-blocking) communication.

11. **Orchestration vs Choreography**: Familiarize yourself with orchestration (a centralized approach) versus choreography (a decentralized approach) in the context of managing business processes.

12. **Domain-Driven Design**: Use principles from Domain-Driven Design to find sensible boundaries for your services.

13. **Service Interfaces**: Implement service interfaces properly to avoid complications in the system.

# Building Microservices - Chapter 4 Integration

## Integration Styles
1. **Orchestration vs Choreography**
   - Orchestration centralizes control, which can result in logic congestion.
   - Choreography decentralizes control and is more flexible but requires additional monitoring.

2. **Synchronous vs Asynchronous Calls**
   - Synchronous calls are simpler but can limit independence.
   - Asynchronous calls promote a more choreographed approach, enabling decoupled services.

3. **RPC vs REST**
   - RPC can be heavily tied to specific platforms, hiding complexity and leading to tight coupling.
   - REST is a flexible architectural style based on the concept of resources.

## REST and HTTP
1. REST allows a client to get a representation of a resource, which can be stored in various formats.
2. HTTP verbs align with the REST style and allow for the same operation to be executed across all resources.

## Richardson Maturity Model
1. A useful guide to understanding the different styles of REST.

## HATEOAS (Hypermedia As the Engine of Application State)
1. Provides flexibility and reduces coupling by allowing a client to interact with a server using links to other resources.

## Data Formats
1. REST over HTTP supports various data formats, including JSON, XML, HTML etc.
2. JSON is preferred for its simplicity, but XML provides native support for hypermedia controls.

## Avoid Exposing Internal Implementations
1. Be cautious about REST frameworks that directly expose database representations, leading to high coupling.

## Alternative Protocols
1. Consider other protocols like WebSockets for efficient data streaming and RPC frameworks for low-latency communications.

## Asynchronous Event-Based Collaboration
1. Complex but can lead to significantly more decoupled and scalable systems.

## Reactive Extensions (Rx)
1. Allows the composition of multiple calls and operations, simplifying the handling of concurrent calls.

## Code Reuse in Microservices
1. Sharing code or libraries can create unwanted coupling, therefore, avoid code leakage outside service boundaries.

## Bootstrapping New Services
1. Avoid shared code across microservices to prevent coupling. Copy the code for each new service instead.

## Client Libraries
1. Helpful for using services and avoiding code duplication. However, ensure server-side logic does not leak into the client.

## Versioning
1. Use techniques like a Tolerant Reader and semantic versioning (MAJOR.MINOR.PATCH) to manage changes without causing disruption.

## Service Interactions
1. REST over HTTP is a sensible default choice for service-to-service interactions due to its wide support and suitability for large volumes of traffic.

## User Interfaces
1. UI is where all microservices are unified into a user-friendly experience. It can be designed using API composition, UI Fragment Composition or Backends for Frontends (BFF).

## Coexisting Different Endpoint Versions
1. Useful when maintaining multiple versions of the service or endpoint. Requires a mechanism to route requests accordingly.

## Integrating with Third-Party Software
1. Can be beneficial when cost-effective or when the demand for software cannot be met internally.

## CMS as a Service
1. CMS should be treated as a service that allows for the creation and retrieval of content. Front the CMS with your own service to maintain control over integration and scaling. 

This cheatsheet highlights the key ideas and principles for use in software engineering practices. Always consider the context and requirements of your specific system when applying these concepts.

# Building Microservices Chapter 5: Splitting the Monolith

This chapter delves into various service-to-host mapping models and isolation techniques that can be used in deploying microservices. It provides a detailed comparison of these models, highlighting the trade-offs between cost, complexity, security, and performance. The use of orchestration tools is emphasized for efficient management of services, particularly in models that advocate for multiple instances per host.

## Service-to-Host Mapping Models 

1. **Service Instance per Host Model:** This model states that only one service instance should run per host. While this model offers high security and resource allocation, it may not be cost-efficient for all organizations.
2. **Service Instance per VM/Container Model:** This model offers better resource utilization than the previous model but is complex to manage due to the increased number of services and hosts.
3. **Multiple Service Instances per Host Model:** It advocates running multiple instances of the same service on a single host. This approach has its own benefits such as lower costs and simplicity, but it might be less secure and can lead to resource contention.

## Isolation Techniques

1. **Virtual Machines (VMs):** VMs provide strong isolation but have performance overhead due to the hypervisor layer. This approach is recommended for cases where high isolation is required.
2. **Linux Containers:** Containers are lightweight and use the host's OS directly, reducing the resource overhead. This is beneficial for hosting multiple lightweight services on a single machine.
3. **Process Level Isolation:** The isolation level determines the safety and resource sharing of the services running on the same host. A high isolation level provides a secure environment but may also limit the resources accessible by the services.

## Understanding Containers

The concept of containers is elaborated, clarifying that a container is not a lightweight VM, but an isolated slice of the OS.

## Docker: Standardizing Containers

Docker standardizes the Linux container interfaces, making them easier to use and more portable. Docker is valuable for building, running, and shipping applications with ease and efficiency.

## Orchestration Tools

The use of orchestration tools like Kubernetes, Amazon ECS, Docker Swarm, etc., is crucial for managing services, especially in the latter two models. These tools ensure effective resource utilization and simplify managing complex architectures.

1. **Kubernetes:** Kubernetes is a popular orchestration platform for managing containerized applications. It provides features for service discovery, scaling, and failure handling.
2. **Amazon ECS:** Amazon Elastic Container Service (ECS) is another option for running Docker containers, especially for those heavily invested in the AWS ecosystem.
3. **Docker Swarm:** Docker Swarm provides native clustering for Docker. It turns a pool of Docker hosts into a single virtual host.
4. **Cloud Foundry:** Cloud Foundry is a multi-cloud, open-source platform as a service (PaaS) governed by the Cloud Foundry Foundation. It provides a higher level of abstraction than Docker and allows running applications in various languages on your own servers or cloud-based servers.
5. **Service Mesh:** Tools like Istio and Linkerd provide a service mesh that helps in managing inter-service communication in a microservices architecture.

**Conclusion**

This chapter provides a detailed explanation of various tools and platforms available for managing the complexities of deploying and operating a microservices-based system. It emphasizes that the selection of these tools and models should align with the specific needs and constraints of the organization. It's essential to select the most suitable model and isolation technique based on your specific organizational requirements, available resources, and security constraints.

# Building Microservices: Chapter 6 Deployment

**Automation**

- Automation is vital in handling the complexity of microservices. It should encompass launching virtual machines, deploying software, and database changes.

**Cases of Successful Automation**

- Companies like RealEstate.com.au and Gilt have used automation to scale from a few services to hundreds, demonstrating its effectiveness.

**Virtualization vs Containers**

- Virtualization (like VMware) slices a physical server into separate hosts, but it incurs resource overhead.
- Linux containers, used by Docker, create separate process spaces for each container, providing lower resource overheads and faster provisioning times.

**Development and Testing Tools**

- Vagrant: Allows developers to create production-like environments locally, using a standard virtualization system (usually VirtualBox).
- Docker: Built on Linux containers, it handles the management of containers, providing networking solutions and version control.

**Security**

- Remember that containers are not completely sealed; processes from one container can interact with others or the underlying host. Use virtual machines for high isolation needs.

**Container Platforms and Tools**

- Docker: Provides a simple platform as a service (PaaS) on a single machine.
- CoreOS: A lightweight OS designed specifically for Docker.
- Kubernetes: Offers scheduling layers to manage resources across Docker containers.
- Deis: Aims to provide a Heroku-like PaaS on top of Docker.

**Deployment Practices**

- Uniform Deployment Interface: Ensure a microservice can be deployed on demand in different situations (locally for dev/test, production deployments).
- Single Command Deployment: Use a parameterizable command-line call for deployment, specifying what is being deployed, its version, and the environment.
- Environment Definitions: Set up to map a microservice to compute, network, and storage resources.
- Use Terraform for managing complex deployment structures, but note it might require substantial upfront effort.

**Microservice Release & Deployment**

- Each microservice should be able to release independently from another.
- Prefer a single repository and a single CI build per microservice to support independent deployments.
- Aim for a single-service per host/container setup using technologies like Docker for easier management.
- Automate as much as possible, consider switching technologies if your current one doesn't support this.
- Understand the impact your deployment choices have on developers and provide self-service deployment tools for different environments.

# Building Microservices: Chapter 7 Testing

**Key Takeaways:**

1. **System Trade-offs:** Not all parts of your microservices are equally critical. Some parts can afford temporary unavailability without severely impacting your business. Understand these trade-offs to better shape your system design and evolution.

2. **Cross-Functional Requirements (CFRs):** CFRs involve non-functional aspects like performance, security, and accessibility. Your test strategy should cater to these requirements, and they should be regularly reviewed.

3. **Performance Tests:** These tests ensure that your microservices can handle their expected load and latency. They should form a part of your regular testing regimen and target core journeys in your system. Clear performance targets should guide the interpretation of test results.

4. **Holistic Testing Approach:** Aim for a balanced test strategy that gives quick feedback. Minimize dependence on end-to-end tests by using consumer-driven contracts (CDCs), which promote inter-team discussions. Understand the trade-off between spending more time on testing and catching issues faster in production.

5. **Monitoring Microservices:** As the complexity of your system grows with more servers and microservices, monitoring needs to be refined. Monitor each component individually, but also use aggregation techniques to get an overview.

6. **Single Service, Single Server Monitoring:** Monitor key metrics like CPU and memory usage. Access and review logs for error detection and troubleshooting.

7. **Single Service, Multiple Servers Monitoring:** Track the same metrics as for a single server but on a per-host and aggregate basis. Log access and review need to be more sophisticated, possibly involving tools like ssh-multiplexers.

8. **Multiple Services, Multiple Servers Monitoring:** Centralize the collection and aggregation of logs and application metrics with the growth in complexity. Employ specialized systems like Logstash and Kibana for centralized log access, review, and analytics.

**Summary:**

This chapter explores the trade-offs in microservices design and the importance of testing for Cross-Functional Requirements (CFRs). It emphasizes the need for regular performance tests and introduces a holistic approach to testing, which includes consumer-driven contracts (CDCs). The chapter also highlights the importance of monitoring in a microservices architecture, explaining approaches for single and multiple servers. The complexity of monitoring increases with the number of microservices and servers, necessitating advanced techniques and tools for effective log access, review, and analytics.

# Building Microservices: Chapter 8 Monitoring

**Key Takeaways:**

1. **Metrics Collection:** Choose an easy-to-integrate system for metric collection. Use tools like Graphite to aggregate, send, and query metrics.

2. **Capacity Planning:** Understand usage patterns to manage infrastructure needs effectively. Monitoring aids in scaling resources optimally.

3. **Service Metrics:** Your services should expose basic and service-specific metrics like response times, error rates, and feature utilization.

4. **Synthetic Monitoring:** Use synthetic transactions to simulate user behavior and monitor the overall system's health. But do not replace lower-level metrics entirely.

5. **Implementing Semantic Monitoring:** Run end-to-end tests continuously in production, but consider data requirements and side effects.

6. **Correlation IDs:** Track user requests using correlation IDs to understand the flow of calls. Utilize tools like Zipkin for detailed tracking.

7. **Importance of Monitoring:** It provides insights about system performance, aids in capacity planning, helps in troubleshooting with detailed tracing, and gives a closer representation of the user's experience.

**Actionable Points:**

1. Implement an easy-to-integrate metrics collection system.
2. Use monitoring for capacity planning by understanding usage patterns.
3. Expose service-specific metrics.
4. Implement synthetic monitoring but retain lower-level metrics for diagnostic details.
5. Use end-to-end tests for semantic monitoring in production.
6. Use correlation IDs to track user requests and understand the flow of calls.
7. Use monitoring to gain insights into system performance, plan capacity, troubleshoot issues, and understand user experience.

# Building Microservices: Chapter 9 - Security Cheatsheet & Key Takeaways:

**1. Shared Secret Communication:**
   - Implement a secure protocol for sharing secrets or keys for authentication.
   - Ensure that access is revoked immediately if the shared secret is compromised.
   
**2. JSON Web Tokens (JWTs):**
   - Implement JWTs for secure authentication and information exchange, ensuring a correct setup to prevent severe implications.
   
**3. API Keys:**
   - Utilize API keys to limit the actions of a requester and identify them.
   - They can be used for inter-microservice communication.
   
**4. The Deputy Problem:**
   - Mitigate the deputy problem by verifying the caller's identity or providing the original principal's credentials.
   - Apply an implicit trust mechanism to prevent a service from making calls on behalf of a malicious party.

**5. Data Encryption:**
   - Encrypt sensitive data at rest to prevent unauthorized access.
   - Use well-known encryption implementations like AES-128 or AES-256.
   - Limit encryption to specific tables or data stores to reduce computational overhead.

**6. Key Management:**
   - Store encryption keys separately from the data.
   - Utilize separate security appliances or key vaults for efficient key management.

**7. Decrypt on Demand:**
   - Encrypt data when first seen and decrypt it only when necessary.
   - Avoid storing data in a decrypted form.

**8. Encrypt Backups:**
   - Ensure backups of sensitive data are encrypted.
   - Manage keys properly to handle different versions of data.

**9. Defense in Depth:**
   - Implement multiple layers of security measures such as firewalls and logging to enhance your security posture.

**10. Other Key Takeaways:**
   - Regularly update your system and ensure it is patched.
   - Use tools like Microsoft's SCCM, RedHat's Spacewalk, Ansible, Puppet, or Chef for system patching.
   - Consider network segregation based on team ownership or risk level for better security in a microservices architecture.
   - Follow the principle of data frugality (Datensparsamkeit) to minimize potential damage from data breaches.
   - Plan for the human element in security, such as revoking access when someone leaves the organization and protecting against social engineering.
   - Rely on industry-hardened technologies instead of creating your own cryptography.
   - Make sure to educate developers about security concerns and incorporate security testing into CI/CD pipelines.
   - Seek external verification through methods like penetration testing to identify and fix potential security vulnerabilities. 

This chapter provides a comprehensive discussion on securing microservices. It addresses how to handle shared secret communication, implement JSON Web Tokens (JWTs), and use API keys. It advises on how to tackle the deputy problem and emphasizes the importance of data encryption and key management. The chapter also encourages implementing a multilayered security strategy and emphasizes the importance of regular system updates, network segregation, and data frugality. It further recommends the use of industry-standard security technologies, security education for developers, and seeking external security assessments.

# Building Microservices: Chapter 10 Conway’s Law and System Design

1. **Conway’s Law Impact:** An organization's communication structure and organizational layout can directly influence the design of its systems. 

2. **Geographical Boundaries:** Fine-grained communication between distributed teams can be challenging due to geographic and timezone differences, leading to larger codebases that are harder to maintain.

3. **Single Service Ownership:** Aim to assign the ownership of a service to a single, co-located team to reduce the cost of change and increase delivery speed.

4. **Beware of Shared Service Ownership:** It can lead to communication barriers and an increase in the cost of change. Instead, consider a feature team model where a small team works on a set of features across different service boundaries.

5. **Align Teams Along Business Domains:** This alignment aids in developing a customer-focused approach, leading to better and efficient feature development.

6. **Internal Open Source Model:** It functions similarly to open source projects, with core committers taking ownership of the codebase and managing changes.

7. **Orphaned Services:** These services still need ownership. If the technology stack is unfamiliar to the team, it could pose additional challenges when changes are needed.

8. **Conway’s Law in Reverse:** Changes in system design can lead to changes in organizational structure to improve team autonomy and delivery speed.


## Summary:

This chapter outlines the relationship between organizational structure and system design, as described by Conway's Law. It explains that a system's design will invariably mirror the communication structure of the organization designing it. To reduce the cost of change and enhance delivery speed, a service should ideally be owned by a single, co-located team.

Considerations like geographic boundaries of teams, shared service ownership, and alignment of teams along business domains are discussed. The chapter also introduces the internal open source model, which operates like an open source project within an organization, with core committers managing changes.

The concept of "orphaned services," those services that lack ownership, is discussed, alongside the challenges such services can pose, especially if they use unfamiliar technology stacks. The chapter concludes by suggesting that alterations in system design can lead to changes in the organization, enhancing team autonomy and expediting delivery.

# Building Microservices: Chapter 11 Microservices at Scale

1. **Expect Failure:** Assume that parts of your system will fail at some point. Build systems that embrace failure rather than attempting to prevent it.

2. **Test for Failure:** Regularly test your system for failure using tools like Netflix's Simian Army to identify weak points. 

3. **Timeouts:** Implement timeouts to prevent systems from waiting indefinitely for a response from a failing service. Timeouts should be reasonable to prevent early termination of requests that are slow but not failing.

4. **Circuit Breakers:** Use circuit breakers to fail quickly and prevent overloading a system with requests when it's down. Monitor and tune circuit breakers over time to ensure they function correctly.

5. **Bulkheads:** Implement bulkheads to isolate parts of your system and ensure that a failure in one area doesn't bring down the entire system. 

6. **Steady State:** Ensure that the system can return to a steady state after a failure occurs. 

7. **Simulate Failures:** Simulate failures in your system to identify and learn how to handle them. Chaos Monkey and Chaos Kong are popular tools for this.

8. **Monitoring and Observability:** Use monitoring and observability tools to understand your system's behavior and to quickly detect, isolate and resolve issues.

9. **Redundancy and Replication:** Redundancy can prevent single points of failure. Replication of services, data, etc. helps in maintaining system availability.

10. **Consumer-Driven Contracts:** Use consumer-driven contracts to ensure compatibility between services. 

11. **Developer Involvement:** Encourage developers to be involved in managing production services. This encourages designing more robust systems and helps in faster resolution when issues occur.

12. **Consequence of Failure:** Understand the consequence of failure for each part of the system. Prioritize the protection of critical services.

13. **Failure Injection Testing (FIT):** Implement FIT in your testing regime to understand the impact of failures on your system and improve its resiliency.

14. **Retry Mechanism:** Implement retry mechanism in the system but ensure that it doesn't exacerbate the problem by overloading a struggling service.

15. **Post-Mortems:** Conduct post-mortems after failures to understand their cause and prevent them from happening again. Foster a blameless culture to encourage open and honest discussions.

**Key Takeaways**

1. **Expect Failures:** Failures are part of distributed systems. Always design your services and system with failures in mind.

2. **Resilience Techniques:** Implement resilience techniques such as timeouts, circuit breakers, and bulkheads to manage failures effectively.

3. **Simulate Failures:** Regularly simulate failures in your system using tools like Chaos Monkey to identify weak points and improve system resiliency.

4. **Monitoring and Observability:** Always monitor your system and have the necessary tools to observe its behavior, this helps in quick troubleshooting.

5. **Developer Involvement:** Involving developers in managing production services can result in designing more robust systems and quicker issue resolution.

6. **Post-Mortems:** After a failure, conduct a post-mortem to understand what went wrong and how it can be prevented in future. 

Remember that each microservice ecosystem is unique and may require different strategies to handle failures. Always test these strategies and iterate to ensure the highest level of resilience.

# Building Microservices: Chapter 12 Bringing It All Together

1. **Implementation Concealment:** The ability of microservices to evolve independently is crucial. Hide implementation details, particularly databases, to prevent coupling often associated with traditional service-oriented architectures.

2. **Technology-Neutral APIs:** To afford freedom in selecting different technology stacks, use technology-neutral APIs. REST is frequently considered as it formalizes the separation of internal and external implementation details.

3. **Decentralization and Autonomy:** Hand over decision-making control to service-owning teams. This involves self-service deployment, development, and testing.

4. **Team Ownership:** The teams should own their services and be responsible for the changes they make, deciding when those changes are released. The teams' alignment with the organization is vital to benefit from Conway’s law.

5. **Decentralized Architecture:** Centralized business logic systems like enterprise service buses or orchestration systems should be avoided. Instead, prefer choreography over orchestration and emphasize smart endpoints.

6. **Independent Deployment:** Each microservice must be deployable independently. When breaking changes are required, aim to coexist versioned endpoints, enabling consumers to evolve over time. A one-service-per-host model can minimize side effects on other services.

7. **Failure Isolation:** Plan for failures in the system and don't assume remote calls are like local ones. Implement bulkheads and circuit breakers to limit the impact of a failing component. 

8. **Observability:** Use semantic monitoring to verify your system's correct behavior. Aggregate logs and stats for easier troubleshooting. Correlation IDs can assist in tracing calls through the system.

9. **Consideration before Transitioning to Microservices:** If the domain is not well understood, finding suitable bounded contexts for the services can be challenging. It may be better to start with a monolithic structure and break it down when stable.

10. **Evolutionary Architecture:** Acknowledge that not all decisions will be correct, and mistakes will happen. Embrace evolutionary architecture and learn to make incremental changes to your system over time.

11. **Embrace Change:** Change is inevitable in software development. The discipline to continually change and evolve systems is an important aspect of working with microservices. 

**Summary**

This chapter stresses the need to hide implementation details, use technology-agnostic APIs, and embrace decentralization for both decision-making and architecture. It discusses the importance of team ownership, independent deployment, failure isolation, and observability. The chapter also highlights careful consideration before transitioning to microservices and emphasizes the importance of embracing change and evolutionary architecture. The key theme is that moving to a microservices architecture provides more options and decisions, making the transition challenging but rewarding when done right.
