---
title: Riconciliazione di un diagramma di Database con un Database modificato (Visual Database Tools) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bcb7a22be32b5a4593105097485538443d0bff49
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171354"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a>Riconciliazione di un diagramma di database con un database modificato (Visual Database Tools)
  Il diagramma di database viene salvato per aggiornare il database in modo che corrisponda al diagramma. Tuttavia, se il database è stato aggiornato da altri utenti dopo l'apertura del diagramma, le modifiche apportate potranno avere effetto sul diagramma e viceversa.  
  
 Salvando il diagramma, le differenze tra il database e il diagramma verranno riconciliate sovrascrivendo le modifiche apportate da altri utenti, al fine di garantire la corrispondenza tra il database e il diagramma.  
  
### <a name="to-update-a-database-to-match-your-diagram"></a>Per aggiornare un database in modo che corrisponda al diagramma  
  
1.  Salvare il diagramma del database.  
  
     Se si salva il diagramma per la prima volta, specificare un nome per il diagramma nella finestra di dialogo **Salva nuovo diagramma di database** e scegliere **OK**.  
  
2.  Nella finestra di dialogo **Salva** è contenuto l'elenco delle tabelle su cui influirà il salvataggio del diagramma. Scegliere **Sì** per continuare.  
  
3.  Nella finestra di dialogo **Rilevate modifiche al database** vengono elencati gli oggetti modificati che verranno cambiati per assicurare la corrispondenza con il diagramma. Scegliere **Sì** per salvare il diagramma e accettare l'elenco di modifiche.  
  
    > [!NOTE]  
    >  Se il diagramma contiene tabelle e colonne eliminate dal database, salvando il diagramma verranno create nuovamente nel database solo le corrispondenti definizioni. Con questa operazione non verranno ripristinati i dati contenuti in tali oggetti prima dell'eliminazione.  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a>Per aggiornare il diagramma in modo che corrisponda a un database modificato  
  
1.  Chiudere il diagramma senza salvare le modifiche.  
  
2.  Fare clic con il pulsante destro del mouse sul diagramma in Esplora oggetti.  
  
3.  Scegliere **Aggiorna**dal menu di scelta rapida.  
  
4.  Aprire nuovamente il diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare diagrammi di database &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  