---
title: Use Azure Migrate to move VMware VMs to Azure Stack HCI (preview)
description: Learn about how to use Azure Migrate to migrate VMware VMs to your Azure Stack HCI cluster (preview).
author: alkohli
ms.topic: overview
ms.date: 06/26/2024
ms.author: alkohli
ms.reviewer: alkohli
ms.subservice: azure-stack-hci
---

# Overview of Azure Migrate based VMware migration for Azure Stack HCI (preview)

[!INCLUDE [applies-to](../../includes/hci-applies-to-23h2.md)]

This article provides an overview of how to migrate VMware virtual machines (VMs) to your Azure Stack HCI cluster using Azure Migrate.

Azure Migrate is a central hub for tools to discover, assess, and migrate on-premises servers, apps, and data to the Microsoft Azure cloud. Azure Stack HCI is a hyperconverged infrastructure (HCI) cluster solution that hosts virtualized Windows and Linux workloads in a hybrid environment. You can use the Azure Migrate platform to move on-premises VMware VMs to your Azure Stack HCI cluster.

For more information on the Azure Migrate platform, see [About Azure Migrate](/azure/migrate/migrate-services-overview).

[!INCLUDE [important](../../includes/hci-preview.md)]

## Benefits

Here are the benefits of using Azure Migrate to migrate your on-premises VMware VMs to Azure Stack HCI. This solution:

- Requires no preparation for your VMware VMs including installation of agents prior to migration.
- Provides the control plane via the Azure portal. You can use the portal to start, run, and track your migration to Azure Stack HCI.
- Keeps the data flow local, from on-premises VMware source servers to Azure Stack HCI.
- Results in a minimal downtime for the VMs running on your on-premises VMware servers.

## Migration components

With Azure Migrate, you can choose to migrate your data from your on-premises VMware environment to Azure or to your on-premises Azure Stack HCI cluster.

The following diagram shows the migration process to your on-premises Azure Stack HCI cluster:

:::image type="content" source="./media/migration-azure-migrate-vmware-overview/azure-migrate-vmware-workflow-1.png" alt-text="Diagram that shows a high-level workflow for VMware migration using Azure Migrate.":::

The migration process requires the following components:

- An Azure Migrate project. Both the source and target appliances need to be registered with this project.
- Azure Migrate appliance running on your on-premises VMware servers. The VMware source servers host the VMs that you want to migrate.
- Target appliance running on your on-premises Azure Stack HCI cluster. The target cluster hosts the VMs that you migrated from your VMware source environment.

> [!NOTE]
> The Azure Migrate project is used to discover the VMware VMs and replicate them to the target Azure Stack HCI cluster. The VMware VM disks and data that are being migrated are not stored in the associated Azure Storage account. Only the metadata is stored in Storage account.

## Migration phases

Here are the key phases of the migration process:


|#  |Phase  |Description  |
|---------|---------|---------|
|1.     |**Prepare**        |Prepare to migrate by completing the migration prerequisites. Deploy, configure, and register your Azure Stack HCI cluster. This cluster is the migration target. Create an Azure Migrate project and an Azure Storage account in Azure.<br><br> For more information, see [Review prerequisites for Azure Migrate](migrate-vmware-prerequisites.md).         |
|2.     |**Discover**       |Create and configure an Azure Migrate source appliance on VMware. Use this appliance to discover your on-premises source VMware servers. <br><br> For more information, see [Discover VMware VMs](migrate-vmware-replicate.md).          |
|3.     |**Replicate**      |Create and configure the target appliance on your Azure Stack HCI. Select and replicate the VMs that were discovered in the previous step. <br><br> For more information, see [Replicate VMware VMs](migrate-vmware-replicate.md).         |
|4.     |**Migrate, verify**|Once the replication is complete, select and migrate VMware VMs to your Azure Stack HCI. After the migration is complete, verify that the VMs have booted successfully and the data has migrated properly. You can now pause the replication and decommission the source VMware VMs. <br><br> For more information, see [Migrate and verify VMware VMs](./migrate-vmware-migrate.md).         |


## Next steps

To prepare for VMware migration, see the following articles:

- [Review the requirements](migrate-vmware-requirements.md) for VMware VM migration to Azure Stack HCI.
- [Complete the prerequisites](migrate-vmware-prerequisites.md) for VMware VM migration to Azure Stack HCI.
