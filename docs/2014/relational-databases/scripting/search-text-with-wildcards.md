---
title: Eseguire ricerche di testo con caratteri jolly | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- vs.wildcards
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3419d8fb17d11e340eff50331908641929a78d1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114961"
---
# <a name="search-text-with-wildcards"></a>Testo di ricerca con caratteri jolly
  Caratteri o cifre nel campo **Trova** della finestra di dialogo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.  
  
#### <a name="to-search-using-wildcards"></a>Per eseguire la ricerca utilizzando caratteri jolly  
  
1.  Per consentire l'uso di caratteri jolly nel campo **Trova** durante operazioni Ricerca veloce, **Cerca nei file**, **Sostituzione veloce**o **Sostituisci nei file** , selezionare l'opzione **Utilizza** in **Opzioni di ricerca** e quindi scegliere **Caratteri jolly**.  
  
2.  Accanto al campo **Trova** viene reso disponibile il pulsante triangolare per **l'elenco dei riferimenti**. Fare clic su di esso per visualizzare l'elenco dei caratteri jolly disponibili. L'elemento scelto dall' **Elenco riferimenti**viene inserito nella stringa **Trova** .  
  
 Nella tabella seguente sono descritti i caratteri jolly disponibili nell' **Elenco riferimenti**.  
  
|Espressione|Sintassi|Description|  
|----------------|------------|-----------------|  
|Un solo carattere|?|Individua un qualsiasi singolo carattere.|  
|Una sola cifra|#|Individua una qualsiasi singola cifra. Ad esempio, 7# individua i numeri che comprendono 7 seguito da un altro numero. In questo caso potrebbe essere 71 ma non 17.|  
|Qualsiasi carattere esterno al set|[! ]|Individua qualsiasi carattere non specificato nel set.|  
|Zero o più caratteri|*|Individua uno o più caratteri. Ad esempio, nuovo* individua qualsiasi testo che comprende "nuovo", come nuovofile.txt.|  
|Qualsiasi carattere del set|[ ]|Individua qualsiasi carattere specificato nel set.|  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione](search-and-replace.md)   
 [Testo di ricerca con espressioni regolari](search-text-with-regular-expressions.md)  
  
  
