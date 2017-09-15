---
title: Panoramica di schemi e dati multidimensionali | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf3e8d6bebd5860df9f52236eecf4d1f287a8f9d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Panoramica di schemi e dati multidimensionali
## <a name="understanding-multidimensional-schemas"></a>Informazioni sugli schemi multidimensionali  
 L'oggetto di metadati centrali in ADO MD è il *cubo*, che è costituito da un set strutturato di dimensioni correlate, gerarchie, livelli e membri.  
  
 Oggetto *dimensione* è una categoria di dati dal database multidimensionale, derivato da entità aziendali indipendente. In genere, una dimensione contiene gli elementi da utilizzare come criteri di query per le misure del database.  
  
 Oggetto *gerarchia* è un percorso di aggregazione di una dimensione. Una dimensione può avere più livelli di granularità, che hanno relazioni padre-figlio. Una gerarchia definisce la correlazione di questi livelli.  
  
 Oggetto *livello* è un passaggio di aggregazione in una gerarchia. Per le dimensioni con più livelli di informazioni, ogni livello è un livello.  
  
 Oggetto *membro* è un elemento di dati in una dimensione. In genere, si crea una didascalia o si descritta una misura del database utilizzando i membri.  
  
 I cubi sono rappresentati da [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) gli oggetti ADO MD. Dimensioni, gerarchie, livelli e membri sono inoltre rappresentati da oggetti ADO MD corrispondenti: [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [gerarchia](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md), e [ Membro](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Dimensioni  
 Le dimensioni di un cubo dipendono dalle entità aziendali e i tipi di dati da creare nel database. In genere, ogni dimensione è un punto di ingresso indipendenti o di un meccanismo per la selezione di dati.  
  
 Ad esempio, un cubo contenente i dati di vendita ha le cinque dimensioni seguenti: agente, Geography, ora, i prodotti e le misure. La dimensione Measures contiene valori di dati di vendita effettivi, mentre le altre dimensioni rappresentano modi per classificare e raggruppare i valori di dati di vendita.  
  
 La dimensione Geography è il seguente set di membri:  
  
```  
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>Gerarchie  
 Gerarchie definiscono il modo in cui i livelli di una dimensione possono essere "raggruppati" o raggruppati. Una dimensione può avere più di una gerarchia. È presente una gerarchia naturale della dimensione Geography:  
  
### <a name="levels"></a>Levels  
 Nella dimensione Geography riportato di seguito viene illustrata nella figura precedente, ogni casella rappresenta un livello nella gerarchia.  
  
 Ogni livello dispone di un set di membri, come indicato di seguito:  
  
-   il mondo`= {All}`  
  
-   Continenti`= {North America, Europe}`  
  
-   Paesi`= {Canada, USA, UK, Germany}`  
  
-   Aree`= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Città`= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Membri  
 I membri al livello foglia di una gerarchia non hanno elementi figlio e i membri al livello radice non dispongono di alcun elemento padre. Tutti gli altri membri hanno almeno un elemento padre e almeno un elemento figlio. Ad esempio, un attraversamento dell'albero gerarchico nella dimensione Geography parziale restituisce le relazioni padre-figlio seguenti:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 I membri possono essere consolidati per uno o più gerarchie per ogni dimensione. Si consideri una dimensione temporale in cui sono disponibili due modi di eseguire il rollup a livello di anno dal livello di giorni:  
  
 Questo esempio viene inoltre illustrata un'altra caratteristica: alcuni membri del livello settimana della gerarchia anno settimana non vengono visualizzati in qualsiasi livello della gerarchia di un trimestre dell'anno. Di conseguenza, una gerarchia non deve includere tutti i membri di una dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (multidimensionale) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilizzo di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilizzo dei dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
