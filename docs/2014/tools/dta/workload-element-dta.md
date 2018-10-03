---
title: Elemento Workload (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1bc86764dce10dfad5c25ca7a1bd7f3d2bc519c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087301"
---
# <a name="workload-element-dta"></a>Elemento Workload (DTA)
  Specifica il carico di lavoro da utilizzare per una sessione di ottimizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Avviare e usare Ottimizzazione guidata motore di database](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**Elementi figlio**|[File di elemento &#40;DTA&#41;](file-element-dta.md)<br /><br /> [Elemento database per il carico di lavoro &#40;DTA&#41;](database-element-for-workload-dta.md)<br /><br /> [Elemento EventString &#40;DTA&#41;](eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Note  
 Un carico di lavoro è un set di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite sui database che si desidera ottimizzare. Ottimizzazione guidata motore di database può utilizzare come carichi di lavoro script [!INCLUDE[tsql](../../includes/tsql-md.md)] , file di traccia e tabelle di traccia.  
  
 Se viene specificato un carico di lavoro in un file di input XML e un carico di lavoro nella riga di comando con lo strumento **dta** , per l'ottimizzazione verrà utilizzato il carico di lavoro specificato nella riga di comando. Tutte le opzioni di ottimizzazione specificate nella riga di comando prevalgono su quelle specificate in un file di input XML. L'unica eccezione è rappresentata dal caso in cui una configurazione definita dall'utente venga specificata in modalità di valutazione nel file di input XML. Ad esempio, se viene immessa una configurazione nel `Configuration` elemento del file di input XML e `EvaluateConfiguration` elemento viene specificato come una delle opzioni di ottimizzazione, le opzioni di ottimizzazione specificate nel file di input XML sostituiranno le opzioni di ottimizzazione immesse dalla la riga di comando.  
  
 È necessario specificare un carico di lavoro per ogni sessione di ottimizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente specifica i **MyDatabase.MyDBOwner.TuningTable001** tabella di traccia per il `Workload` elemento. La tabella **TuningTable001** è stata creata con il modello Tuning di SQL Server Profiler e salvando l'output della traccia come tabella.  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
