---
title: MoveFirst, MoveLast, MoveNext e MovePrevious metodi (RDS) | Documenti Microsoft
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
- MoveLast method [RDS]
- MovePrevious method [RDS]
- MoveFirst method [RDS]
- MoveNext method [RDS]
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae28d49a51d2bd4dbf516a7cc96bbf20381ccdfe
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-rds"></a>MoveFirst, MoveLast, MoveNext e MovePrevious metodi (RDS)
Sposta il primo, ultimo, successivo o precedente record in un oggetto specificato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare il **spostare** metodi con il **RDS. DataControl** oggetto per spostarsi tra i record dei dati nei controlli con associazione a dati in una pagina Web. Ad esempio, si supponga di visualizzare un **Recordset** in una griglia utilizzando l'associazione a un **RDS. DataControl** oggetto. È quindi possibile includere i pulsanti First, Last, Avanti e indietro che consente agli utenti per spostarsi al primo, ultimo, successivo, o record precedente visualizzato **Recordset**. Tale scopo, chiamare il **MoveFirst**, **MoveLast**, **MoveNext**, e **MovePrevious** metodi il **RDS. DataControl** oggetto nelle procedure onClick per i pulsanti First, Last, Avanti e indietro, rispettivamente. Il [esempio Address Book](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md) viene illustrato come eseguire questa operazione.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Move (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext e MovePrevious metodi (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Metodo MoveRecord (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)



