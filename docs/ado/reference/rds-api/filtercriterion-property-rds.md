---
title: "Proprietà FilterCriterion (RDS) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: FilterCriterion property [RDS]
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 24e64adb684435f40c52c55d1c97b1c863551ecb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="filtercriterion-property-rds"></a>Proprietà FilterCriterion (RDS)
Indica l'operatore di valutazione da utilizzare nel valore di filtro.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *String*  
 Oggetto **stringa** valore che specifica l'operatore di valutazione del [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) ai record. Può essere una qualsiasi delle operazioni seguenti: <, \<=, >, > =, =, o <>.  
  
## <a name="remarks"></a>Osservazioni  
 Il [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **FilterCriterion**, e [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)proprietà forniscono l'ordinamento e filtrare le funzionalità della cache sul lato client. La funzionalità di ordinamento Ordina i record per i valori da una colonna. La funzionalità di filtro consente di visualizzare un subset di record in base a criteri di ricerca, mentre la versione completa [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene mantenuto nella cache. Il [reimpostare](../../../ado/reference/rds-api/reset-method-rds.md) metodo i criteri e sostituire corrente **Recordset** con un aggiornabile **Recordset**.  
  
 Il "! =" operatore non è valido per **FilterCriterion**; in alternativa, utilizzare "<>".  
  
 Se il filtro e l'ordinamento vengono impostate e si chiama il **reimpostare** metodo, viene innanzitutto filtrato il set di righe e quindi eseguire l'ordinamento. Per ordinamenti crescenti, i valori null sono in alto. per ordinamenti decrescenti, i valori null sono nella parte inferiore (crescente è l'impostazione predefinita).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection proprietà e la reimpostazione metodo esempio (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Proprietà FilterColumn (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [Proprietà FilterValue (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [Proprietà SortColumn (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [Proprietà SortDirection (Servizi Desktop remoto)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


