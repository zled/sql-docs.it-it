---
title: "Passaggio 5: DataControl è rendere utilizzabile (esercitazione su RDS) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f59e167dfad5ddd4b99d784b34e37556a076a2f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Passaggio 5: DataControl è rendere utilizzabile (esercitazione di servizi desktop remoto)
L'oggetto restituito **Recordset** l'oggetto è disponibile per l'utilizzo. È possibile esaminare, esplorare o modificarlo come qualsiasi altra **Recordset**. Cosa si può fare con il **Recordset** dipende dall'ambiente. Visual Basic e Visual C++ sono controlli visivi che è possono utilizzare un **Recordset** direttamente o indirettamente con l'aiuto di un controllo di dati di attivazione.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Ad esempio, se si visualizzano una pagina Web in Microsoft Internet Explorer, potrebbe essere desidera visualizzare il **Recordset** dati in un controllo visivo dell'oggetto. Controlli visivi in una pagina Web non possono accedere un **Recordset** direttamente l'oggetto. Tuttavia, possono accedere le **Recordset** mediante il [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). Il **RDS. DataControl** diventa utilizzabile da un oggetto visivo controllare quando il relativo [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) è impostata sul **Recordset** oggetto.  
  
 L'oggetto controllo visual deve avere il **DATASRC** parametro impostato sul **RDS. DataControl**e il relativo **DATAFLD** proprietà impostata su un **Recordset** campo (colonna) dell'oggetto.  
  
 In questa esercitazione, impostare il **SourceRecordset** proprietà:  
  
```  
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 6: Le modifiche vengono inviate al Server (esercitazione di servizi desktop remoto)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

