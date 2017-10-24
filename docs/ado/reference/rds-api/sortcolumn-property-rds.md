---
title: "Proprietà SortColumn (RDS) | Documenti Microsoft"
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
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c2cf7afef8435343b9b3c7362940e29fc448056
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sortcolumn-property-rds"></a>Proprietà SortColumn (RDS)
Indica da quale colonna per ordinare i record.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 *String*  
 Oggetto **stringa** valore che rappresenta il nome o l'alias della colonna in base al quale ordinare i record.  
  
## <a name="remarks"></a>Osservazioni  
 Il **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), e [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)proprietà forniscono l'ordinamento e filtrare le funzionalità della cache sul lato client. La funzionalità di ordinamento Ordina i record per i valori da una colonna. La funzionalità di filtro consente di visualizzare un subset di record in base a criteri di ricerca, mentre la versione completa [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) viene mantenuto nella cache. Il [reimpostare](../../../ado/reference/rds-api/reset-method-rds.md) metodo i criteri e sostituire corrente **Recordset** con un aggiornabile **Recordset**.  
  
 Ordinare elementi su un **Recordset**, è necessario salvare le modifiche in sospeso. Se si utilizza il **RDS. DataControl**, è possibile utilizzare il [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) metodo. Ad esempio, se il **RDS. DataControl** è denominato ADC1, il codice sarebbe `ADC1.SubmitChanges`. Se si utilizza un oggetto ADO **Recordset**, è possibile utilizzare il relativo [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo. Utilizzando **UpdateBatch** è il metodo consigliato per **Recordset** gli oggetti creati con il [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) metodo. Ad esempio, il codice può essere `myRS.UpdateBatch` o `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn, SortDirection proprietà e la reimpostazione metodo esempio (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Proprietà di ordinamento](../../../ado/reference/ado-api/sort-property.md)   
 [Proprietà SortDirection (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)






