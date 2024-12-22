a) Describe handoff/handover in 1G systems.

Handoff in 1G systems refers to the process of transferring an ongoing call or data session from one cell to another without disconnecting the service. This occurs when a mobile user moves from the coverage area of one base station to another.

    Types of Handoff in 1G:
        Hard Handoff: The connection to the current base station is terminated before establishing a connection with the next base station.
        Signal Strength-Based: The handoff decision is based on the received signal strength (RSS) from neighboring base stations.
        Fixed Threshold: A predefined RSS threshold triggers the handoff.

    Challenges in 1G Handoff:
        Call drops due to slow handoff decision-making.
        High latency in establishing connections with new base stations.
        Interference between adjacent cells during the process.

b) Illustrate the near-far problem in CDMA systems.

The near-far problem in Code Division Multiple Access (CDMA) systems occurs when signals from a nearby transmitter overpower the signals from a distant transmitter at the receiver.

    Explanation:
    In CDMA, multiple users share the same frequency band, and their signals are distinguished by unique codes. However, a nearby transmitter's stronger signal may overwhelm weaker signals from distant transmitters due to limited dynamic range in the receiver's circuitry.

    Impact:
        Causes interference and degradation in signal quality.
        Leads to unequal resource utilization and unfair communication access.

    Solutions:
        Power Control Mechanisms: Adjust transmission power levels dynamically to ensure all signals are received with similar strength.
        Advanced Filtering Techniques: Enhance the receiver's ability to differentiate between signals.

c) Illustrate all the entities of a Mobile IP system. Explain the registration process of a home agent in a foreign network.
Entities of a Mobile IP System:

    Mobile Node (MN): The device that changes its point of attachment across networks.
    Home Agent (HA): A router in the mobile node's home network that forwards data packets to the mobile node when it is in a foreign network.
    Foreign Agent (FA): A router in the visited network that provides routing services to the mobile node.
    Care-of-Address (CoA): A temporary IP address assigned to the mobile node in the foreign network.

Registration Process:

    Discovery:
        The MN sends an Agent Discovery message to identify nearby FAs.
        The FA responds with its advertisement, providing the CoA.

    Registration Request:
        The MN sends a registration request containing the CoA to the HA via the FA.

    Verification and Authentication:
        The HA verifies the MN's credentials and registers the CoA.

    Registration Reply:
        The HA sends a reply to the MN via the FA, confirming successful registration.

    Tunneling:
        The HA tunnels packets destined for the MN to the CoA using encapsulation techniques.

d) Illustrate any two models proposed to improve TCP's performance over wireless networks. Also, give their advantages and disadvantages.

    Snoop Protocol:

        A transport layer enhancement that adds a snoop agent at the base station to cache packets sent to mobile devices.

        Mechanism:
            The snoop agent monitors TCP packets, retransmitting lost packets locally without involving the sender.

        Advantages:
            Reduces end-to-end latency for retransmissions.
            Improves throughput by addressing packet losses locally.

        Disadvantages:
            Requires modifications to the base station.
            Ineffective for encrypted packets.

    Split TCP:

        Splits the TCP connection into two parts: one from the sender to the base station and another from the base station to the mobile device.

        Advantages:
            Optimizes performance over wireless links.
            Reduces the impact of high latency on end-to-end communication.

        Disadvantages:
            Breaks the end-to-end semantics of TCP.
            Increases complexity in managing split connections.

e) Describe Fisheye State Routing (FSR). Investigate the methodology used by FSR to compensate for the imprecise knowledge of the path from source to destination.
Fisheye State Routing (FSR):

FSR is a proactive routing protocol used in ad-hoc networks. It reduces overhead by maintaining a gradual precision of routing information depending on the distance of the destination.
Methodology:

    Scope-Based Updates:
        Routing updates are more frequent for nodes closer to the source and less frequent for distant nodes.

    Fisheye Perspective:
        The routing table contains detailed information about nearby nodes and summarized information about faraway nodes.

    Reduced Overhead:
        Limits the frequency of updates for distant nodes, reducing the amount of control traffic.

Advantages:

    Reduces the bandwidth consumed by routing updates.
    Suitable for large networks with dynamic topology.

Disadvantages:

    Imprecise routing information may lead to suboptimal path selection.
    Initial packet delivery may experience higher latency for distant nodes.

Compensation Mechanism:

FSR compensates for imprecise path knowledge by updating routing tables dynamically as packets traverse through intermediate nodes, ensuring eventual accuracy and packet delivery efficiency.


a) Describe MAHO in 2G Systems

Mobile-Assisted Handoff (MAHO) in 2G systems is a mechanism where the mobile device (user equipment) plays an active role in the handoff process by measuring signal strengths and reporting them to the network.

    Process:
        The mobile device measures the signal strength of its serving base station and neighboring base stations.
        It reports the measurements to the serving base station periodically.
        The network decides whether a handoff is required based on signal quality and other criteria.
        If needed, the handoff is executed seamlessly to a better base station.

    Advantages:
        Reduces the decision-making load on base stations.
        Improves handoff accuracy by using real-time signal measurements.

    Applications:
    Widely used in GSM (2G) networks to support seamless mobility.

b) Illustrate the Near-Far Problem in CDMA Systems

The near-far problem in CDMA systems arises when signals from a nearby transmitter overpower signals from a distant transmitter, making it difficult for the receiver to decode the weaker signals.

    Illustration:
    In a shared frequency environment:
        A nearby user's strong signal interferes with a distant user's weak signal.
        The receiver’s limited dynamic range struggles to distinguish between them.

    Impact:
        Degraded performance for distant users.
        Reduced system capacity.

    Solutions:
        Power Control: Adjusts the transmission power of users to ensure signals reach the base station with similar strengths.
        Advanced Signal Processing: Filters and decodes signals efficiently.

c) Illustrate Data Replication for a Mobile Computing System. Describe Its Three Types
Data Replication:

Data replication refers to creating and maintaining multiple copies of data across different devices or locations to enhance availability and reliability in mobile computing.
Types of Data Replication:

    Full Replication:
        All data is replicated on every node in the system.
        Advantages: High availability and fault tolerance.
        Disadvantages: High storage and synchronization overhead.

    Partial Replication:
        Only a subset of data is replicated on nodes based on usage patterns or importance.
        Advantages: Reduced storage requirements and optimized performance.
        Disadvantages: Limited availability for less-replicated data.

    Dynamic Replication:
        Data replication changes dynamically based on access patterns, network conditions, or node mobility.
        Advantages: Adaptable to changing scenarios and efficient resource utilization.
        Disadvantages: Complexity in implementation and management.

d) Differentiate Between the Types of Faults Associated With Mobile Agent Computing

Mobile agent computing systems can encounter several types of faults, which are categorized as follows:

    Communication Faults:
        Occur due to network disconnection, delays, or packet loss.
        Example: An agent fails to communicate with its home server during migration.
        Impact: Loss of messages or incomplete task execution.

    Agent Faults:
        Happen due to bugs or errors in the mobile agent’s code.
        Example: An agent crashes during execution.
        Impact: Loss of task progress or incorrect results.

    Server Faults:
        Occur when the host server or node becomes unavailable.
        Example: Server failure during agent execution.
        Impact: Task interruption and data loss.

    Security Faults:
        Include attacks like tampering, eavesdropping, or impersonation.
        Example: Malicious nodes modifying the agent’s data.
        Impact: Breach of confidentiality and integrity.

e) Describe Fisheye State Routing (FSR). Investigate the Methodology Used by FSR to Compensate for the Imprecise Knowledge of the Path From Source to Destination
Fisheye State Routing (FSR):

FSR is a proactive routing protocol designed for large-scale ad-hoc networks. It reduces routing overhead by maintaining routing information with varying precision levels based on the node's distance from the source.
Mechanism:

    Scope-Based Updates:
        Frequent updates for nearby nodes and infrequent updates for distant nodes.
        Reduces overhead while maintaining high accuracy for local routes.

    Gradual Precision:
        Routing tables contain precise details for nearby nodes and summarized information for faraway nodes.

Compensation for Imprecise Knowledge:

FSR dynamically updates routing tables as packets traverse the network. Each intermediate node refines and corrects routing information, ensuring packet delivery to the destination despite initial imprecision.
Advantages:

    Efficient for large, dynamic networks.
    Reduces control message overhead.

Disadvantages:

    Delayed accuracy for distant nodes.
    Increased latency for initial packet delivery in large networks.
