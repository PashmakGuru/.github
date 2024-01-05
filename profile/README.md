# Pashmak Guru: A Learning Journey in Infrastructure-as-Code (IaC)

> [!NOTE]  
> Please be advised that this project is currently in its development phase. As such, not all features and functionalities are fully implemented at this moment.

## Introduction to Pashmak Guru

Pashmak Guru is a GitHub organization where we, as a team of learners and enthusiasts, explore the principles of Infrastructure-as-Code (IaC). We use Terraform modules to build infrastructure on Microsoft Azure, to learn various topics and keep them here for people who are interested in learning too. This organization demonstrates how IaC can be applied, albeit not with the polish of a production-ready project. See the [Pashmak Guru repositories](https://github.com/orgs/PashmakGuru/repositories).

## Our Approach

- **Practical Examples with Terraform and Azure:** We provide examples and experiments that we conduct in real-time, showcasing our learning journey in creating infrastructure on Azure.
- **Integration with Port Internal Developer Platform:** We use this platform as part of our learning to understand better how different tools work together.

## Architecture
Here is a C4 component-level diagram of the whole organization IaC and IDP integration:
```mermaid
C4Container

Person(platform_admin, "Platform Admin", "Owner of the infrastructure")
Person(platform_engineer, "DevOps/Platform Engineer", "Developer of the platform")
Person(developer, "Developer", "Developer and software engineers")

System_Ext(azure, "Microsoft Azure", "Cloud Computing Platform<br>azure.microsoft.com")
System_Ext(tfc, "Terraform Cloud", "Terraform Cloud SaaS<br>app.terraform.io")
System_Ext(port, "Port IDP", "Port Internal Developer Platform<br>app.getport.io")
System_Ext(github, "GitHub", "GitHub<br>github.com")

Container_Boundary(c_github, "GitHub Repositories") {
    Container(platform_internals, "Platform Internals", "bash, terraform, workflow", "Bootstrap and manage<br>infrastructure prerequisites.")
    Container(platform_repo_scaffolder, "Platform Repository Scaffolder", "cookiecutter, workflow, vuejs, golang", "Scaffolding and managing<br>repositories and templates.")
    Container(platform_cloud_resources, "Platform Cloud Resources", "terraform, workflow", "Manage cloud resources<br>on Azure.")
    Container(terraform_azure_kubernetes_cluster, "Kubernetes Cluster<br>Terraform Module", "terraform, workflow", "Manage Azure Kubernetes<br>Service.")
    Container(terraform_azure_front_hub, "Fronthub<br>Terraform Module", "terraform, workflow", "Manage Azure DNS Zone and<br>Front Door.")
    Container(terraform_azure_administrative_argocd, "Administrative ArgoCD<br>Terraform Module", "terraform, workflow", "Deploy and manage<br>Administrative ArgoCD.")
    Container(terraform_azure_blob_storage, "Blob Storage<br>Terraform Module", "terraform, workflow", "Manage Azure Blob Storage.")
    Container(gha_platform_orchestrator, "Platform Orchestrator<br>GitHub Action", "golang, workflow, action", "Preparing requirements of<br>Platform Cloud Resources.")
    Container(gha_port_labs_cookiecutter, "Port Cookiecutter<br>GitHub Action", "forked", "Scaffolding templates using<br>cookiecutter.")
}

%% Person Relations
Rel(developer, port, "Uses")
Rel(platform_engineer, port, "Uses")
Rel(platform_engineer, port, "Uses")
Rel(platform_engineer, platform_internals, "Updates")
Rel(platform_admin, port, "Initiates")
Rel(platform_admin, azure, "Initiates")
Rel(platform_admin, tfc, "Initiates")
Rel(platform_admin, platform_internals, "Fetches")

%% System Relations
Rel(tfc, azure, "Manages")
Rel(tfc, tfc, "Manages")
Rel(tfc, port, "Manages")
Rel(port, platform_repo_scaffolder, "Dispatches")
Rel(port, platform_cloud_resources, "Dispatches")

%% Component Relations
Rel(platform_internals, tfc, "Runs")
Rel(platform_repo_scaffolder, github, "Creates/Deletes")
Rel(platform_repo_scaffolder, gha_port_labs_cookiecutter, "Uses")
Rel(platform_cloud_resources, terraform_azure_kubernetes_cluster, "Uses")
Rel(platform_cloud_resources, terraform_azure_front_hub, "Uses")
Rel(platform_cloud_resources, terraform_azure_administrative_argocd, "Uses")
Rel(platform_cloud_resources, terraform_azure_blob_storage, "Uses")
Rel(platform_cloud_resources, gha_platform_orchestrator, "Runs")
Rel(gha_platform_orchestrator, platform_cloud_resources, "Modifies")
Rel(platform_cloud_resources, tfc, "Runs")

UpdateRelStyle(platform_repo_scaffolder, github, $offsetY="-20", $offsetX="30")
UpdateRelStyle(platform_repo_scaffolder, gha_port_labs_cookiecutter, $offsetY="-80", $offsetX="-65")
UpdateRelStyle(gha_platform_orchestrator, platform_cloud_resources, $offsetX="-60")

UpdateElementStyle(terraform_azure_kubernetes_cluster, $bgColor="#844FBA")
UpdateElementStyle(terraform_azure_front_hub, $bgColor="#844FBA")
UpdateElementStyle(terraform_azure_administrative_argocd, $bgColor="#844FBA")
UpdateElementStyle(terraform_azure_blob_storage, $bgColor="#844FBA")
UpdateElementStyle(gha_platform_orchestrator, $bgColor="#a67b40")
UpdateElementStyle(gha_port_labs_cookiecutter, $bgColor="#a67b40")
```

## Who Is This For

- **Aspiring Cloud Enthusiasts:** Perfect for those who are starting their journey in cloud computing and want to learn alongside a team doing the same.
- **Students & Hobbyists:** If you're interested in exploring cloud infrastructure and IaC, our repositories offer real-time learning scenarios.

## Getting Started

Dive into our repositories, each equipped with instructions and insights into our learning process. Pick any project that interests you and follow along.

## Contributing

We welcome contributions of all kinds! Feel free to suggest improvements, share your learning, or even help us understand best practices.

## Connect With Us

Join our journey and share your experiences. We’re all learning together and your input is valuable in this shared path. Let's [discuss](https://github.com/PashmakGuru/.github/discussions/categories/general) about your ideas!
