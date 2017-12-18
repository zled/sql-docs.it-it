---
title: Gestione connessione dell'archiviazione di Azure | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc320994dba6dc2b6f2207d5a6aad9e9c193d515
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="azure-storage-connection-manager"></a>Gestione connessione dell'archiviazione di Azure
  Il componente **Gestione connessione dell'archiviazione di Azure** consente di connettere un pacchetto SSIS a un account di archiviazione di Azure usando i valori specificati per le proprietà: Nome dell'account di archiviazione e Chiave dell'account.  
   
 **Gestione connessione dell'archiviazione di Azure** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **Sottoscrizione di Azure**, quindi fare clic su **Aggiungi**.  
  
2.  Nella finestra di dialogo Editor gestione connessione di archiviazione di Azure, scegliere **Usa account Azure** per connettersi a un servizio di archiviazione di Azure con Internet o scegliere **Usa account per sviluppatore locale** per connettersi al servizio locale ospitato dall'emulatore di archiviazione di Azure.  
  
3.  Se si seleziona l'opzione **Usa account Azure** , eseguire queste operazioni:  
  
    1.  Specificare i valori per i campi **Nome dell'account di archiviazione** e **Chiave dell'account** . Questi valori vengono archiviati come dati sensibili nel pacchetto SSIS.  
  
    2.  Selezionare **Usa HTTPS** per usare HTTPS anziché HTTP per connettersi al servizio di archiviazione di Azure.  
  
4.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
5.  È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  
