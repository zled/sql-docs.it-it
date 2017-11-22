---
title: Invertire una transazione (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
caps.latest.revision: "8"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3b070c2452fa453a1017080abf4876f817cf3fd4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="reverse-a-transaction-master-data-services"></a>Invertire una transazione (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]gli amministratori possono invertire una transazione quando è necessario annullare un'azione. Esempi di transazioni sono modifiche al valore dell'attributo, spostamenti di gerarchie o eliminazioni di membri. Questo argomento si applica solo a transazioni di entità con il tipo di log delle transazioni "Attributo". Passare alla pagina di visualizzazione delle entità per visualizzare la cronologia delle transazioni delle entità con il tipo di log delle transazioni "Membro".  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale **Gestione versioni** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-reverse-a-transaction"></a>Per invertire una transazione  
  
1.  Scegliere [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Gestione versioni **dalla pagina iniziale di**.  
  
2.  Sulla barra dei menu fare clic su **Transazioni**.  
  
3.  Nella pagina **Transazioni** selezionare un modello dall'elenco **Modello** .  
  
4.  Selezionare una versione dall'elenco **Versione** .  
  
5.  Fare clic sulla riga nella griglia per la transazione che si desidera invertire.  
  
6.  Fare clic su **Inverti transazione selezionata**.  
  
7.  Nella finestra di dialogo di conferma fare clic su **OK**. Un'altra transazione viene aggiunta alla griglia per registrare la transazione invertita.  
  
## <a name="see-also"></a>Vedere anche  
 [Transazioni &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)   
 [Riattivare un membro o una raccolta &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
 [Eseguire il rollback della cronologia delle revisioni del membro](../master-data-services/rollback-member-revision-history-master-data-services.md)
  
  
