<img src="images/purdue-cs-logo.jpg" alt="drawing" width="450"/>

# Reproducing "Dynamic Adaptation of Software-defined Networks for IoT Systems: A Search-based Approach"

**Members:** [Agresh Bharadwaj](https://www.linkedin.com/in/agreshb/), [Ayush Garg](linkedin.com/in/ayushgarg99/), [Tulika Sureka](https://www.linkedin.com/in/tulikasureka/), [Vishnu Teja Narapareddy](https://www.linkedin.com/in/vishnu-teja-n/), and [Vivek Gupta](https://www.linkedin.com/in/guptav96/)

### Introduction
IoT-enabled applications depend on a communication network for transmitting large volumes of data in unpredictable and changing environments. 
These networks are prone to congestion when there is a burst in demand, e.g., as an emergency situation is unfolding, and therefore rely on configurable software-defined networks (SDN). The goal of this project is to reproduce the novel approach proposed in Dynamic Adaptation of Software-defined Networks for IoT Systems: A Search-based Approach (DICES) which is a dynamic adaptive SDN configuration approach for IoT systems.
<p float="center" >
  <img src="images/EMS_DESIGN.png" alt="Example of an Emergency Monitoring System IoT Network" width="400"/>   
 
</p>

### Motivation
The motivation behind reproducing this novel approach is to understand how the resolution of congestion is done in real-time by minimizing network utilization, data transmission delays, and adaptation costs. 
The approach builds on existing work in dynamic adaptive search-based software engineering (SBSE) to reconfigure an SDN while simultaneously ensuring multiple quality-of-service criteria


### Methodology
Implementation for the DICES algorithm was done in java. We created a new java application with a Reactive Forwarding as the base code. We used the reactive forwarding command and reactive forwarding metrics code from onos opensource GitHub repository. We modified the existing reactive forwarding code in both activate and deactivate steps. In the activate step, we setup all the dependend classes and initialize these values and create a new DynamicAdaptiveControlTask object. This task object extends the java TimerTask class. This makes it easy to schedule our DynamicAdaptiveControlTask on a parallel thread using the existing java timer. We also modify the existing link weight paths to inlcude our DICES generated DynamicLinkWeights when calculating the paths in reactive forwarding packet processor. In the deactivate method, we also ensure to stop the DynamicAdaptiveControlTask. This completes the setup of DICES and its integration with reactive forwarding.


### Discussion
<p float="center" >
  <img src="images/exp1_delay.png" alt="Average Delay" width="300"/>    <img src="images/packetloss_exp1.png" alt="Average Packet Loss" width="305"/>  
 

<p float="center" >
  <img src="images/exp2_links.png" alt="Example of an Emergency Monitoring System IoT Network" width="300"/>   
  <img src="images/exp2_links.png" alt="Example of an Emergency Monitoring System IoT Network" width="300"/>   

</p>



### Conclusion
We conclude that this search-based approach, DICES is able to dynamically mitigate network congestion via network reconfiguration. It is realized through a feedback-loop control mechanism that executes periodically and reconfigures the SDN when the congestion is detected. The reconfiguration action is computed using a tailored multi-objective search algorithm which minimizes network-link utilization, transmission delay and reconfiguration costs. We were able to reproduce the results for the two research questions we were interested in, relating to the effectiveness and scalability of DICES. Our results indicate that: (1) DICES efficiently and effectively adapts an SDN to resolve congestion, and (2) DICES scales to real-world systems, since the execution time scales linearly with the network size and the number of requests. 