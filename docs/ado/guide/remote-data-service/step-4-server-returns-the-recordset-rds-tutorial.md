---
title: 'Passaggio 4: Server restituisce il Recordset (esercitazione su RDS) | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b607faa566bf584e1a18acb2ed6970f2e45d4404
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>Passaggio 4: Server restituisce il Recordset (esercitazione di servizi desktop remoto)
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Converte l'oggetto recuperato RDS **Recordset** oggetto a un form che può essere inviato al client (, vale a dire *effettua il marshalling* il **Recordset**). Il formato esatto della conversione e la modalità di invio varia a seconda se il server è in Internet o intranet, una rete locale o una libreria a collegamento dinamico. Tuttavia, questo dettaglio non è critico; tutto che è importante è che Servizi Desktop remoto invia la **Recordset** al client.  
  
 Sul lato client, un **Recordset** oggetto viene restituito e assegnato a una variabile locale.  
  
```  
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 5: DataControl è rendere utilizzabile (esercitazione di servizi desktop remoto)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
