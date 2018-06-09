---
title: Proprietà DAX | Documenti Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9150eb13b6c39f74f1e65743b6a79aca0a07676a
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238841"
---
# <a name="dax-properties"></a>Proprietà DAX
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

   La sezione DAX del file msmdsrv.ini contiene impostazioni che consentono di controllare particolari comportamenti delle query in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ad esempio il limite superiore del numero di righe restituite in un set di risultati di query DAX.

  Per i set di righe di maggiori dimensioni, ad esempio quelli restituiti nei modelli DirectQuery, l'impostazione predefinita pari a un milione di righe può risultare insufficiente. La necessità di adeguare il limite è segnalata da un messaggio di errore simile al seguente: "Il set di risultati di una query sull'origine dati esterna ha superato le dimensioni massime consentite di '1000000' righe."

Per aumentare il limite superiore, specificare l'impostazione di configurazione **MaxIntermediateRowSize** . Sarà necessario aggiungere manualmente l'intero elemento alla sezione DAX del file di configurazione. L'impostazione non è presente nel file fino a quando non viene aggiunta.

## <a name="configuration-snippet"></a>Frammento di configurazione

```
<ConfigurationSettings>
. . .
<DAX>
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . .
```

## <a name="property-descriptions"></a>Descrizioni delle proprietà

Impostazione |valore |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Numero massimo di righe restituito in una query DAX. Aggiungere manualmente questa voce al file msmdsrv.ini e aumentarne il valore se l'impostazione predefinita è troppo bassa.
PredicateCheckSpoolCardinalityThreshold| 5000 | Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico Microsoft.

Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
