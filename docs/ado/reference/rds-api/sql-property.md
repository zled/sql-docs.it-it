---
title: "Proprietà SQL | Documenti Microsoft"
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
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b16ac51bae59fbb4435f094da6e0ac0e40053e89
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sql-property"></a>Proprietà SQL
Indica la stringa di query utilizzata per recuperare il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 È possibile impostare il **SQL** proprietà in fase di progettazione nel [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) tag OBJECT dell'oggetto, o in fase di esecuzione nel codice di script.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parametri  
 *Stringa di query*  
 Oggetto **stringa** valore che contiene una richiesta di dati SQL valida.  
  
 *DataControl*  
 Una variabile oggetto che rappresenta un **RDS. DataControl** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 In generale, si tratta di un'istruzione SQL, utilizzando il sottolinguaggio del server di database, ad esempio `"Select * from NewTitles"`. Per garantire che i record siano corrispondenti e aggiornati in modo accurato, una query aggiornabile deve contenere un campo diverso da un campo binario lungo o un campo calcolato.  
  
 Il **SQL** proprietà è facoltativa se un oggetto business sul lato server personalizzato recupera i dati per il client.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Proprietà Connect (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Metodo query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Metodo SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



