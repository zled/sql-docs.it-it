---
title: Le impostazioni Client necessarie | Documenti Microsoft
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
helpviewer_keywords: DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 152d3fdee15d8696be60f1575ac1dc785d5420c3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="required-client-settings"></a>Impostazioni Client richieste
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Specificare le impostazioni seguenti per l'utilizzo di un oggetto personalizzato **DataFactory** gestore.  
  
-   Specificare "Provider = MS Remote" nel [connessione ADO (Object)](../../../ado/reference/ado-api/connection-object-ado.md) oggetto [proprietà Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o **connessione** stringa di connessione dell'oggetto "**Provider**= "parola chiave.  
  
-   Impostare il [proprietà CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**.  
  
-   Specificare il nome del gestore da utilizzare nel [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto **gestore** , proprietà o [Recordset ADO (Object)](../../../ado/reference/ado-api/recordset-object-ado.md) stringa di connessione dell'oggetto " **Gestore**= "parola chiave. (Non è possibile impostare il gestore di **connessione** oggetto stringa di connessione.)  
  
 Servizi Desktop remoto include un gestore predefinito sul server denominato **MSDFMAP. Gestore**. (Il file di personalizzazione predefinito denominato MSDFMAP. INI).  
  
 **Esempio**  
  
 Si supponga che le sezioni seguenti **MSDFMAP. INI** e il nome dell'origine dati, AdvWorks, sono stati definiti in precedenza:  
  
```  
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 I frammenti di codice seguente vengono scritti in Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>RDS. Versione DataControl  
  
```  
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "http://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Versione di recordset  
  
```  
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Specificare il [proprietà gestore (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) proprietà o la parola chiave; il [proprietà Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o la parola chiave; e *CustomerById* e  *CustomerDatabase* gli identificatori. Aprire quindi il **Recordset** oggetto  
  
 Reporting Services. Aprire "CustomerByID (4)", "gestore = MSDFMAP. Gestore;"& _  
  
```  
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=http://yourServer"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare il File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione relativa alla personalizzazione File SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione UserList File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sui File di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)






















