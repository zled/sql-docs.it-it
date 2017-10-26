---
title: Gestione connessione di Azure Resource Manager | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd1dbf668bf3ac24d9d6598b0ff9e2256d897c42
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="azure-resource-manager-connection-manager"></a>Gestione connessione di Azure Resource Manager
Il **Connection Manager di Azure Resource Manager** consente a un pacchetto SSIS gestire le risorse di Azure utilizzando un [dell'entità servizio](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal).

Il **Connection Manager di Azure Resource Manager** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Per creare e configurare un **Connection Manager di Azure Resource Manager**, attenersi alla procedura seguente:

1. Nel **Aggiungi gestione connessione SSIS** nella finestra di dialogo **AzureResourceManager**, fare clic su **Aggiungi**.
2. Nel **Azure Resource Manager Connection Manager Editor** finestra di dialogo, specificare il **ID applicazione**, **chiave applicazione**, e **ID Tenant** per l'entità servizio. Per informazioni dettagliate su queste proprietà, fare riferimento a [questo](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) articolo.
3. Scegliere **OK** per chiudere la finestra di dialogo.
4. È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .

