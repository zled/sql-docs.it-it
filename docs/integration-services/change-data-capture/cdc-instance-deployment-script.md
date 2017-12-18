---
title: CDC Instance Deployment Script | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d70b2281c145aab485a8868ac7238a079d38584d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="cdc-instance-deployment-script"></a>CDC Instance Deployment Script
  Nella finestra di dialogo CDC Instance Deployment Script viene visualizzato lo script di distribuzione dell'istanza di CDC. Questo script può essere usato per ricreare il database CDC con tutti i relativi elementi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diversa.  
  
 Al completamento dello script di distribuzione, è necessario accertare le condizioni seguenti:  
  
-   Lo script di distribuzione presuppone che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione sia stata preparata per Oracle CDC, tramite Oracle CDC Service Configuration Console o lo **script di preparazione** creato dal programma.  
  
-   La parte dello script utilizzata per abilitare il database per CDC deve essere eseguita con il ruolo `sysadmin`.  
  
-   Nello script non viene memorizzata la password di log mining di Oracle. Questa operazione deve essere eseguita manualmente dopo l'esecuzione dello script e l'avvio del servizio CDC.  
  
 Selezionare le opzioni seguenti nella finestra di dialogo **CDC Instance Deployment Script** .  
  
 **Save As**  
 Tramite questa opzione è possibile salvare lo script in un file di testo nel percorso desiderato. È possibile copiare il file con lo script in qualsiasi altro server si desideri eseguirlo.  
  
 **Copia**  
 Tramite questa opzione è possibile copiare lo script negli Appunti. Sarà quindi possibile incollare lo script in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o in qualsiasi editor di testo per eseguirlo in un momento successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Preparare SQL Server per CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
