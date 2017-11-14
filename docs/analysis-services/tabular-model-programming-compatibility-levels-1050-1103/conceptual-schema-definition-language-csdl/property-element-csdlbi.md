---
title: Elemento Property (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d61770b935ad397d5d0db48a3651f143ebef5522
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="property-element-csdlbi"></a>Elemento Property (CSDLBI)
  L'elemento Property in CSDLBI è un tipo complesso che fornisce le aggiunte all'elemento Property di CSDL, a supporto dei modelli di dati di Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Property di CSDLBI.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Sommario|No|Stringa che contiene l'identificatore delle impostazioni locali (LCID) della richiesta.|  
|DefaultAggregationFunction|Sì|Stringa che specifica la funzione di aggregazione che deve essere utilizzata se i calcoli vengono eseguiti sull'attributo e nessun'altra funzione è stata specificata.<br /><br /> Se omessa, viene utilizzata l'aggregazione predefinita per il modello, di solito SUM.|  
|GroupingBehavior|No|Valore che specifica come vengono raggruppati i risultati della query. Il contenuto dell'attributo è definito dal tipo semplice TGroupingBehavior (vedere la tabella di seguito).|  
|OrderBy|No|Riferimento a un'altra proprietà all'interno del modello che definisce l'ordinamento per i valori di questa proprietà.<br /><br /> I valori per le due proprietà DOVONO avere un mapping da 1 a 1. In caso contrario, il comportamento dell'ordinamento è indefinito.<br /><br /> Se questo elemento viene omesso, le proprietà vengono ordinate in base ai relativi valori.|  
|Stability|No|Attributo che specifica la stabilità dei valori di proprietà tra le operazioni di aggiornamento.<br /><br /> Questo attributo non viene impostato dagli utenti, ma viene generato dall'ambiente di progettazione solo per valori instabili. Viene sempre applicato alle colonne contenenti un numero di righe e alle colonne contenenti formule che generano risultati indeterminati, ad esempio NOW() o RAND().<br /><br /> I valori per questo attributo sono elencati nella tabella seguente in cui viene descritto il tipo Stabilitysimple.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 Nella tabella seguente vengono elencati i valori del tipo semplice GroupingBehavior.  
  
|Valore|Description|  
|-----------|-----------------|  
|GroupOnValue|Raggruppare in base al valore dell'attributo.|  
|GroupOnEntityKey|Raggruppare in base alla chiave di entità.|  
  
 Nell'esempio seguente viene illustrato l'utilizzo di questi due valori. Si supponga che la query sia stata progettata per restituire le deduzioni delle retribuzioni per un determinato utente che viene specificato in base al nome. Se il database contiene due utenti con lo stesso nome ma con identificatori di database diversi, i risultati della query sono diversi a seconda del valore dell'attributo applicato alla colonna:  
  
-   **GroupOnValue**: Query risultati includono singole deduzioni delle retribuzioni di entrambi gli utenti contemporaneamente.  
  
-   **GroupOnEntityKey**: Query risultati includono singole deduzioni delle retribuzioni per ogni utente, ma elencati singolarmente.  
  
## <a name="stability"></a>Stability  
 Nella tabella seguente sono elencati i valori del **stabilità** tipo semplice.  
  
|Valore|Description|  
|-----------|-----------------|  
|Stable|La proprietà rimane costante tra le operazioni di aggiornamento.|  
|RowNumber|La proprietà contiene un numero di riga.|  
|Volatile|La proprietà potrebbe non rimanere costante tra le operazioni di aggiornamento.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'XML seguente vengono rappresentate, in CSDLBI versione 1.1, alcune proprietà nel modello tabulare di esempio di AdventureWorks.  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, vengono mostrate alcune proprietà per le colonne del modello di dati che rappresenta il cubo Operations di Contoso. Si noti che le annotazioni Business Intelligence non vengono richieste o applicate alla maggior parte delle colonne, ma solo a quelle che richiedono una gestione speciale nel livello di presentazione.  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  

