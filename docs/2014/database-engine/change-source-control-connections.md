---
title: Modificare le connessioni di controllo di origine | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3d158c2a0981b6174bcb83948b10bacd1a97d1f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188948"
---
# <a name="change-source-control-connections"></a>Modifica delle connessioni del controllo del codice sorgente
  La prima volta che viene aggiunta o aperta una soluzione dal controllo del codice sorgente, il provider del controllo crea un'associazione tra la cartella radice della directory della soluzione locale e la cartella corrispondente del server.  
  
 La cartella radice, chiamata anche radice unificata, risiede nel client. Sotto di essa si trovano tutti i file a cui fa riferimento una soluzione o un progetto. Per trovare l'ultima versione di una soluzione, la cronologia e le informazioni sullo stato, individuare la cartella che si trova nel server del controllo del codice sorgente. In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, le cartelle del server sono denominate progetti.  
  
 In molti casi è necessario disassociare o disconnettere una soluzione dalla sua cartella del server. Se, ad esempio, il computer in cui si trova il provider del controllo del codice sorgente non è disponibile, è possibile connettersi a un computer di backup, riassociare la soluzione a una cartella del server sottoposta a backup e riprendere a lavorare normalmente. Se un progetto di controllo del codice sorgente è inoltre duplicato, potrebbe essere necessario associare la soluzione alla cartella del server in cui si trova la nuova versione del progetto.  
  
 Utilizzare l'interfaccia utente del provider del controllo del codice sorgente per cambiare la cartella del server alla quale è associata una soluzione. È possibile aprire l'interfaccia utente del controllo del codice sorgente dall'ambiente [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>Per aprire l'interfaccia utente del controllo del codice sorgente dall'ambiente Studio  
  
1.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **avviare Microsoft Visual SourceSafe**.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di controlli di origine](../../2014/database-engine/source-control-basics.md)   
 [Impostare le opzioni di controllo di origine](../../2014/database-engine/set-source-control-options.md)   
 [Esclusione di file dal controllo del codice sorgente](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
