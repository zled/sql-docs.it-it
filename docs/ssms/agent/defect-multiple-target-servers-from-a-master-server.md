---
title: "Escludere più server di destinazione da un server master | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d24f986e0274592b8984c9bf5d493261781b8f77
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Escludere più server di destinazione da un server master
In questo argomento viene illustrata la procedura per l'esclusione di più server di destinazione da una configurazione di amministrazione multiserver in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Eseguire questa procedura dal server master.  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Per escludere più server di destinazione da un server master  
  
1.  In **Esplora oggetti**espandere un server configurato come server master.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e fare clic su **Gestione server di destinazione**.  
  
3.  Fare clic su **Invia istruzioni**e quindi selezionare **Escludi** nell'elenco **Tipo istruzione**.  
  
4.  In **Destinatari**eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Tutti i server di destinazione** per escludere tutti i server di destinazione di questo server master. Questa opzione consente di disinstallare completamente l'attuale configurazione di amministrazione multiserver.  
  
    -   Fare clic su **Solo i server di destinazione seguenti**e quindi sulla casella **Seleziona** corrispondente per escludere solo alcuni server di destinazione di questo server master.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)  
[Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Defect a Target Server from a Master Server](../../ssms/agent/defect-a-target-server-from-a-master-server.md)  
  

