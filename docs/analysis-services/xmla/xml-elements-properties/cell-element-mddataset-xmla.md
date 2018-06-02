---
title: Cella elemento (MDDataSet) (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ba73a6ea5926de6f445c5ca5cec8142b3e196bd
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576273"
---
# <a name="cell-element-mddataset-xmla"></a>Elemento Cell (MDDataSet) (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni su una sola cella contenuta in un elemento padre [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md) elemento.  
  
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
|Elementi padre|[CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md)|  
|Elementi figlio|Zero o più valori di proprietà di cella o [errore](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|CellOrdinal|Richiesto **unsignedInt** attributo. La posizione ordinale della cella all'interno del dataset multidimensionale.|  
  
## <a name="remarks"></a>Remarks  
 Nell'elemento padre **radice** elemento, il **assi** elemento è seguito dal **CellData** elemento, una raccolta di **cella** elementi contenenti i valori di proprietà per ogni cella restituita nel dataset multidimensionale. Il **cella** elemento contiene il **CellOrdinal** attributo, che indica la posizione ordinale in base zero della cella all'interno del dataset multidimensionale e di un elemento per ogni valore della proprietà cella associato alla cella. Valore di proprietà di ogni cella di **cella** è definita da un elemento XML separato. Il valore della proprietà della cella è i dati contenuti nell'elemento XML e il nome della proprietà della cella, come definito nel **CellInfo** elemento dell'elemento radice padre, corrisponde al nome dell'elemento XML.  
  
 Nella sintassi seguente viene descritto un valore della proprietà della cella:  
  
```  
<CellProperty xsi:type="string">value</CellProperty>  
```  
  
 Il tipo di dati del valore proprietà della cella viene specificato solo per la proprietà VALORE della cella. I tipi di dati di altre proprietà della cella sono determinati dalla definizione della proprietà di cella inclusa nel **CellInfo** elemento. Un elemento di valore di proprietà di cella può essere escluso se è stato specificato un valore predefinito (includendo un **predefinito** elemento per una definizione di proprietà di cella contenuta nel **CellInfo** elemento) per una proprietà di cella, o se non è stato specificato alcun valore predefinito e il valore della proprietà della cella è null.  
  
## <a name="cell-property-errors"></a>Errori proprietà cella  
 Se una proprietà della cella non può essere restituita a causa di un errore che si verifica nell'istanza di Analysis Services, ad esempio un errore di calcolo che impedisce che il valore restituito per una cella specificata, un **errore** elemento sostituisce il contenuto del proprietà della cella in questione. Nell'esempio XML seguente è descritto un errore di proprietà della cella:  
  
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
 Il riferimento dell'asse per una cella può essere calcolato in base una **CellOrdinal** valore dell'attributo. Concettualmente, le celle sono numerate in un set di dati come se fosse il set di dati un *p*-matrice dimensionale, dove *p* è il numero di assi. Le celle sono indirizzate in ordine di riga.  
  
 Si suppone che una query richieda quattro misure su colonne e una crossjoin di due stati con quattro trimestri sulle righe. Nella seguente il risultato del set di dati, il **CellOrdinal** proprietà per la parte del risultato del dataset mostrata in grassetto è il set {9, 10, 11, 13, 14, 15, 17, 18, 19}. Infatti, il set di celle sono numerate in ordine crescente di riga, a partire da un **CellOrdinal** pari a 0 per la cella superiore sinistra.  
  
|State|Quarter|Vendite unità|Costo magazzino|Vendite magazzino|Conto vendite|  
|-----------|-------------|----------------|----------------|-----------------|-----------------|  
|California|Q1|16890|14431.09|36175.2|5498|  
||Q2|18052|15332.02|38396.75|5915|  
||Q3|18370|**15672.83**|**39394.05**|**6014**|  
||T4|21436|**18094.5**|**45201.84**|**7015**|  
|Oregon|Q1|19287|**16081.07**|**40170.29**|**6184**|  
||Q2|15079|12678.96|31772.88|4799|  
||Q3|16940|14273.78|35880.46|5432|  
||T4|16353|13738.68|34453.44|5196|  
|Washington|Q1|30114|25240.08|63282.86|9906|  
||Q2|29479|24953.25|62496.64|9654|  
||Q3|30538|25958.26|64997.38|10007|  
||T4|34235|29172.72|73016.34|11217|  
  
 Applicando la formula nella figura, l’asse k = 0 ha Uk = 4 membri e l’asse k = 1 ha Uk = 8 tuple P = 2 è il numero complessivo di assi nella query. Prendendo la cella {California, Q3 Archivia Costato} come S0, la sommatoria iniziale è i = 0 a 1. Per i = 0, l'ordinale della tupla su asse 0 di {Costo Magazzino} è 1. Per i = 1, l'ordinale della tupla di {CA, Q3} è 2.  
  
 Per i = 0, Ei = 1, pertanto per i = 0 la somma è 1 * 1 = 1 e per i = 1, la somma è 2 (ordinale della tupla) orari 4 (il valore di Ei calcolato come 1 \* 4), o 8. La somma di 1 + 8 è quindi 9, l'ordinale della cella per quella cella.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente illustra la struttura del **cella** elemento, inclusi il valore, FORMATTED_VALUE e FORMAT_STRING cella i valori delle proprietà per ogni cella.  
  
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
 [Tipo di dati MDDataSet &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
