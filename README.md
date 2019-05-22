# smesh
ad hoc self-contained mesh network simulator


### Usage
Use `smesh-conf.yml` to configure the properties of your mesh network. You can specify different types of nodes each one with his signal range and other properties. E.g.:

```yml
define:
  common_node:
    range: 50,
    speed: 2
  
  backhaul_node:
    range: 100,
    speed: 5
````

You can make your own topology by declaring all nodes with his connections. E.g.:

```yml
define:
  - common_node:
      range: 50,
      speed: 2
  
  - backhaul_node:
      range: 100,
      speed: 5

topology:
  node1:
    type: common_node
    connections:
      - node2, node4, node7
      
    node2:
    type: common_node
    connections:
      - node1,
      
     ... 
````

Or you can let `smesh` generate a random topology for you. E.g.:

```yml
define:
  - common_node:
      range: 50,
      speed: 2
  
  - backhaul_node:
      range: 100,
      speed: 5

random_topology:
  nodes: 25,
  types:
    - common_nodes
```

After configuring your network, you can run `smesh`. There are commands to send package from one node to another, list nodes, show topology, make various nodes send messages to another nodes.
