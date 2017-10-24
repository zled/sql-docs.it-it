---
title: "Proprietà SortDirection (RDS) | Documenti Microsoft"
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
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1d0395c390da04314dad0bc886f71333baac7b7a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sortdirection-property-rds"></a>Proprietà SortDirection (RDS)
Indica se una sequenza di ordinamento è crescente o decrescente.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *Valore*  
 Oggetto **booleano** valore che, se impostato su **True**, indica la direzione di ordinamento è crescente. **False** indica l'ordine decrescente.  
  
## <a name="remarks"></a>Osservazioni  
 Il [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **SortDirection**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), e [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)proprietà forniscono l'ordinamento e filtrare le funzionalità della cache sul lato client. La funzionalità di ordinamento Ordina i record con valori di una colonna. La funzionalità di filtro consente di visualizzare un subset di record in base a criteri di ricerca, mentre la versione completa [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene mantenuto nella cache. Il [reimpostare](../../../ado/reference/rds-api/reset-method-rds.md) metodo i criteri e sostituire corrente **Recordset** con un aggiornabile **Recordset**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection proprietà e la reimpostazione metodo esempio (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Proprietà di ordinamento](../../../ado/reference/ado-api/sort-property.md)   
 [Proprietà SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)



