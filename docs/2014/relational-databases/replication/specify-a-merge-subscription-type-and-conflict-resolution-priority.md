---
title: Specificare una sottoscrizione di tipo Merge e la priorità per la risoluzione dei conflitti (SQL Server Management Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 33
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: de41a4bf6075a816b751574b5505e324d07aa89f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069588"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>Impostazione di una sottoscrizione di tipo merge e della priorità per la risoluzione dei conflitti (SQL Server Management Studio)
  Specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti nella pagina **Tipo di sottoscrizione** della Creazione guidata nuova sottoscrizione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [Create a Pull Subscription](create-a-pull-subscription.md) e [Create a Push Subscription](create-a-push-subscription.md).  
  
 Dopo la creazione di una sottoscrizione non è più possibile modificarne il tipo. È tuttavia possibile modificare la priorità per il tipo di sottoscrizione del server nella finestra di dialogo **Proprietà sottoscrizione - \<ServerPubblicazione>: \<DatabasePubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) e [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Per specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti  
  
1.  Nella pagina **Tipo di sottoscrizione** della Creazione guidata sottoscrizione selezionare **Client** o **Server** per l'opzione **Tipo di sottoscrizione** .  
  
2.  Se si seleziona un tipo di sottoscrizione **Server**, immettere anche un valore compreso tra 0,00 e 99,99 per l'opzione **Priorità per la risoluzione dei conflitti** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Per modificare la priorità per la risoluzione dei conflitti  
  
1.  Nella finestra di dialogo **Proprietà sottoscrizione - \<ServerPubblicazione>: \<DatabasePubblicazione>** visualizzata nel server di pubblicazione immettere un valore compreso tra 0,00 e 99,99 per l'opzione **Priorità**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Sottoscrizione delle pubblicazioni](subscribe-to-publications.md)  
  
  