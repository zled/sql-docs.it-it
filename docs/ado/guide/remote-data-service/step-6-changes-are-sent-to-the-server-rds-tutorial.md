---
title: 'Passaggio 6: Le modifiche vengono inviate al Server (esercitazione su RDS) | Documenti Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], changes sent to server
ms.assetid: b1e927d6-7d50-4978-9eef-045043cdce7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0537d8d05553b4e50861bda664d2cdc53489cb82
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="step-6-changes-are-sent-to-the-server-rds-tutorial"></a>Passaggio 6: Le modifiche vengono inviate al Server (esercitazione di servizi desktop remoto)
Se il **Recordset** oggetto viene modificato, tutte le modifiche (vale a dire le righe che vengono aggiunti, modificate o eliminate) possono essere inviate al server.  
  
> [!NOTE]
>  Il comportamento predefinito di servizi desktop remoto può essere richiamato in modo implicito con oggetti ADO e il Provider remoto Microsoft OLE DB. Le query possono restituire **Recordset**s e modificato **Recordset**s può aggiornare l'origine dati. In questa esercitazione non richiama Servizi Desktop remoto con gli oggetti ADO, ma è come se fosse presente:  
  
```  
Dim rs as New ADODB.Recordset  
rs. "SELECT * FROM Authors","=MS Remote;=Pubs;" & _  
=http://yourServer;=SQLOLEDB;"  
...              ' Edit the Recordset.  
rs.   ' The equivalent of   
...  
```  
  
 **La parte** Presupponi per questo case che si usa solo il [RDS. Elemento DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) e che un **Recordset** oggetto è ora associato il **RDS. Elemento DataControl**. Il [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) metodo aggiorna l'origine dati con tutte le modifiche di **Recordset** oggetto se la [Server](../../../ado/reference/rds-api/server-property-rds.md) e [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà vengono comunque impostate.  
  
```  
Sub RDSTutorial6A()  
Dim DC as New RDS.DataControl  
Dim RS as ADODB.Recordset  
DC. = "http://yourServer"  
DC. = "DSN=Pubs"  
DC. = "SELECT * FROM Authors"  
DC.  
...  
Set RS = DC.  
   ' Edit the Recordset.  
...  
DC.  
...  
```  
  
 **Parte B** in alternativa, è possibile aggiornare il server con il [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto, che specifica una connessione e un **Recordset** oggetto.  
  
```  
Sub RDSTutorial6B()  
Dim DS As New RDS.DataSpace  
Dim RS As ADODB.Recordset  
Dim DC As New RDS.DataControl  
Dim DF As Object  
Dim blnStatus As Boolean  
Set DF = DS.("RDSServer.DataFactory", "http://yourServer")  
Set RS = DF. ("DSN=Pubs", "SELECT * FROM Authors")  
DC. = RS    ' Visual controls can now bind to DC.  
    ' Edit the Recordset.  
blnStatus = DF."DSN=Pubs", RS  
End Sub  
```  
  
 **Questa è la fine dell'esercitazione.**  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Provider di servizi remoti Microsoft OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Esercitazione su RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
