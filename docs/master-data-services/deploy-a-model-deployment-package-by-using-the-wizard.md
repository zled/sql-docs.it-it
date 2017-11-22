---
title: Distribuire un pacchetto di distribuzione di modelli tramite la procedura guidata | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deployment packages [Master Data Services], deploying
- models [Master Data Services], deploying a package
ms.assetid: 4f65dc60-0ff8-46e6-9988-5bc5b9603ad0
caps.latest.revision: "16"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ceecdbdafa9675ffd78178fee26fa3069fca669
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-a-model-deployment-package-by-using-the-wizard"></a>Distribuire un pacchetto di distribuzione di modelli tramite la procedura guidata
  Utilizzare Distribuzione guidata modello [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per distribuire pacchetti contenenti solo oggetti modello. Se è necessario distribuire un pacchetto con i dati, vedere [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  I pacchetti possono essere distribuiti solo nella versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzata per crearli. Pertanto non è possibile distribuire pacchetti creati in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Amministrazione sistema** nell'ambiente [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] di destinazione.  
  
-   È necessario che sia già disponibile un pacchetto di distribuzione di modelli. Per altre informazioni, vedere [Creare un pacchetto di distribuzione di modelli tramite la procedura guidata](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
  
-   È necessario essere un amministratore nell'ambiente in cui viene distribuito il modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-deploy-a-model-deployment-package-of-model-objects-only"></a>Per distribuire un pacchetto di distribuzione di modelli di soli oggetti modello  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella barra dei menu della pagina **Vista modelli** scegliere **Sistema** , quindi fare clic su **Distribuzione**.  
  
3.  Su **Distribuzione guidata modello**, fare clic su **Distribuisci**.  
  
4.  Fare clic su **Sfoglia**.  
  
5.  Individuare il pacchetto di distribuzione (file con estensione pkg) e fare clic su **Apri**.  
  
6.  Scegliere **Avanti**.  
  
7.  Dopo aver caricato il pacchetto, fare clic su **Avanti**.  
  
8.  Se il modello è già presente, è possibile aggiornarlo selezionando **Aggiorna il modello esistente**. Per creare un nuovo modello, selezionare **Crea un nuovo modello** e, dopo aver fatto clic su **Avanti** , è possibile digitare un nome per il nuovo modello.  
  
9. Scegliere **Fine** per uscire dalla procedura guidata.  
  
 **Note:**  
  
-   Se la vista sottoscrizioni nel pacchetto ha lo stesso nome di una vista sottoscrizioni in un modello esistente, viene visualizzato l'avviso: **la vista delle sottoscrizioni del deployer è stata rinominata**. Inoltre, la vista viene creata come *modelname.subscriptionviewname*. Se questo nome è già in uso, la vista della sottoscrizione non viene creata.  
  
-   Il processo di distribuzione si svolge in quattro passaggi:  
  
    1.  Creazione degli oggetti modello.  
  
    2.  Creazione delle viste sottoscrizioni.  
  
    3.  Creazione delle regole business.  
  
-   Quando si crea un nuovo modello o se ne clona uno esistente, se si verifica un errore durante un qualsiasi passaggio del processo, il modello viene eliminato.  
  
     Quando si aggiorna un modello, se si verifica un errore durante uno dei primi tre passaggi, l'operazione viene interrotta; tuttavia il rollback delle modifiche già effettuate non viene eseguito.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Gli attributi file e le autorizzazioni di utenti e gruppi non sono inclusi nei pacchetti di distribuzione dei modelli. Dopo avere distribuito un modello, è necessario aggiornare questi elementi manualmente. Per altre informazioni, vedere:  
  
-   [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di modelli &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md)  
  
  
