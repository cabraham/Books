# Platform Strategy

## Innovation Through Harmonization

#### What is a platform?

- A platform in general terms is something that elevates you.  It is also something to build upon.
- Going along with this definition, when standing on a platform, it allows you to see further.

> Platforms generate value through the interaction between their participants.


Platforms enable, democratize, self-perpetuate, accelerate, and don't constrain.

* Interesting note: business applications are best when constraints are there... but platforms go the other way reducing constraints.


#### An analogy
- A supermarket is NOT a platform because the supermarket controls the inventory and sales
- A farmer's market however connects various sellers and buyers together.  


Platforms are largely invisible and enable connectivity.  


#### Examples of platforms

- Media Platforms like Facebook, Netflix, TikTok, etc
- Cloud Platforms like AWS, GCP, Azure
- Business Platforms like SAP and SalesForce


### Chapter 3 - The Fab Four of Technology Platforms
![Types of IT platforms](images/types_of_IT_platforms.png)

1. *Marketplaces* - facilitate transactions between customer groups such as buyers and sellers of physical goods, or consumers of services like media, car sharing, or accomodation

- Common Use Cases
    - The platform handles search, advertising, reviews, ranking, fraud detection, and even payment services.

- Interaction
    - Participants interact with the marketplace via web browser, mobile app, or APIs.
    - Marketplace platforms allow sellers to build their own storefronts, often without knowing how to code
    - Thus reducing friction and barrier to entry

- Implementation
    - The platforms are usually custom built and proprietary.  
    - The primary reason is because of the sheer scale and transaction volume that the platform must handle
    - Sometimes however they result in open-source projects based on their in-house development

2. *Base Platforms* - provides technical products and services to support developers and IT departments

- Common Use Cases
    - All major cloud providers provide services that traditionally would be done in house, like server provisioning, storage, and network hardware.
    - These platforms are not a single product per se, but a collection of technical services that a customer can build applications on top of

- Interaction
    - Online consoles - like AWS console 
    - Command-line (CLI) - supports direct interaction or scripting for automated execution
    - Web APIs - that can be called from applications
    - Cloud platform languages - CDK, Terraform, Pulumi, etc

    - Base platforms aim for feature parity across these channels

- Implementation
    - Propietary implementations due to the scale and complexity of provisioning resources
    - Levels of customization down to selection of hardware like CPUs

- Considerations
    > How users access your platform is at least as important as what's inside.
    - Cloud providers initially offered virtual machines, storage, and queue services... which isn't new
    - What was new however is the way those services would be consumed


3. Developer Platforms - built by IT departments to provide reuse of common IT services, boost developer productivity, and to ensure compliance with operational guidelines

- Common Use Cases

- Interaction
    - app devs interact with in-house platforms similar to base platform
    - however there may not provide feature parity across web consoles, command lines, and APIs

- Implementation
    - typically built on top of a cloud base platform
    - it can span public cloud and on-premises data centers

- Considerations
    - in-house platform teams are focused on internal customers
    - even though their platforms are not on the "free-market", they may still need an internal marketing, consulting, and support teams

4. Business Capability Platforms - exposes functions from the business domain
    - examples are digital identity services and payment APIs

- Common Use Cases

- Interaction
    - APIs are the key enabler for business capability platforms

- Implementation
    - like regular products but have additional provisions for external usage such as public APIs, multi-tenancy, or scalability

- Considerations
    - 



## Part 2: A Strategy for PLatforms

- Building a platform of any kind reduces complexity by solving alot of common problems, all the while reducing cost
- Building a platform however is not purely an IT exercise.  It requires significant investment in both technology and organizational change

## Chapter 3 - Formulating a Strategy

> "Strategy is the difference between making a wish and making it come true"

> "Strategy is not complex.  But it is hard.  It's hard because it forces people and organizations to make specific choices about their future - something that doesn't happen in most companies."


### Think in the First Derivative
    - Platforms enable faster delivery
    - Rolling out a platform is not drive by the wish to achieve a predefined, static target state.  
    - Rather, it allows the organization to grow or change more quickly


![Rate of Change](images/rate_of_change.png)

A platform strategy, should think in the first derivative, which is the rate of change.

### Documenting a Strategy
- aim for emphasis over completeness

- a good strategy will cover 3 dimensinos
1. A point: where do you want to go
2. A path: how will you get there?
3. The Terrain: What happens when you step off that path?

The shape of the terrain represents the strategy's risk profile.  The shortest and quickest path may be very risky.


![Misleading roadmaps vs strategic roadmaps](images/strategy_roadmaps.png)

Strategy Is a Winding Road

- Strategy defines overall direction, but not the exact steps
- Tactics to implement the strategy may not line up exactly
    - the concept of a hiker using switchbacks
    - few people walk up a hill in a straight line
- However strategy and tactics do need to have a proper linkage
