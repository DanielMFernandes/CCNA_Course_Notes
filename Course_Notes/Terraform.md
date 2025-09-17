Infrastructure as Code

- Infrastructure as Code (IaC) is the practice of provisioning and managing infrastructure (servers, networks, cloud resources) using machine-readable configuration files (code) instead of manual configuration (e.g., CLI/GUI).

- Ansible, Puppet, and Chef are examples of IaC configuration management tools.
  - Ansible manages device configurations using several files:

![image](https://github.com/user-attachments/assets/c6b7dd53-2c47-437d-b79b-15b321a0b0e8)

- Terraform is an IaC-based provisioning tool that automates the creation of infrastructure resources.

- IaC automates infrastructure deployment and management, ensuring consistency, scalability, and repeatability.


-----

Configuration management (e.g., Ansible, Puppet, Chef)
- Manages existing infrastructure by installing software, configuring settings, and maintaining system state.
- Ensures consistency by applying and enforcing configurations across multiple devices.

Infrastructure provisioning (e.g., Terraform)
- Creates, modifies, and deletes infrastructure resources such as servers and network infrastructure.
- Focuses on initial setup rather than ongoing configuration management.

Configuration management tools work on already existing systems, whereas provisioning tools build infrastructure from scratch.

Terraform (provisioning) and Ansible (configuration management) can work together:
- Terraform provisions infrastructure (VMs, networks, storage, etc.), and Ansible provides ongoing configuration and management.

![image](https://github.com/user-attachments/assets/dc535bdc-9526-4a55-9f29-14765464c244)

-------

Configuration management tools typically use a mutable infrastructure approach.
- Infrastructure can be modified after deployment (e.g., applying updates, patches, or configuration changes)
- Changes are made in place, meaning existing resources are updated rather than replaced.

![image](https://github.com/user-attachments/assets/36d5e8ae-f960-4db2-b44e-770bad8ae9a1)

Provisioning tools employ an immutable infrastructure approach.
- Infrastructure cannot be changed after deployment. “Changes” involve replacing the previous resource with a new version.
- No configuration drift, since each deployment starts from a fresh, predefined state.

![image](https://github.com/user-attachments/assets/23995061-1b43-4d03-a74b-58f39e667213)

--------
PROCEDURAL VS DECLARATIVE

Procedural approach (a.k.a. Imperative)
- Follows explicit steps in a specific order to achieve the desired outcome.
- The user must define each action to configure the infrastructure.
- Provides greater control compared to a declarative approach.

Declarative approach
- Defines the desired end state.
- The tool (e.g., Terraform) figures out the steps needed to achieve the goal.
- Easier to maintain and ensures consistency across deployments.

A procedural approach focuses on how to make changes (explicit steps).
- “Configure router’s hostname with hostname R1”
- “Configure the IP address of G0/1 with ip address 192.168.1.1 255.255.255.0”
- “Enable the interface with no shutdown”
  
A declarative approach focuses on what the final state should be.
- “Create a router named R1 with IP address 192.168.1.1/24 on its G0/1 interface, ensuring the interface is enabled”.

![image](https://github.com/user-attachments/assets/4c629acc-39c9-48ad-9c9b-794a4f1de0fa)

----
TERRAFORM

Terraform is an open-source IaC tool developed by HashiCorp (acquired by IBM in 2025).

It is primarily a provisioning tool, focused on deploying infrastructure resources on various cloud & on-prem platforms.

- These platforms are called providers and include AWS, Azure, GCP, Kubernetes, and many more (1000+).
  - This includes integrations with Cisco platforms like Catalyst Center, ACI, and IOS XE.

Like Ansible, Terraform uses a push model and is agentless; it doesn’t require a software agent on infrastructure it provisions or manages.

![image](https://github.com/user-attachments/assets/c445ff2a-e4aa-4639-b391-afbc7b448186)

The basic Terraform workflow consists of three main steps:
- Write: Define the desired state of your infrastructure resources in configuration files.
- Plan: Verify the changes that will be executed before applying them.
- Apply: Execute the plan to provision and manage the infrastructure resources.

While Terraform Core is written in Go, configuration files are written in HashiCorp Configuration Language (HCL).
- HCL is an example of a domain-specific language (DSL), a type of language specialized for a particular purpose.
  - Because DSLs are specialized, they allow users to perform complex tasks with much less effort than a general language (like Python or Go) would require.


