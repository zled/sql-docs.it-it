---
title: Rimozione di SSMA per i componenti di DB2 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef9a64e458d03a0832ef3d5cd656747360e4a2db
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Rimozione di SSMA per i componenti di DB2 (DB2ToSQL)
Al termine di migrazione di database da DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile disinstallare i componenti SSMA. È possibile disinstallare i componenti client in qualsiasi momento. Tuttavia, non è opportuno disinstallare il pacchetto di estensione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , a meno che i database migrati non usare più funzioni nel **ssma_DB2** dello schema del **sysdb** database.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Disinstallazione di SSMA per Client DB2  
È possibile disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi**.  
  
**Per disinstallare SSMA**  
  
1.  Nel Pannello di controllo aprire **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant per DB2**, quindi fare clic su **rimuovere**.  
  
3.  Per confermare che si desidera disinstallare SSMA, fare clic su **Sì**.  
  
## <a name="uninstalling-the-extension-pack"></a>Disinstallare il pacchetto di estensione  
Se si è certi dei database migrati non utilizzano gli oggetti di **sysdb.ssma_DB2** dello schema, è possibile rimuovere il pacchetto di estensione eliminandolo dallo schema: è disponibile alcuna disinstallazione di Windows  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per DB2ToSQL Client DB2 &#40; &#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Installazione dei componenti SSMA DB2ToSQL SQL Server &#40; &#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
