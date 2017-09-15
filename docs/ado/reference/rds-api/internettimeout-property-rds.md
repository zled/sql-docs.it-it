---
title: "Proprietà InternetTimeout (RDS) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2320ba200cf8343a32e2a0d00589a80014517260
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="internettimeout-property-rds"></a>Proprietà InternetTimeout (RDS)
Indica il numero di millisecondi di attesa prima del timeout di una richiesta.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che rappresenta il numero di millisecondi prima che una richiesta di timeout.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà si applica solo alle richieste inviate con il protocollo HTTP o HTTPS.  
  
 Le richieste in un ambiente a tre livelli possono richiedere alcuni minuti per l'esecuzione. Utilizzare questa proprietà per specificare un tempo aggiuntivo per le richieste a esecuzione prolungata.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Oggetto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà InternetTimeout (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [Esempio di proprietà InternetTimeout (VC + +)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 


