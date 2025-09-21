# test

Kubernetes (K8s) architecture follows a master-worker model, comprising a Control Plane and Worker Nodes. 
1. Control Plane (Master Node Components): This is the brain of the cluster, making global decisions and responding to cluster events. Its key components are:
kube-apiserver: The central interface, exposing the Kubernetes API and handling all communication within the cluster. It validates and processes requests, authenticates users, and stores the cluster state in etcd.
etcd: A highly-available key-value store that serves as Kubernetes' backing store for all cluster data. It acts as the single source of truth for the cluster's state.
kube-scheduler: Responsible for scheduling pods onto appropriate worker nodes based on resource requirements, policies, and other constraints.
kube-controller-manager: Runs various controllers that manage the cluster's state, such as the replication controller (ensuring desired replica counts), node controller (managing node status), and endpoint controller (connecting services to pods).
cloud-controller-manager (optional): Integrates Kubernetes with cloud provider APIs to manage cloud-specific resources like load balancers, persistent volumes, and node lifecycle.
2. Worker Nodes (Data Plane Components): These are the machines where containerized applications (pods) run. Each worker node contains:
kubelet: An agent that communicates with the Control Plane, ensuring that containers within pods are running and healthy as specified by the API server. It manages the lifecycle of pods and their containers.
kube-proxy: Maintains network rules on nodes, enabling network communication to and from pods, and performs load balancing for services.
Container Runtime: An engine responsible for running containers (e.g., Docker, containerd, CRI-O). It executes the container images within pods.
