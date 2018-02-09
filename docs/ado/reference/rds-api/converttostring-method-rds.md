---
title: Metodo ConvertToString (RDS) | Documenti Microsoft
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
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95425c734f254bf534eacdad606025fca43c2158
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="converttostring-method-rds"></a>Metodo ConvertToString (RDS)
Converte un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in una stringa MIME che rappresenta i dati di recordset.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataFactory*  
 Una variabile oggetto che rappresenta un [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto.  
  
 *Recordset*  
 Una variabile oggetto che rappresenta un **Recordset** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 I file ASP, usare **ConvertToString** per incorporare il **Recordset** in una pagina HTML generata nel server per il trasporto in un computer client.  
  
 **ConvertToString** carica innanzitutto il **Recordset** nel servizio cursore le tabelle e quindi genera un flusso in formato MIME.  
  
 Nel client, Remote Data Service può convertire la stringa MIME in completamente funzionante **Recordset**. Funziona anche per la gestione di meno di 400 righe di dati con non più di larghezza di 1024 byte per ogni riga. Non è consigliabile utilizzare per trasmettere dati BLOB e di set di risultati di grandi dimensioni tramite HTTP. Nessuna compressione in transito viene eseguita nella stringa di molto grandi set di dati verrà richiedere tempi lunghi di trasporto su HTTP rispetto al formato con ottimizzazione per la trasmissione viene definito e distribuito da Remote Data Service come formato di protocollo di trasporto nativi.  
  
> [!NOTE]
>  Se si utilizza Active Server Pages per incorporare la stringa MIME risultante in una pagina HTML client, tenere presente che le versioni precedenti alla versione 2.0 di VBScript limitano le dimensioni della stringa di 32 KB. Se questo limite viene superato, viene restituito un errore. Quando si utilizza l'incorporamento MIME tramite i file ASP, mantenere l'ambito della query relativamente ridotto. Per risolvere questo problema, scaricare la versione più recente di VBScript dal sito Web di Microsoft Windows Script Technologies.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo ConvertToString (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [Esempio di metodo ConvertToString (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


