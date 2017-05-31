---
title: Accesso offline alla documentazione di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 08/22/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 257ed357-8cbb-43bd-b042-254be5fbb977
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1266b0249a96fbc4828b2afee9fb218682501e4d
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-documentation-offline-access"></a>Accesso offline alla documentazione di SQL Server

Visualizzare la documentazione tecnica di SQL Server 2016 offline.
  
## <a name="prerequisites"></a>Prerequisiti
Per visualizzare la documentazione tecnica di SQL Server 2016 offline è necessario HelpViewer 2.2 che può essere installato insieme a: 
- [Visual Studio 2015 (qualsiasi edizione che include Community)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) o
- [Versione di anteprima di SQL Server Management Studio (SSMS) aprile 2016 (13.0.12500.29) o versione successiva](https://msdn.microsoft.com/library/mt238290.aspx)

Installare uno di questi prodotti prima di procedere con i passaggi seguenti.
  
## <a name="install-sql-server-offline-technical-documentation"></a>Installare la documentazione tecnica offline di SQL Server 

1. Installare una versione qualsiasi di Visual Studio 2015 o la versione di anteprima di SSMS aprile 2016 o versione successiva. 
2. Avviare SSMS o Visual Studio.
3. Dal menu **Guida** sulla barra di spostamento superiore selezionare  **Aggiungi e rimuovi contenuto della Guida**. 

#### <a name="this-action-launches-the-helpviewer"></a>Questa azione avvia il visualizzatore della Guida.

4. Nel visualizzatore della Guida scegliere l'origine dell'installazione predefinita, vale a dire **Online** 
5. Fare clic su **Aggiungi** accanto alla documentazione che si vuole installare.
6. Fare clic sul pulsante **Aggiorna** in basso a destra dello schermo per scaricare e installare la documentazione selezionata.
![caricare contenuto offline](../sql-server/media/load-offline-content.png) 

 >** IMPORTANTE!!** Dopo aver fatto clic su Aggiorna, il visualizzatore della Guida potrebbe bloccarsi o interrompersi. La documentazione selezionata è stata comunque scaricata e installata. **Per risolvere il problema**, terminare il visualizzatore della Guida in Gestione attività e riavviarlo seguendo i 3 passaggi descritti in precedenza. La prima volta che il visualizzatore della Guida si blocca o si interrompe, seguire anche [questa procedura](https://msdn.microsoft.com/library/mt654096.aspx) . È necessario eseguire questi passaggi una sola volta, ma sarà probabilmente necessario terminare il visualizzatore della Guida in Gestione attività ogni volta che si aggiorna il contenuto.  
6. Riavviare il visualizzatore della Guida selezionando di nuovo Guida/Aggiungi o rimuovi contenuto. La documentazione è ora disponibile offline.



   ![Disponibile offline](../sql-server/media/offline-ready-to-use.png)




