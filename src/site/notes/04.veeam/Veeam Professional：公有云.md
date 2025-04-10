---
{"dg-publish":true,"permalink":"/04.veeam/Veeam Professional：公有云/"}
---

# 云的备份和复制

## 采用 Veeam 的公有云备份

Veeam 提供强大的解决方案来增强您的公有云备份策略。借助 Veeam，您可以保护 AWS、Azure 和 Google Cloud 等常见公有云环境中的各种工作负载和数据类型。它为创建映像级备份、利用云原生快照和确保数据可用性提供了高效的工具。Veeam 还通过多个恢复选项简化了恢复，并通过智能数据管理最大限度地降低了成本。无论您是需要保护关键工作负载、满足合规性要求，还是增强云中的业务连续性，Veeam 都能为您提供工具和专业知识，以优化您的公有云备份策略。

本模块将重点介绍如何安装和配置 Veeam Backup _for AWS、Azure 和 Google Cloud。_第一步是熟悉数据架构中跨兼容云平台使用的一些组件：
![Pasted image 20250410143208.png](/img/user/99.picture/Pasted%20image%2020250410143208.png)


---

### 备份一体机
备份设备是基于 Linux 的虚拟机实例，其中安装了 Veeam Backup f_或 Google Cloud__、AWS 和 Azure_。备份设备执行以下管理活动：

- 管理架构组件。
- 协调快照创建、备份和恢复任务。
- 控制备份策略计划。
- 生成每日报告和电子邮件通知。

备份设备还维护配置数据库，用于存储从 Veeam Backup for Cloud Platform 收集的数据，用于现有备份策略、受保护的虚拟机实例和云 SQL 实例、已部署的工作实例、连接的 Google Cloud 项目等。
### 备份存储库
备份存储库是云存储桶中的一个子目录，适用于受支持云平台的 Veeam Backup 可在其中存储受保护虚拟机实例和云 SQL 实例的备份。

为了与备份存储库通信，Veeam Backup & Replication使用Veeam Data Mover，该服务在工作实例上运行并负责数据处理和传输。当备份策略针对备份存储库时，Veeam Data Mover 会与存储库建立连接以支持数据传输。
### Worker 实例
工作实例是一个辅助的基于Linux的VM实例，它与备份设备和其他Veeam Backup&Replication架构组件进行交互。工作实例在将数据传入和传出备份存储库时处理备份工作负载并分配备份流量。

这会在备份或还原过程期间自动在云中部署工作实例，并在该过程结束后立即将其删除。根据执行的作，Veeam Backup for Google Cloud 将工作实例部署在不同位置，以最大限度地降低跨区域流量费用并加快数据传输速度。

有关数据存储位置的更多信息，请单击[了解更多信息！](https://helpcenter.veeam.com/docs/vbgc/guide/overview_worker_instances.html?ver=50)

---

# 从Veeam Backup & Replication部署

##  公有云平台部署

Veeam Backup&Replication为您的公共云工作负载提供无缝的备份部署和配置，为托管在AWS、Azure或其他领先云平台中的环境提供全面的数据保护。凭借其灵活的部署选项，Veeam 使企业能够有效地保护其在公有云中的关键数据，确保数据可用性、简化的管理和可靠的灾难恢复功能。
![Pasted image 20250410143421.png](/img/user/99.picture/Pasted%20image%2020250410143421.png)
Veeam Backup&Replication简化了直接从其界面部署公共云平台的过程，使企业能够快速配置和配置云资源以进行数据保护和灾难恢复。借助原生集成和自动化功能，Veeam 支持企业将其备份基础架构无缝扩展至公有云平台，从而确保云中的数据可用性和弹性。
![Pasted image 20250410143440.png](/img/user/99.picture/Pasted%20image%2020250410143440.png)


# 从 Marketplace 部署

通过利用 Marketplace 部署选项，企业可以轻松访问和部署 Veeam 的全面数据保护功能，确保在所选云环境中执行高效的备份、复制和恢复作。这种简化的方法简化了部署流程，使企业能够直接从其首选市场快速利用 Veeam 强大的备份和复制功能。


---

### AWS 市场
1. **使用 CloudFormation 模板安装 Veeam Backup for AWS（推荐）**
    - Veeam Backup _for AWS_ 安装在单个 Amazon EC2 实例上。Amazon EC2 实例是在产品安装期间创建的。
    - Veeam Backup _for AWS_ 会自动创建备份设备配置以及执行备份和灾难恢复作所需的 2 个 IAM 角色。
2. **从 AMI 安装 Veeam Backup for AWS**
    - Veeam Backup _for AWS_ 安装在单个 Amazon EC2 实例上。Amazon EC2 实例是在产品安装期间创建的。
![Pasted image 20250410143710.png](/img/user/99.picture/Pasted%20image%2020250410143710.png)
### Microsoft Azure 市场
从 Microsoft Azure Marketplace 部署 Veeam 一体机后，可在云环境中直接设置 Veeam 备份解决方案。

- 此过程包括从 Azure Marketplace 中选择 Veeam 一体机，并根据 Azure 管理控制台中的特定备份和恢复需求对其进行配置。
- 该部署支持与 Azure 服务集成，确保数据在云和混合环境中受到保护，并根据需要提供自动化和扩展选项。
![Pasted image 20250410143735.png](/img/user/99.picture/Pasted%20image%2020250410143735.png)
### Google Cloud 市场
从 Google Cloud Marketplace 部署 Veeam 一体机有助于将 Veeam 备份和恢复解决方案集成到 Google Cloud Platform （GCP） 环境中。

- 它包括从 Google Cloud Marketplace 中选择 Veeam 一体机，并利用 GCP 的管理工具配置其设置以满足特定的数据保护要求。
- 此部署支持与 GCP 服务无缝集成，提供为云原生和混合云架构量身定制的可扩展和自动化数据备份解决方案。
![Pasted image 20250410143751.png](/img/user/99.picture/Pasted%20image%2020250410143751.png)


---

![Pasted image 20250410143805.png](/img/user/99.picture/Pasted%20image%2020250410143805.png)

# 适用于 AWS/Azure/Google Cloud 的 Veeam Backup
![Pasted image 20250410144047.png](/img/user/99.picture/Pasted%20image%2020250410144047.png)
## 在 AWS 中执行备份作业
备份副本是一个强大的安全网，让您可以完全控制 Microsoft 365 数据，并在必要时为您提供无缝恢复选项。单击下面的选项卡，详细了解您可以对使用 Microsoft 365 创建的备份副本执行哪些作：

---
### 创建 Amazon EC2 实例和 Amazon RDS 资源的云原生快照
Amazon EC2 实例的云原生快照包括附加到已处理实例的 Amazon EBS 卷的时间点快照。这些快照（也称为 Amazon EBS 快照）是使用原生 AWS 功能拍摄的。

数据库实例的云原生快照包括实例的存储卷快照。数据库实例的快照（也称为数据库快照）是使用本机 AWS 功能拍摄的。
 
Aurora 数据库集群的云原生快照包括备份整个集群的存储卷快照，而不仅仅是单个数据库。Aurora 数据库集群的快照（也称为数据库集群快照）是使用本机 AWS 功能拍摄的。

### 将云原生快照复制到远程站点
默认情况下，云原生快照仅存储在已处理实例所在的 AWS 区域中。为了增强数据安全性，您可以指示 Veeam Backup _for AWS_ 创建云原生快照的副本，并将其存储在任何 AWS 账户内的任何其他 AWS 区域。您还可以将快照复制功能与各种数据恢复选项相结合，以在 AWS 区域和 AWS 账户之间迁移实例数据。

### 创建 Amazon EC2 实例的映像级备份
除了云原生快照之外，您还可以使用映像级备份来保护 Amazon EC2 实例。映像级备份捕获已处理的 Amazon EC2 实例（包括实例配置、作系统数据、应用程序数据等）在特定时间点的整个映像。备份以本机 Veeam 格式保存到备份存储库中。

### 创建 Amazon EFS 文件系统的备份和备份副本
Amazon EFS 文件系统备份可捕获 Amazon EFS 文件系统在特定时间点的整个映像（包括文件系统配置、文件、目录等）。Amazon EFS 备份是使用原生 AWS 功能进行的。

默认情况下，Amazon EFS 备份仅存储在已处理文件系统所在的 AWS 区域中。为增强数据安全性，您可以指示 Veeam Backup for AWS 创建这些备份的副本，并将其存储在同一 AWS 账户内的任何其他 AWS 区域。您可以将备份复制功能与各种数据恢复选项相结合，以在 AWS 区域之间迁移文件系统数据。

---
为确保自动数据保护，请创建备份策略并按需执行 Amazon EC2 实例、Amazon RDS 资源和 Amazon EFS 文件系统等 AWS 资源。此外，您可以手动启动备份以提高灵活性和控制力。要了解有关备份策略的更多信息，请参阅[管理 EC2、RDS 和 EFS 备份策略。](https://helpcenter.veeam.com/docs/vbaws/guide/policies_ec2_manage.html?ver=70)

## 为 AWS 执行还原

Veeam Backup _for AWS_ 支持您快速恢复 Amazon EC2 实例、Amazon RDS 数据库和 Amazon EFS 文件系统，从而在数据意外丢失或系统故障期间实现无缝恢复。借助灵活的还原选项，您可以高效地恢复特定数据、整个实例或数据库，以确保 AWS 环境中的业务连续性。

在各种灾难恢复场景中，Veeam Backup _for AWS_ 允许您使用备份数据执行以下还原作：

### 还原 EC2 实例
将 Amazon EC2 实例从原生云快照、快照副本或映像级备份还原到原始位置或新位置。Veeam Backup _for AWS_ 提供以下还原选项：

- **Instance Restore （实例还原**） – 还原整个 Amazon EC2 实例。
- **卷还原** — 还原附加到 Amazon EC2 实例的 Amazon EBS 卷。
- **文件级还原** — 还原 Amazon EC2 实例的单个文件和文件夹。

您可以将 Amazon EC2 实例数据恢复到最新状态或任何可用的还原点。
### 还原 RDS 实例
在灾难中，您可以从云原生快照、快照副本或 AWS 快照还原数据库实例或 Aurora 数据库集群。Veeam Backup _for AWS_ 支持您一次将一个或多个 Amazon RDS 资源还原到原始位置或新位置。不支持使用 gp3 存储卷还原 Amazon RDS 资源。
### 还原 EFS 文件系统
将文件系统从备份还原到原始位置或新位置。Veeam Backup _for AWS_ 提供以下还原选项：

- **File System Restore （文件系统还原**） – 还原整个 Amazon EFS 文件系统。
- **文件级还原** — 还原存储在文件系统中的单个文件和文件夹。

您只能将 Amazon EFS 文件系统还原到源文件系统所属的同一 AWS 账户。您还可以将 Amazon EFS 文件系统数据恢复到最新状态或任何可用的还原点。
### 恢复 VPC 配置
将 Amazon VPC 配置从 Amazon VPC 配置备份还原到原始位置或新位置。Veeam Backup _for AWS_ 提供以下灾难恢复作：

- **Amazon VPC 配置还原** — 还原整个 Amazon VPC 配置。
- **Selected Items Restore （所选项目还原**） – 还原所选 Amazon VPC 配置项。

您可以将 Amazon VPC 配置数据恢复到最新状态或任何可用的还原点。


## 执行 Azure 备份 
Veeam Backup _for Microsoft Azure_ 利用原生 Azure 功能，无需安装代理软件即可检索实例中的数据。相反，它会在每次备份会话期间为 Azure VM 和 Azure 文件共享或 Azure SQL 数据库创建 BACPAC 文件，从而实现受保护 Azure 资源的映像级备份。

单击每个选项卡以了解有关在 Microsoft Azure 中保护数据的不同方法的更多信息：


---

### 创建 Azure VM 的云原生快照
云原生快照包括附加到已处理 Azure VM 的虚拟磁盘的时间点快照。虚拟磁盘的快照是使用[本机 Microsoft Azure 功能。（在新选项卡中打开）](https://learn.microsoft.com/en-us/azure/virtual-machines/snapshot-copy-managed-disk?tabs=portal)

### 创建 Azure VM 的映像级备份

除了云原生快照之外，您还可以使用映像级备份来保护 Azure VM。映像级备份捕获已处理的 Azure VM 在特定时间点的整个映像（包括 OS 数据、应用程序数据等）。备份将作为多个文件保存到[原生 Veeam 格式。（在新选项卡中打开）](https://helpcenter.veeam.com/docs/vbazure/guide/backup_chain_vm.html?ver=60)

### 创建 Azure SQL 数据库的映像级备份

Azure SQL 数据库的映像级备份捕获已处理数据库（包括表、约束、索引和实际数据）在特定时间点的整个映像。备份将作为多个文件以原生 Veeam 格式保存到备份存储库中。

### 创建 Azure 文件共享的云原生快照

云原生快照包括基本文件、元数据和已处理的 Azure 文件共享系统属性中的文件的时间点快照。这些文件的快照是使用[本机 Microsoft Azure 功能。](https://learn.microsoft.com/en-us/azure/storage/files/storage-snapshots-files)

---
您可以创建备份策略来自动执行数据保护任务并相应地安排它们。您可以根据需要为备份策略中包含的 Azure VM 和 Azure 文件共享手动拍摄云原生快照。此外，可以在 Azure SQL 数据库需要时执行手动备份。

![Pasted image 20250410144712.png](/img/user/99.picture/Pasted%20image%2020250410144712.png)

## 为 Azure 执行还原

Veeam Backup _for Microsoft Azure_ 支持用户执行各种还原场景，例如从虚拟机备份中还原整个 Azure 虚拟机和单个文件，甚至将 Azure SQL 数据库还原到特定时间点。这些灵活的还原选项可确保 Azure 工作负载的无缝数据恢复和业务连续性。

在各种灾难恢复场景中，Veeam Backup _for Microsoft Azure_ 允许您使用备份数据执行以下还原作：

---
### 还原 AZURE VM
如果发生灾难，您可以从云原生快照或映像级备份还原整个 Azure VM。Veeam Backup _for Microsoft Azure_ 支持您将一个或多个 Azure 虚拟机同时转换为原始位置或新位置。为了从云原生快照恢复 Azure 虚拟机，Veeam Backup _for Microsoft Azure_ 使用原生 Microsoft Azure 功能。
### 还原 AZURE SQL 数据库
如果发生灾难，您可以从映像级备份还原整个 Azure SQL 数据库。Veeam Backup _for Microsoft Azure_ 支持您将一个或多个数据库同时转换为原始位置或新位置。在一个还原会话中，您只能还原属于同一 SQL Server 的 Azure SQL 数据库。
### 还原 AZURE 文件共享
如果发生灾难，您可以从云原生快照恢复 Azure 文件共享的损坏或丢失的文件。Veeam Backup _for Microsoft Azure_ 支持您将文件和文件夹还原到原始文件共享或其他文件共享。

---

## 执行 Google Cloud 备份

Veeam Backup _for Google Cloud_ 利用原生 Google Cloud 功能备份虚拟机实例和 Cloud SQL 实例，无需在机箱内使用代理软件。每个备份会话都会为备份策略中包含的每个实例创建一个云原生快照，从而启用映像级备份以实现最佳数据保护。

点击浏览每个标签页，详细了解在 Google Cloud 中保护数据的不同方法：

---
### 创建 VM 实例的云原生快照
云原生快照包括附加到已处理 VM 实例的永久性磁盘的时间点快照。永久磁盘的快照（也称为 PD 快照）是使用[原生 Google Cloud 功能。（在新选项卡中打开）](https://cloud.google.com/compute/docs/disks/create-snapshots)默认情况下，云原生快照存储在最靠近原始实例所在区域的多区域位置。不过，可以在[备份策略设置。（在新选项卡中打开）](https://helpcenter.veeam.com/docs/vbgc/guide/backup_policy_target.html?ver=50)

### 创建 VM 实例的映像级备份

除了云原生快照之外，您还可以使用映像级备份来保护 VM 实例。映像级备份捕获已处理的 VM 实例（包括 OS 数据、应用程序数据等）在特定时间点的整个映像。备份将作为多个文件以本机 Veeam 格式保存到存储桶中。

### 创建 Cloud SQL 实例的云原生快照

云原生快照是已处理的 Cloud SQL 实例的时间点快照。Cloud SQL 实例的快照是使用[原生 Google Cloud 功能。（在新选项卡中打开）](https://cloud.google.com/sql/docs/mysql/backup-recovery/backups)默认情况下，云原生快照存储在最靠近原始实例所在区域的多区域位置。

Cloud SQL 实例的云原生快照在 Google Cloud 文档中称为备份。但是，由于 Cloud SQL 实例的所有“备份”会在您删除实例本身后自动删除，因此在本指南中，Cloud SQL 实例的“备份”称为快照。就 Veeam 逻辑而言，备份是存储在备份存储库中的独立文件，不受对原始实例执行的任何作的影响。

### 创建 Cloud SQL 实例的映像级备份

除了云原生快照之外，您还可以使用映像级备份来保护 Cloud SQL 实例。镜像级备份可以捕获处理后的 Cloud SQL 实例（包括实例配置、数据库、触发器、存储过程和用户）在特定时间点的整个镜像。备份将作为多个文件以本机 Veeam 格式保存到存储桶中。

Veeam Backup _for Google Cloud_ 支持您保护 MySQL 和 PostgreSQL 实例。不支持 SQL Server 实例。有关 Cloud SQL 实例类型的更多信息，请参阅[Google Cloud 文档。](https://cloud.google.com/sql/docs/features)

---
配置备份策略以自动执行数据保护任务。此外，对于备份策略中包含的 VM 实例和 Cloud SQL 实例，您可以在需要时手动启动云原生快照，确保全面的数据保护。

![Pasted image 20250410145032.png](/img/user/99.picture/Pasted%20image%2020250410145032.png)

## 为 Google Cloud 执行还原
使用 Veeam Backup _for Google Cloud_ 执行还原，您可以在发生数据丢失、意外删除或系统故障时快速恢复虚拟机实例和 Cloud SQL 实例。它通过为特定情况或整个备份提供灵活的还原选项，确保业务连续性并最大限度地减少停机时间。

在各种灾难恢复场景中，Veeam Backup _for Google Cloud_ 允许您使用备份数据执行以下作：

### VM 还原
将 VM 实例、磁盘和文件从云原生快照或映像级备份还原到原始位置或新位置。Veeam Backup _for Google Cloud_ 提供以下还原作：

- **实例还原** — 从还原点启动整个 VM 实例。
- **磁盘还原** — 还原附加到 VM 实例的永久性磁盘。
- **文件级恢复** — 恢复 VM 实例的单个文件和文件夹。

您可以将 VM 实例数据恢复到最新状态或任何可用的还原点。

### 云 SQL 还原

将 Cloud SQL 实例（从云原生快照或映像级备份）和 Cloud SQL 数据库（从映像级备份）还原到原始位置或新位置。Veeam Backup _for Google Cloud_ 提供以下还原作：

- **实例还原** - 从还原点启动整个 Cloud SQL 实例。
- **数据库还原** - 还原 Cloud SQL 实例的特定数据库。

您可以将 Cloud SQL 实例数据恢复到最新状态或任何可用的恢复点。


























