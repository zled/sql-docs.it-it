---
title: Gestione connessione della sottoscrizione di Azure | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
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
- sql13.dts.designer.afpsubscrconn.f1
- sql14.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 54dfa9242d714f759b90df4dfc2671b8f4e3d44e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="azure-subscription-connection-manager"></a>Gestione connessione della sottoscrizione di Azure
  **Gestione connessione della sottoscrizione di Azure** consente di connettere un pacchetto SSIS a una sottoscrizione di Azure usando i valori specificati per le proprietà: ID sottoscrizione di Azure e Certificato di gestione.  
  
 **Gestione connessione della sottoscrizione di Azure** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** mostrata sopra selezionare **Sottoscrizione di Azure**, quindi fare clic su **Aggiungi**.  Viene visualizzata la finestra di dialogo **Editor gestione connessione di Sottoscrizione di Azure** .  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  Immettere l'ID sottoscrizione di Azure, che identifica in modo univoco una sottoscrizione di Azure, per **ID sottoscrizione di Azure**.  Il valore si trova nel [portale di gestione di Azure](https://manage.windowsazure.com) nella pagina **Impostazioni** :  
  
    ![SSIS-AzureSettings-SubscriptionID](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  Scegliere il **percorso dell'archivio** e il **nome dell'archivio** del certificato di gestione dagli elenchi a discesa.  
  
4.  Immettere l' **identificazione personale del certificato di gestione** oppure fare clic su **Sfoglia** per scegliere un certificato dall'archivio selezionato. Il certificato deve essere caricato come certificato di gestione per la sottoscrizione. A tale scopo, fare clic su **Carica** nella pagina seguente del portale di Azure. Per altre informazioni, vedere questo [post MSDN](https://msdn.microsoft.com/library/azure/gg551722.aspx) .  
  
     ![SSIS-AzureSettings-ManagementCertificate](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Fare clic su **Test connessione** per testare la connessione.  
  
6.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
  
