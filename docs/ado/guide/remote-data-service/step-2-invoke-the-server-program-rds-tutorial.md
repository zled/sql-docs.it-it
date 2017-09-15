---
title: 'Passaggio 2: Richiamare il programma di Server (esercitazione su RDS) | Documenti Microsoft'
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS tutorial [ADO], invoking server program
ms.assetid: 5e74c2da-65ee-4de4-8b41-6eac45c3632e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd6ffeef7f178c7823b25fcd9a6b8e1a73c6756b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-2-invoke-the-server-program-rds-tutorial"></a>Passaggio 2: Richiamare il programma di Server (esercitazione di servizi desktop remoto)
Quando si richiama un metodo nel client *proxy*, il programma effettivo sul server esegue il metodo. In questo passaggio, si sarà esegue una query sul server.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 **Parte** se non è stato utilizzato [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) in questa esercitazione, il modo più semplice per eseguire questo passaggio, è possibile utilizzare il [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto. Il **RDS. DataControl** combina il passaggio precedente della creazione di un proxy, con questo passaggio, invia la query.  
  
 Impostare il **RDS. DataControl** oggetto [Server](../../../ado/reference/rds-api/server-property-rds.md) proprietà per identificare in cui l'applicazione server deve essere creata un'istanza; il [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà per specificare la stringa di connessione per accedere all'origine dati; e il [SQL](../../../ado/reference/rds-api/sql-property.md) proprietà per specificare il testo del comando di query. Eseguire quindi il [aggiornare](../../../ado/reference/rds-api/refresh-method-rds.md) per il programma del server per la connessione all'origine dati, recuperare le righe specificate dalla query e restituire un **Recordset** oggetto al client.  
  
 In questa esercitazione non utilizza il **RDS. DataControl**, ma è come se fosse presente:  
  
```  
Sub RDSTutorial2A()  
   Dim DC as New RDS.DataControl  
   DC.Server = "http://yourServer"  
   DC.Connect = "DSN=Pubs"  
   DC.SQL = "SELECT * FROM Authors"  
   DC.Refresh  
...  
```  
  
 Né esercitazione richiama Servizi Desktop remoto con gli oggetti ADO, ma è come se fosse presente:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "SELECT * FROM Authors","Provider=MS Remote;Data Source=Pubs;" & _  
        "Remote Server=http://yourServer;Remote Provider=SQLOLEDB;"  
```  
  
 **Parte B** il metodo generale di eseguire questo passaggio consiste nel richiamare il **RDSServer** oggetto [Query](../../../ado/reference/rds-api/query-method-rds.md) metodo. Tale metodo accetta una stringa di connessione, viene utilizzato per connettersi a un'origine dati, e un testo di comando, viene utilizzato per specificare le righe da restituire dall'origine dati.  
  
 Questa esercitazione viene utilizzato il **DataFactory** oggetto **Query** metodo:  
  
```  
Sub RDSTutorial2B()  
   Dim DS as New RDS.DataSpace  
   Dim DF  
   Dim RS as ADODB.Recordset  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Passaggio 3: Server Ottiene un Recordset (esercitazione di servizi desktop remoto)](../../../ado/guide/remote-data-service/step-3-server-obtains-a-recordset-rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   

