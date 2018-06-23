---
title: CDC Instance Deployment Script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 588c413c66560399941e75c4f8287b1b31da3067
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166210"
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
 [Preparare SQL Server per CDC](prepare-sql-server-for-cdc.md)  
  
  