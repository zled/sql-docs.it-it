---
title: Modificare i file archiviati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97d6ab997a1ece36919a49243e0f1dc3cc6f3593
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202411"
---
# <a name="edit-checked-in-files"></a>Modificare i file archiviati
  Prima di poter modificare i file inclusi nel controllo del codice sorgente in genere è necessario estrarli. È tuttavia possibile configurare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per poter modificare i file che non sono stati estratti. In questo caso le modifiche verranno conservate in memoria fino al salvataggio dei file. In seguito verrà chiesto di estrarre il file dal controllo del codice di origine.  
  
 Se si lavora in un team, non è consigliabile consentire modifiche dei file archiviati a meno che il provider del controllo del codice sorgente non supporti estrazioni sia della versione locale sia della versione del server. La maggior parte dei provider non supporta estrazioni della versione locale. In questo caso e se un file archiviato viene modificato, sarà necessario unire manualmente la versione in memoria e la versione del server prima di poter archiviare il file. In questo scenario, le unioni automatiche e assistite dal provider non sono supportate.  
  
### <a name="to-edit-checked-in-files"></a>Per modificare i file archiviati  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **le opzioni** finestra di dialogo espandere il **controllo del codice sorgente**l cartella e quindi fare clic su **ambiente**.  
  
3.  Fare clic su **consentire archiviato in modifica degli elementi**, quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle archiviazioni](../../2014/database-engine/manage-checkins.md)   
 [Gestione delle estrazioni](../../2014/database-engine/manage-checkouts.md)  
  
  
