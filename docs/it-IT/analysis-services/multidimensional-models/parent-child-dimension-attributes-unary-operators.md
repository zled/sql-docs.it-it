---
title: Operatori unari nelle dimensioni padre-figlio | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4646fd5e9a58ba275c10549aa5a9ae0600c41070
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="parent-child-dimension-attributes---unary-operators"></a>Attributi della dimensione padre-figlio, gli operatori unari
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In una dimensione contenente una relazione padre-figlio in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specificare una colonna dell'operatore unario (o di rollup personalizzato) che determina il rollup personalizzato per tutti i membri non calcolati dell'attributo padre. L'operatore unario viene applicato ai membri ogni volta che i valori dei membri padre vengono valutati. La proprietà **UnaryOperatorColumn** in un attributo padre (**Usage**=Parent) specifica la colonna di una tabella nella vista origine dati contenente gli operatori unari. I valori per gli operatori di rollup personalizzato archiviati in questa colonna vengono applicati a ogni membro dell'attributo.  
  
 È possibile creare e specificare un calcolo denominato in una tabella della dimensione nella vista origine dati come colonna dell'operatore unario. L'espressione più semplice, ad esempio '+', restituisce lo stesso operatore per tutti i membri. È tuttavia possibile utilizzare qualsiasi espressione a condizione che restituisca un operatore per ogni membro.  
  
 È possibile modificare manualmente l'impostazione della proprietà **UnaryOperatorColumn** in un attributo padre oppure usare la funzionalità avanzata di definizione della funzione di aggregazione personalizzata disponibile in Configurazione guidata funzionalità di Business Intelligence per sostituire la funzione di aggregazione predefinita associata ai membri di una dimensione. Per altre informazioni sull'uso di Configurazione guidata funzionalità di Business Intelligence per eseguire questa configurazione, vedere [Aggiungere un'aggregazione personalizzata a una dimensione](../../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
 L'impostazione predefinita della proprietà **UnaryOperatorColumn** in un attributo è (nessuna), ovvero gli operatori di rollup personalizzato sono disabilitati. Nella tabella seguente vengono elencati gli operatori unari e viene descritta la loro funzione quando vengono applicati a un livello.  
  
|Operatore unario|Description|  
|--------------------|-----------------|  
|+ (segno di addizione)|Il valore del membro viene aggiunto al valore aggregato dei membri di pari livello precedenti. Si tratta dell'operatore predefinito se per un attributo non viene definita alcuna colonna dell'operatore unario.|  
|– (segno di sottrazione)|Il valore del membro viene sottratto dal valore aggregato dei membri di pari livello precedenti.|  
|* (asterisco)|Il valore del membro viene moltiplicato per il valore aggregato dei membri di pari livello precedenti.|  
|/ (barra)|Il valore del membro viene diviso per il valore aggregato dei membri di pari livello precedenti.|  
|~ (tilde)|Il valore del membro viene ignorato.|  
  
 I valori vuoti e qualsiasi altro valore non presente nella tabella vengono considerati come operatori unari (+). Poiché non esiste un ordine di precedenza tra gli operatori, l'ordine di valutazione è determinato dall'ordine dei membri archiviati nella colonna dell'operatore unario. Per modificare l'ordine di valutazione, creare un nuovo attributo, impostarne la proprietà **Type** su **Sequence**e quindi assegnare numeri di sequenza corrispondenti all'ordine di valutazione nella relativa proprietà **Source Column** . È inoltre necessario ordinare i membri dell'attributo in base a tale attributo. Per altre informazioni sull'uso di Configurazione guidata funzionalità di Business Intelligence per ordinare i membri di un attributo, vedere [Definire l'ordinamento di una dimensione](../../analysis-services/multidimensional-models/bi-wizard-define-the-ordering-for-a-dimension.md).  
  
 È possibile usare la proprietà **UnaryOperatorColumn** per specificare un calcolo denominato che restituisca un operatore unario come valore letterale per tutti i membri dell'attributo. È sufficiente digitare un carattere letterale quale `'*'` nel calcolo denominato. In questo modo l'operatore predefinito, ovvero il segno di addizione (+), viene sostituito dall'operatore di moltiplicazione, ovvero l'asterisco (*), per tutti i membri dell'attributo. Per altre informazioni, vedere [Definire calcoli denominati in una vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md).  
  
 Nella scheda **Esplorazione** di Progettazione dimensioni è possibile visualizzare gli operatori unari accanto a ogni membro di una gerarchia. È inoltre possibile modificare gli operatori unari in caso di utilizzo di una dimensione abilitata per la scrittura. Se la dimensione non è abilitata per la scrittura, è necessario utilizzare uno strumento per modificare direttamente l'origine dei dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [Operatori di Rollup personalizzati nelle dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)   
 [Avviare la procedura guidata di Business Intelligence in Progettazione dimensioni](../../analysis-services/multidimensional-models/database-dimensions-bi-wizard-in-dimension-designer.md)  
  
  
