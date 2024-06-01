# Amazon Event Bridge

- Event buses can be accessed by other AWS accounts using Resource-based Policies
- You can archive events (all/filter) sent to an event bus (indefinitely or set period)
- Ability to replay archived events
  ![Event bridge](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/26868d91-f984-41c2-83a5-d220885f11ff)

**EventBridge - Schema Registry**

- EventBridge can analyze the events in your bus and infer the schema
- The Schema Registry allows you to generate code for your application, that will know in advance how data is structured in the event bus
- Schema can be versioned 

**Amazon EventBridge – Resource-based Policy**

- Manage permissions for a specific Event Bus
- Example: allow/deny events from another AWS account or AWS region
- Use case: aggregate all events from your AWS Organization in a single AWS account or AWS region
  ![Eventbridge resource based policy](https://github.com/JordanSennett/AWS-Security-Specialty/assets/15804669/ac9307d3-5b11-434e-b051-be02c3b41d9e)

