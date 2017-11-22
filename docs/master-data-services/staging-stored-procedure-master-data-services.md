---
title: Stored procedure di gestione temporanea (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 04/01/2016
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
caps.latest.revision: "15"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ca00f345569d60b7a7dcd78ce63fca380835feb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="staging-stored-procedure-master-data-services"></a>Stored procedure di gestione temporanea (Master Data Services)
  Quando si inizia il processo di gestione temporanea da [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], viene usata una delle tre stored procedure seguenti.  
  
-   stg.udp_\<name>_Leaf  
  
-   stg.udp_\<name>_Consolidated  
  
-   stg.udp_\<name>_Relationship  
  
 Dove name è il nome della tabella di staging specificata alla creazione dell'entità.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Parametri delle stored procedure del processo di gestione temporanea  
 Nella tabella seguente vengono elencati i parametri di queste stored procedure.  
  
|Parametro|Description|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Obbligatorio|Il nome della versione. Può supportare o non supportare la distinzione tra maiuscole e minuscole, a seconda dell'impostazione delle regole di confronto di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Obbligatorio|Determina se le transazioni sono registrate durante il processo di gestione temporanea. I valori possibili sono:<br /><br /> **0**: le transazioni non vengono registrate.<br /><br /> **1**: le transazioni vengono registrate.<br /><br /> <br /><br /> Per altre informazioni sulle transazioni, vedere [Transazioni &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Richiesto, salvo che dal servizio Web|Il valore **BatchTag** come specificato nella tabella di staging.|  
|**Batch_ID**<br /><br /> Richiesto solo dal servizio Web|Il valore **Batch_ID** come specificato nella tabella di staging.|  
|**Nome utente**|Parametro facoltativo|  
|**ID utente**|Parametro facoltativo|  
  
### <a name="staging-process-stored-procedure-example"></a>Esempio di stored procedure del processo di gestione temporanea  
 Nell'esempio seguente viene illustrata la modalità di inizio del processo di gestione temporanea mediante una stored procedure di gestione temporanea.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
      @UserName=N’domain\user’  
  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di convalida &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [Visualizzare gli errori che si verificano durante il processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)  
  
  
