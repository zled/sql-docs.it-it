---
title: Modificare i file archiviati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 065f8d2d32d8ad16fe955ba8e36c7e65926bec95
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808287"
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
  
  
