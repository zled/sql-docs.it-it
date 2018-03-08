---
title: Oggetto di associazione di dati della Rubrica indirizzi | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9689d8c41a899c9446f3f21ede83ea88c68b77a3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="address-book-data-binding-object"></a>Oggetto di associazione di dati della Rubrica
L'applicazione Address Book utilizza il [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto per associare i dati dal database di SQL Server a un oggetto visivo (in questo caso, una tabella DHTML) la pagina dell'applicazione client HTML. Usa la logica di programma VBScript basati sugli eventi di [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) per:  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
-   Eseguire query sul database, inviare aggiornamenti al database e aggiornare la griglia dati.  
  
-   Consentire agli utenti di spostarsi al primo, successivo, precedente, o l'ultimo record nella griglia dei dati.  
  
 Il codice seguente definisce il **RDS. DataControl** componente:  
  
```  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="http://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 Il tag OBJECT definisce il **RDS. DataControl** componente nel programma. Il tag include due tipi di parametri:  
  
-   Quelli associati con il tag OBJECT generico.  
  
-   Parametri specifici per il **RDS. DataControl** oggetto.  
  
## <a name="generic-object-tag-parameters"></a>Parametri del Tag OBJECT generico  
 Nella tabella seguente vengono descritti i parametri associati con il tag OBJECT.  
  
|Parametro|Description|  
|---------------|-----------------|  
|***CLASSID***|Numero univoco a 128 bit che identifica il tipo di oggetto incorporato al sistema. Questo identificatore viene mantenuto nel Registro di sistema del computer locale. (Per l'ID di classe di **RDS. DataControl** , vedere [RDS. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***ID***|Definisce un identificatore a livello di documento per l'oggetto incorporato che viene utilizzato per identificarlo nel codice.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. Parametri DataControl Tag  
 Nella tabella seguente vengono descritti i parametri specifici per il **RDS. DataControl** oggetto. (Per un elenco completo del **RDS. DataControl** oggetto parametri e all'implementazione, vedere [RDS. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Parametro|Description|  
|---------------|-----------------|  
|[SERVER](../../../ado/reference/rds-api/server-property-rds.md)|Se si sta utilizzando HTTP, il valore è il nome del computer server preceduto da `http://`.|  
|[CONNECT](../../../ado/reference/rds-api/connect-property-rds.md)|Fornisce le informazioni di connessione necessarie per il **RDS. DataControl** per connettersi a SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Imposta o restituisce la stringa di query utilizzata per recuperare il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Pulsanti di comando di Address Book](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


