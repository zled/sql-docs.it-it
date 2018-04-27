---
title: Gestione connessione Azure Resource Manager | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
caps.latest.revision: 3
author: Lingxi-Li
ms.author: lingxl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e4a9863f8bef6b32985720e402c7e8bb2fadbd5
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="azure-resource-manager-connection-manager"></a>Gestione connessione Azure Resource Manager
La **gestione connessione Azure Resource Manager** consente a un pacchetto SSIS di gestire le risorse di Azure mediante un'[entità servizio](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Gestione connessione di Azure Resource Manager** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Per creare e configurare una **gestione connessione Azure Resource Manager**, eseguire la procedura seguente:

1. Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureResourceManager** e fare clic su **Aggiungi**.
2. Nella finestra di dialogo **Editor gestione connessione Azure Resource Manager** compilare i campi **ID applicazione**, **Chiave applicazione** e **ID tenant** per l'entità servizio. Per informazioni dettagliate su queste proprietà, vedere [questo](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) articolo.
3. Scegliere **OK** per chiudere la finestra di dialogo.
4. È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .
