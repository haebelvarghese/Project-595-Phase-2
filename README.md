# Neuromorphic-Computing-Haebel
Project for the EE-595 Summer Course. We are designing a algorithm-hardware co-optimization framework.

# Neuromorphic Computing using Memristors

## Team Members

### Haebel Varghes, Lei Ding, Shreya Nandy

My student ID: 5736637176

This repo hosts resources and codes for EE 595 project "Neuromorphic Computing using Memristors"


## Preliminary summary

<https://1drv.ms/w/s!AvC8SENWufoEg_IzbgfqYzRMZy6Zjw?e=y14cfb>

## Proposal

<https://docs.google.com/document/d/1Sb3gQYsvauGhS4CUvpPSOWDSfVPKRJBNzcIC0ySyt54/edit?pli=1>

## Phase 1

<https://github.com/haebelvarghese/Neuromorphic-Computing-Haebel.git>

### Phase 2 update

### Abstract

Spiking Neural Networks on neuromorphic hardware have a lot of advantages, hence it is used for efficient implementation of deep neural networks. But as we design more complex deep neural networks, we need to find better methods to reduce the storage size and the time required for computing. In this paper we are using the model compression technique to optimize our SNN. We are hence designing an algorithm-hardware co-optimization framework that will improve the hardware usage and at the same time keep the accuracy of the neural network high.   

### Problem Description

The team aims to study and produce a framework that optimizes Spiking Neural Network (SNN) by utilizing model compression techniques including weight pruning and weight quantization considering the simulation of such neural network is very power hungry. In adidtion to such optimization, a major goal of such framework is the ability to transform an optimized SNN to an actual hardware based simulation using components specifically designed for different neural networks. The team believes that the optimization of SNN and ability to transform software design to hardware design within the same framework will help advance the research and development of SNN related hardwares and broaden SNN driven applications.

The team has two groups studying two aspects of the problem: software and hardware. On the software side, the focus is on implementing and optimizing a given SNN model with model compression techniques mentioned above. Furthermore, a visualizer that helps understand the network topology is to be developed.

### Project Timeline

We have understood the hardware simulator.We have modified the hardware simulator to run the neural network. We need to run the original neural network and compare the results.

### Hardware part

## Description of the TrueNorth chip
The TrueNorth chip was designed by IBM to do neuromorphic computing. The chip follows a spiking neural network approach to do various kinds of deep learning. Using spiking neural networks has a lot of power advantages in hardware. Also the aim of chip is to provide scalable communication techniques among the multiple cores in the chip. The core is the repeating element of the TrueNorth chip. A chip consists of 64 x 64 cores i.e. 4096 cores. The neural network is designed across these cores or maybe even across multiple chips if the network is huge.

## Description of the core
The core is the main working part of the chip. A core has 256 neurons and 256 axons and 256 x 256 synapses. The neurons act as the output or where the computation occurs. The axon acts as the input to which the spike inputs can be given. The synapses refer to the connections between the axons and the neurons. Each synapse can have a weight value as inhibitory or excitatory. 

The neurosynaptic core consists of five parts for its operation:
1)	Neuron – the neuron does the synaptic integration and the threshold voltage updation.
2)	Memory – the memory consists of the neuron information as in the connections and the destinations if a spike occurs. 
3)	Scheduler – the scheduler stores the spike data. This spike data will then be given to the axons which act as the inputs.
4)	Router – the router transfers the spike data from the neuron which fires to the scheduler of the destination core.
5)	Controller – the controller takes the spike data from the scheduler and the neuron information from the memory and starts the neuron computation. If spike occurs then it sends the spike to the router.

## Modifications to the code
•	The current TrueNorth chip simulator consists of random input values stored to the sram and the computation occurs. We have modified the code to get the input from a file and then store it to the SRAM memory.
•	The inputs are supposed to be given as a spike train, but as then the file would to too big, the input is given with a spike rate. This spike rate is given to the input neurons. The code is modified to read the spike rate and fire the input neurons accordingly.
•	The neural network connection on the chip is decided before hand. As each core can only handle 256 neurons, we need to use multiple cores for our neural network. The design of the network on the chip must be decided and given in the input file.
•	The output spike data should be stored into a file. So that a comparison can be done with the software simulator.

### Papers for phase 2
[1] Sawada, Jun, Filipp Akopyan, Andrew S. Cassidy, Brian Taba, Michael V. Debole, Pallab Datta, Rodrigo Alvarez-Icaza et al. "Truenorth ecosystem for brain-inspired computing: scalable systems, software, and applications." In SC'16: Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis, pp. 130-141. IEEE, 2016.

This paper focuses on the applications of Truenorth simulator and provides an end-to-end ecosystem ( specifying, training and deploying neural networks) for both software and hardware implementation of it. It presents different layers in the ecosystem which can be used for neurosynaptic computing. It provides techniques to reduce intra and inter chip network traffic. This paper also looks into the test and verification part by comparing the duplicated copies of every normal spike with the spikes computed by the simulator to find out the discrepancy. The main principle in the paper is demonstrating two systems: the NS1e- 16 scale-out system and the NS16e scale-up system, describing a full developed workflow for the neural network algorithms along with libraries and software tools, mapping of hardware locations to logical network representations and proving deployment status of the system.

[2] Akopyan, Filipp, Jun Sawada, Andrew Cassidy, Rodrigo Alvarez-Icaza, John Arthur, Paul Merolla, Nabil Imam et al. "Truenorth: Design and tool flow of a 65 mw 1 million neuron programmable neurosynaptic chip." IEEE transactions on computer-aided design of integrated circuits and systems 34, no. 10 (2015): 1537-1557.

This paper discusses the architecture of the Truenorth simulator and provides a tool flow for the hardware implementation of it.  It provides different algorithms and analyses each to see the power consumption by the simulator. The mixed asynchronous and synchronous approach is taken into consideration while suggesting the scaling of the Truenorth architecture.

[3] Wen, Wei, Chunpeng Wu, Yandan Wang, Kent Nixon, Qing Wu, Mark Barnell, Hai Li, and Yiran Chen. "A new learning method for inference accuracy, core occupation, and performance co-optimization on TrueNorth chip." In 2016 53nd ACM/EDAC/IEEE Design Automation Conference (DAC), pp. 1-6. IEEE, 2016.

This paper focuses on the accuracy of the results provided by the truenorth simulator and improving the same. The impact of low data precision is analysed on inference accuracy, core occupation, and performance in the simulator. It then proposes a learning method  which relies on probability to enhance the inference accuracy and reduce the random variance of each computation copy. Different test bench are created and the simulator is tested on the same and then the accuracy results are computed.

[4]Cassidy, A., Sawada, J., Merolla, P., Arthur, J., Alvarez-lcaze, R., Akopyan, F., Jackson, B. and Modha, D., 2016, March. TrueNorth: A high-performance, low-power neurosynaptic processor for multi-sensory perception, action, and cognition. In Proceedings of the Government Microcircuits Applications & Critical Technology Conference, Orlando, FL, USA (pp. 14-17). 
Learned about the Truenorth chip and how it improved neuromorphic computing.

[5]Tavanaei, A., Ghodrati, M., Kheradpisheh, S.R., Masquelier, T. and Maida, A., 2019. Deep learning in spiking neural networks. Neural Networks, 111, pp.47-63.
Understood more deeply about SNNs.

[6]https://towardsdatascience.com/deep-learning-versus-biological-neurons-floating-point-numbers-spikes-and-neurotransmitters-6eebfa3390e9
Studied about the biological neural network and how it is implemented.

[7]Markram, H., Gerstner, W. and Sjöström, P.J., 2012. Spike-timing-dependent plasticity: a comprehensive overview. Frontiers in synaptic neuroscience, 4, p.2.

This paper comprehensively introduces the history of the study of the spiking-timing-dependent plasticity property of biological neuronal network. The paper explained why timing of biological signals is important and how such binary signal form can make neuronal network so complicated and enables incredible ability like learning and adapting. This paper helped us to obtain better understanding of the spiking neural network from a biological perspective.

[8]Morrison, A., Aertsen, A. and Diesmann, M., 2007. Spike-timing-dependent plasticity in balanced random networks. Neural computation, 19(6), pp.1437-1467.

This paper discusses the benefit of introducing spike-timing-dependent plasticity (STDP) into the artificial neuronal network. It also investigates how high level of network connectivity would affect the neuron dynamics. The papers gives us a very good example of how STDP can be implemented in an artificial spiking neural network.

[9]Turrigiano, G.G. and Nelson, S.B., 2000. Hebb and homeostasis in neuronal plasticity. Current opinion in neurobiology, 10(3), pp.358-364.

This paper investigates how STDP property enables neuronal network to facilitate Hebbian unsupervised learning and introduces a new property called homeostasis, which suppresses the activity of certain neurons that fire too frequently so that they do not negatively affect other neurons in the network. This vies us insight about how a learning algorithm can be implemented using SNN, STDP and homeostasis property.

[10]Kheradpisheh, S.R., Ganjtabesh, M., Thorpe, S.J. and Masquelier, T., 2018. STDP-based spiking deep convolutional neural networks for object recognition. Neural Networks, 99, pp.56-67.

This paper discusses about an actual complete example of SNN running certain learning algorithms. We learned how input data is preprocessed and how network is constructed with STDP systematically. This paper provides a good example of how we can construct an effective learning scheme using SNN.

[11]Querlioz, D., Bichler, O., Dollfus, P. and Gamrat, C., 2013. Immunity to device variations in a spiking neural network with memristive nanodevices. IEEE Transactions on Nanotechnology, 12(3), pp.288-295.

This paper gives us another example of how SNN learning can be achieved and how it can be implemented using memristive nanodevices. It describes how synaptic behavior and neuron dynamics are defined and implemented in the system, which helps us to better understand the structure needed to build an effective SNN.

[12]Marcel, S. and Romain, B., 2019. Brian 2, an intuitive and efficient neural simulator. eLife, 8.

This paper introduces the fundamental working mechanics behind the Brian 2 spiking neuron network simulator. The paper gives us better insight on how the simulator should be manipulated to realize our SNN design and how to compress the network as well. 


