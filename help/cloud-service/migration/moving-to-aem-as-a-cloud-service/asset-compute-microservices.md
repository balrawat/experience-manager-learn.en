---
title: AEM Assets Microservices and moving to AEM as a Cloud Service
description: Learn how AEM Assets as a Cloud Service's asset compute microservices allow you to automatically and efficiently generate any rendition for your assets, replacing this role of traditional AEM Workflow.
version: Cloud Service
feature: Asset Compute Microservices
topic: Migration, Upgrade
role: Developer
level: Experienced
kt: 8635
thumbnail: 336990.jpeg
exl-id: 327e8663-086b-4b31-b159-a0cf30480b45
---
# AEM Assets Microservices - Moving to AEM as a Cloud Service

Learn how AEM Assets as a Cloud Service's asset compute microservices allow you to automatically and efficiently generate any rendition for your assets, replacing this role of traditional AEM Workflow.

>[!VIDEO](https://video.tv.adobe.com/v/336990/?quality=12&learn=on)

## Workflow Migration Tool

![Asset Workflow Migration Tool](./assets/asset-workflow-migration.png)

As part of refactoring your code base, use the [Asset Workflow Migration tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/asset-workflow-migration-tool.html) to migrate existing workflows to use the Asset Compute microservices in AEM as a Cloud Service.

### Key Activities

* Use the [Adobe I/O Workflow Migrator](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#command-aio-aem-migrationworkflow-migrator) tool to migrate asset processing workflows to use the Asset Compute microservices.
* Set up a [local development environment](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) and deploy the updated workflows. Manual adjustment may be needed for complex workflows. 
* Continue to iterate in a local development environment using the AEM SDK until the updated workflow matches feature parity.
* Deploy the updated code base to an AEM as a Cloud Service development environment and continue to validate.
