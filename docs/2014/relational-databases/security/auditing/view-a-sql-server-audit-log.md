---
title: Visualizzazione di un log di controllo di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bb33f72c7b3f5f7af6d15004ce6377cbc8d6ffe8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219041"
---
# <a name="view-a-sql-server-audit-log"></a>Visualizzazione di un log di controllo di SQL Server
  Questo argomento descrive come visualizzare un log di controllo di SQL Server in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare un log di controllo di SQL Server mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'autorizzazione `CONTROL SERVER`.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Per visualizzare un log di controllo di SQL Server  
  
1.  In Esplora oggetti espandere la cartella **Sicurezza** .  
  
2.  Espandere la cartella **Controlli** .  
  
3.  Fare clic con il pulsante destro del mouse sul log di controllo da visualizzare e selezionare **Visualizza log di controllo**. Si aprirà la finestra di dialogo **Visualizzatore file di log -***nome_server*. Per altre informazioni, vedere [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).  
  
4.  Al termine, fare clic su **Chiudi**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di visualizzare il log di controllo usando il Visualizzatore file di log. Tuttavia, se si sta creando un sistema di monitoraggio automatizzato, è possibile leggere direttamente le informazioni nel file di controllo usando la funzione [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql). La lettura diretta del file restituisce i dati in un formato leggermente diverso (non elaborato). Vedere **sys.fn_get_audit_file** per altre informazioni  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md)   
 [Scrittura di eventi di controllo di SQL Server nel registro di sicurezza](write-sql-server-audit-events-to-the-security-log.md)  
  
  
