---
title: Cell (MDDataSet) (XMLA) elemento | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Cell Element (MDDataSet)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: c4ea08a4-f653-4ade-be07-b91eb5b1ef32
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f07798a28c59597575de08bf5d0f3ea1d7087c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269507"
---
# <a name="cell-element-mddataset-xmla"></a>Elemento Cell (MDDataSet) (XMLA)
  Contiene informazioni su una sola cella contenuta in un elemento padre [CellData](celldata-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CellData>  
   <Cell CellOrdinal="unsignedInt">  
      <!-- Zero or more cell property values -->  
      <!-- or -->  
      <Error>...</Error>  
   </Cell>  
</CellData>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CellData](celldata-element-xmla.md)|  
|Elementi figlio|Zero o più valori di proprietà di cella o [errore](error-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|CellOrdinal|Obbligatorio `unsignedInt` attributo. La posizione ordinale della cella all'interno del dataset multidimensionale.|  
  
## <a name="remarks"></a>Note  
 Nell'elemento `root` padre, l'elemento `Axes` è seguito dall'elemento `CellData`, una raccolta di elementi `Cell` che contengono i valori della proprietà per ogni cella restituito nel dataset multidimensionale. L'elemento `Cell` contiene l'attributo `CellOrdinal` che indica la posizione ordinale in base zero della cella all'interno del dataset multidimensionale e un elemento per ogni valore della proprietà della cella associato alla cella stessa. Ogni valore della proprietà della cella nell'elemento `Cell` è definito da un elemento XML separato. Il valore della proprietà della cella comprende i dati contenuti nell'elemento XML; il nome della proprietà della cella, come definito nell'elemento `CellInfo` dell'elemento radice padre, corrisponde al nome dell'elemento XML.  
  
 Nella sintassi seguente viene descritto un valore della proprietà della cella:  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 Il tipo di dati del valore proprietà della cella viene specificato solo per la proprietà VALORE della cella. I tipi di dati di altre proprietà della cella sono determinati dalla definizione di proprietà della cella inclusa nell'elemento `CellInfo`. Un elemento del valore della proprietà di cella può essere escluso se un valore predefinito è stato specificato (includendo un elemento `Default` per una definizione di proprietà della cella contenuta nell'elemento `CellInfo` ) per una proprietà della cella, o se non è stato specificato alcun valore predefinito e il valore della proprietà della cella è null.  
  
## <a name="cell-property-errors"></a>Errori proprietà cella  
 Se una proprietà della cella non può essere restituita a causa di un errore che si verifica nell'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio un errore di calcolo che impedisce che il valore restituito per una cella specificata, un `Error` elemento sostituisce il contenuto della proprietà della cella in questione. Nell'esempio XML seguente è descritto un errore di proprietà della cella:  
  
```  
<Cell CellOrdinal="0">  
   <Value xsi:type="xsd:double">  
      <Error>  
         <ErrorCode>2148497527</ErrorCode>  
         <Description>Unknown error</Description>  
      </Error>  
   </Value>  
</Cell>  
```  
  
## <a name="calculating-cell-ordinal-values"></a>Calcolo dei valori ordinali di cella  
 Il riferimento dell'asse per una cella può essere calcolato in base a un valore dell'attributo `CellOrdinal`. Concettualmente, le celle sono numerate in un set di dati come se fosse il set di dati di un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga.  
  
 Si suppone che una query richieda quattro misure su colonne e una crossjoin di due stati con quattro trimestri sulle righe. Nel risultato del dataset, la proprietà `CellOrdinal` per la parte del risultato del dataset mostrata in grassetto è il set {9, 10 11, 13 14, 15 17, 18 19}. Il set è di questo tipo perché le celle sono numerate in ordine crescente di riga, iniziando con un `CellOrdinal` di 0 per la cella più in alto a sinistra.  
  
|State|Quarter|Vendite unità|Costo magazzino|Vendite magazzino|Conto vendite|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|(DOMANDA 1)|16890|14431.09|36175.2|5498|  
||(DOMANDA 2)|18052|15332.02|38396.75|5915|  
||(DOMANDA 3)|18370|**15672.83**|**39394.05**|**6014**|  
||(DOMANDA 4)|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|(DOMANDA 1)|19287|**16081.07**|**40170.29**|**6184**|  
||(DOMANDA 2)|15079|12678.96|31772.88|4799|  
||(DOMANDA 3)|16940|14273.78|35880.46|5432|  
||(DOMANDA 4)|16353|13738.68|34453.44|5196|  
|Washington|(DOMANDA 1)|30114|25240.08|63282.86|9906|  
||(DOMANDA 2)|29479|24953.25|62496.64|9654|  
||(DOMANDA 3)|30538|25958.26|64997.38|10007|  
||(DOMANDA 4)|34235|29172.72|73016.34|11217|  
  
 Applicando la formula nella figura, l’asse k = 0 ha Uk = 4 membri e l’asse k = 1 ha Uk = 8 tuple P = 2 è il numero complessivo di assi nella query. Prendendo la cella {California, Q3 Archivia Costato} come S0, la sommatoria iniziale è i = 0 a 1. Per i = 0, l'ordinale della tupla su asse 0 di {Costo Magazzino} è 1. Per i = 1, l'ordinale della tupla di {CA, Q3} è 2.  
  
 Per i = 0, Ei = 1, quindi ad ho = 0 la somma è 1 * 1 = 1 e per i = 1, la somma è 2 (ordinale della tupla) orari 4 (il valore di Ei calcolato come 1 \* 4), o 8. La somma di 1 + 8 è quindi 9, l'ordinale della cella per quella cella.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene dimostrata la struttura dell'elemento `Cell`, inclusi i valori delle proprietà delle celle VALORE, VALORE_FORMATTATO e STRINGA_FORMATO per ogni cella.  
  
```  
<CellData>  
   <Cell CellOrdinal="0">  
      <Value xsi:type="xsd:double">16890</Value>  
      <FmtValue>16,890.00</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="1">  
      <Value xsi:type="xsd:int">50</Value>  
      <FmtValue>50</FmtValue>  
      <FormatString>Standard</FormatString>  
   </Cell>  
   <Cell CellOrdinal="2">  
      <Value xsi:type="xsd:double">36175.2</Value>  
      <FmtValue>$36,175.20</FmtValue>  
      <FormatString>Currency</FormatString>  
   </Cell>  
</CellData>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati MDDataSet &#40;XMLA&#41;](../xml-data-types/mddataset-data-type-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
