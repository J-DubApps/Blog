+++
date = '2016-01-10T23:17:51-06:00'
draft = false
title = 'Network Topologies Cheatsheet'
type = 'post'
tags = ["tech", "beginner-fundamentals", "enterprise-it", "cheatsheet", "networking", "cisco"]
+++
# Network Topologies Cheatsheet

Network topologies describe the physical or logical arrangement of network devices.

---

## 1. **Star Topology**
- **Description**: All nodes are connected to a central device (switch, hub, or router).
- **Advantages**:
  - Easy to set up and manage.
  - Fault isolation (failure of one node doesn't affect others).
  - Scalable by adding new devices to the central hub.
- **Disadvantages**:
  - Single point of failure (central device).
  - Requires more cabling than bus topology.
- **Use Cases**:
  - Home networks.
  - Small to medium-sized office networks.

---

## 2. **Bus Topology**
- **Description**: All nodes are connected to a single backbone cable.
- **Advantages**:
  - Easy and inexpensive to set up.
  - Requires minimal cabling.
- **Disadvantages**:
  - Backbone failure affects the entire network.
  - Difficult to troubleshoot.
  - Performance degrades with more devices.
- **Use Cases**:
  - Legacy LAN setups.
  - Small networks with limited devices.

---

## 3. **Ring Topology**
- **Description**: Nodes are connected in a circular fashion, with data traveling in one direction (unidirectional) or both directions (bidirectional).
- **Advantages**:
  - Predictable data transmission (deterministic).
  - Easier troubleshooting compared to bus topology.
- **Disadvantages**:
  - Failure in one node can disrupt the entire network (unless dual-ring).
  - Difficult to reconfigure or scale.
- **Use Cases**:
  - Fiber Distributed Data Interface (FDDI).
  - Token Ring networks (now obsolete).

---

## 4. **Mesh Topology**
- **Description**: Each node connects to every other node, creating multiple redundant paths.
- **Advantages**:
  - Highly reliable (no single point of failure).
  - Load balancing possible.
- **Disadvantages**:
  - Expensive to implement.
  - Complex to manage and maintain.
- **Use Cases**:
  - High-performance and fault-tolerant networks (e.g., WANs, military systems).

---

## 5. **Tree (Hierarchical) Topology**
- **Description**: A combination of star and bus topologies, with a root node and hierarchical branching.
- **Advantages**:
  - Scalable (allows hierarchical grouping).
  - Fault isolation within branches.
- **Disadvantages**:
  - Backbone failure disrupts the entire tree.
  - Higher cabling costs compared to star topology.
- **Use Cases**:
  - Enterprise networks.
  - Large-scale LANs.

---

## 6. **Hybrid Topology**
- **Description**: Combination of two or more topologies (e.g., star-ring, star-bus).
- **Advantages**:
  - Flexible and scalable.
  - Can optimize topology for specific needs.
- **Disadvantages**:
  - Complex to design and manage.
  - Higher cost due to mixed technologies.
- **Use Cases**:
  - Data centers.
  - Modern corporate networks.

---

## Topology Summary Table
| **Topology**     | **Advantages**                          | **Disadvantages**                     | **Use Cases**                       |
|-------------------|-----------------------------------------|----------------------------------------|-------------------------------------|
| Star              | Easy to manage, fault isolation        | Central device failure affects network| Home and office networks           |
| Bus               | Simple, cost-effective                 | Backbone failure disrupts all devices | Small/legacy LANs                  |
| Ring              | Predictable, efficient data flow       | Node failure affects network          | FDDI, Token Ring                   |
| Mesh              | Highly reliable, fault-tolerant        | Expensive, complex                    | WANs, high-reliability networks    |
| Tree              | Scalable, hierarchical organization    | Backbone failure affects network      | Enterprise LANs                    |
| Hybrid            | Flexible, scalable                     | Expensive, complex                    | Data centers, corporate networks   |

---

## Visualization of Topologies

### Star Topology

~~~
[Node]   [Node]
    \     /
    [Switch]
    /    \ 
[Node]   [Node]

### Bus Topology

[Node] – [Node] – [Node] – [Node]

### Ring Topology

```
+-----+
|     |
|     |---------
|     |        |
+-----+        |
   |           |
   |           |
+-----+     +-----+
|     |     |     |
|     |-----|     |
|     |     |     |
+-----+     +-----+

```



           .              
           |           
        .--+--.       
       |       |    
      .+.     .+.    
     |   |   |   |     
     1   2   3   4        


