---
title: "Proprietà del gestore (RDS) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25ac7c676fbab1e8b5899a3502fab2199b0afd22
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="handler-property-rds"></a>Proprietà del gestore (RDS)
Indica il nome di un programma di personalizzazione lato server (gestore) che estende la funzionalità del [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)ed eventuali parametri utilizzati per il *gestore*.  
  
 **Si applica a:** [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *String*  
 Oggetto **stringa** valore contenente il nome del gestore e tutti i parametri, tutti separati da virgole (ad esempio, `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà supporta [personalizzazione](../../../ado/guide/remote-data-service/datafactory-customization.md), una funzionalità che richiede l'impostazione di [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**.  
  
 Il nome del gestore e i relativi parametri, se presenti, sono separati da virgole (","). Un comportamento imprevedibile determinerà se un punto e virgola (";"), viene visualizzato in un punto qualsiasi all'interno di *stringa*. È possibile scrivere un gestore personalizzato, a condizione che supporti il **IDataFactoryHandler** interfaccia.  
  
 Il nome del gestore predefinito è **MSDFMAP. Gestore**, e il relativo parametro predefinito è un file di personalizzazione denominato **MSDFMAP. INI**. Utilizzare questa proprietà per richiamare i file di personalizzazione alternativi creati dall'amministratore del server.  
  
 Alternativa all'impostazione di **gestore** è di proprietà per specificare parametri in e un gestore di [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà; ovvero "**gestore =**  *handlerName parameter1, parameter2,....* ".  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Handler (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)



