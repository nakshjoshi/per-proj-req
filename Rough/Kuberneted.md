Bare metal deployment: it is like setting up server at home or kinda locally renting them and deploying apps on them(dependecies checked) and exposding theit IP add publically for everyone to use them
Server: physical machien on 24/7 , has public and static IP
code behavior on server === code behavior on local machien, replicate dependencies and versiosn

AWS: cloud nativee tech like Static IP, elastic LB, CDN(cloudfront), Auto scaling groups were esailt made available, issue: it only works on my PC
Virtualizstion: deiced own OS version, own depencdencies, package them into a system image nd deploy or install anywhere, but due to OS also being in image the size of image for too high, later we removed OS from the virtualization and here comes the concept of docker and containers, (key goal: same behaviors cross platform)

It was hard to manage container creatingf aand restroying them and handling based on traffic on website, her ecomes a large scale cluster mgmt softaware by google , google borg, what they do is basically called container orchestration...later google mage kuberetes, kinda open sources version of borg adn donated it to CNCF, whagt is does is basically container mgmt - deploting, scaling, security and destroying.....kubertes is cloud agnostic aas open sources prevents vendor lockin 

AWS ESC : just upload you docke rimage here 

Kuberneted Arfchitecture: Control Plane(api sever, sontorller, etcg(KV store))
Worling node(kubelet, kube proxy, Container Runtime interface)