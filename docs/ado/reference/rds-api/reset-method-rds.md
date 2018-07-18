---
title: Reset (metodo) (RDS) | Documenti Microsoft
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8528794ecf2d52ec62225085c4de03d250ebf16
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288560"
---
# <a name="reset-method-rds"></a>Reset (metodo) (RDS)
Esegue l'ordinamento o filtro sul lato client **Recordset** basato sulle proprietà di ordinamento e filtro specificata.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *Valore*  
 Facoltativo. Oggetto **booleano** valore **True** (impostazione predefinita), se si desidera filtrare il set di righe "filtrato" corrente. **False** indica che viene filtrato il set di righe originale, rimuovendo eventuali opzioni di filtro precedente.  
  
## <a name="remarks"></a>Remarks  
 Il [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), e [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)proprietà forniscono l'ordinamento e filtrare le funzionalità della cache sul lato client. La funzionalità di ordinamento Ordina i record per i valori da una colonna. La funzionalità di filtro consente di visualizzare un subset di record in base a criteri di ricerca, la versione completa [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene mantenuto nella cache. Il **reimpostare** metodo i criteri e sostituire corrente **Recordset** con un aggiornabile **Recordset**.  
  
 Se sono presenti modifiche ai dati originali non sono state inviate le **reimpostare** metodo avrà esito negativo. Innanzitutto, utilizzare il [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) per salvare le modifiche in lettura/scrittura **Recordset**e quindi usare il **reimpostare** metodo per ordinare o filtrare i record.  
  
 Se si desidera eseguire più di un filtro sul set di righe, è possibile utilizzare l'opzione facoltativa *booleano* argomento con il **reimpostare** metodo. Nell'esempio seguente viene illustrato come eseguire questa operazione:  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection proprietà e la reimpostazione metodo esempio (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



