---
title: Disabilitare Resource Governor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d0f050783582fe62c85da06700dc168f7753785f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299951"
---
# <a name="disable-resource-governor"></a>Disabilitare Resource Governor
  È possibile disabilitare Resource Governor tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per disabilitare Resource Governor usando:**  [Esplora oggetti](#RGOffObjEx), [Proprietà di Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 La disabilitazione di Resource Governor comporta i risultati riportati di seguito:  
  
-   La funzione di classificazione non viene eseguita.  
  
-   Tutte le nuove connessioni vengono classificate automaticamente nel gruppo di carico di lavoro predefinito.  
  
-   Le richieste avviate dal sistema vengono classificate nel gruppo di carico di lavoro interno.  
  
-   Tutte le impostazioni del gruppo del carico di lavoro e del pool di risorse esistenti vengono reimpostate ai valori predefiniti. In questo caso non viene generato alcun evento quando vengono raggiunti i limiti.  
  
-   Il normale monitoraggio del sistema non viene modificato.  
  
-   Le modifiche alla configurazione non hanno effetto fino all'abilitazione di Resource Governor.  
  
-   Al riavvio di SQL Server, non verrà caricata la configurazione di Resource Governor, ma solo i gruppi di carico di lavoro e i pool di risorse interni e predefiniti.  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Non è possibile utilizzare l'istruzione `ALTER RESOURCE GOVERNOR` per disabilitare Resource Governor quando in una transazione utente.  
  
###  <a name="Permissions"></a> Permissions  
 Per disabilitare Resource Governor è necessaria l'autorizzazione CONTROL SERVER.  
  
##  <a name="RGOffObjEx"></a> Disabilitare Resource Governor utilizzando Esplora oggetti  
 **Per disabilitare Resource Governor utilizzando Esplora oggetti**  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Resource Governor**.  
  
2.  Fare clic con il pulsante destro del mouse su **Resource Governor**, quindi su **Disabilita**.  
  
##  <a name="RGOffProp"></a> Disabilitare Resource Governor utilizzando Proprietà di Resource Governor  
 **Per disabilitare Resource Governor utilizzando la pagina Proprietà di Resource Governor**  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Resource Governor**.  
  
2.  Fare clic con il pulsante destro del mouse su **Resource Governor** , quindi fare clic su **Proprietà**. In questo modo viene aperta la pagina **Proprietà di Resource Governor** .  
  
3.  Fare clic sulla casella di controllo **Abilita Resource Governor** , assicurarsi che la casella non sia selezionata, quindi fare clic su **OK**.  
  
##  <a name="RGOffTSQL"></a> Disabilitare Resource Governor utilizzando Transact-SQL  
 **Per disabilitare Resource Governor utilizzando Transact-SQL**  
  
1.  Eseguire l'istruzione **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Esempio (Transact-SQL)  
 Nell'esempio seguente viene abilitato Resource Governor.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](resource-governor.md)   
 [Abilitare Resource Governor](enable-resource-governor.md)   
 [Pool di risorse di Resource Governor](resource-governor-resource-pool.md)   
 [Gruppo di carico di lavoro di Resource Governor](resource-governor-workload-group.md)   
 [Funzione di classificazione di Resource Governor](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
