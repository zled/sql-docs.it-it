---
title: Elemento AssociationSet (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 93e5ac4d-d7e8-490e-b775-28263a48cfcc
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d418e75aa451c14db6010f6cb3673cd8c3a74bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229561"
---
# <a name="associationset-element-csdlbi"></a>Elemento AssociationSet (CSDLBI)
  L'elemento `AssociationSet` è un tipo complesso che definisce un'associazione. Nei modelli di dati CSDLBI, un'associazione è una relazione tra due tabelle.  
  
 Per ogni relazione univoca in un modello, è necessario specificare un elemento `AssociationSet`. Per definire gli endpoint, l'elemento `AssociationSet` utilizza l'elemento `Association`. L'elemento `AssociationSet` definisce inoltre i metadati sulla relazione e sul relativo utilizzo nel modello di dati.  
  
## <a name="applicable-attributes"></a>Attributi applicabili  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento `AssociationSet`.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|State|Sì|Stringa che indica se l'associazione è attiva o meno. Il valore è definito dall'elemento State.|  
|Hidden|no|Valore booleano che indica se la relazione è visibile. Per impostazione predefinita, il valore di Hidden è `false`, ovvero tutte le relazioni sono visibili nel modello.|  
  
## <a name="state-element"></a>Elemento State  
 L'elemento `State` è un tipo semplice che descrive se un'associazione è attiva e da utilizzare nei calcoli o se invece è inattiva e vi si deve far riferimento in modo esplicito nei calcoli.  
  
 Se sono presenti più set di associazioni che connettono due entità, solo un set di associazioni può essere contrassegnato come Active. In altre parole, se esistono due relazioni tra due medesime tabelle, solo una relazione può essere attiva.  
  
 Nella tabella seguente vengono elencati i valori dell'elemento `State`.  
  
|valore|Description|  
|-----------|-----------------|  
|Attiva|L'associazione è attiva.|  
|Inactive|L'associazione è attiva.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente viene illustrata una relazione del modello tabulare AdventureWorks, in CSDLBI versione 1.1. L'associazione viene contrassegnata come Inactive in quanto esiste una relazione tra OrderKey e Date.  
  
```  
<AssociationSet   
    Name="InternetSales_Date_Date_Date"  
    Association="Sandbox.InternetSales_Date_Date_Date">  
    <End EntitySet="InternetSales" />  
    <End EntitySet="DimDate" />  
<bi:AssociationSet State="Inactive" />  
</AssociationSet>  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente viene illustrata la relazione definita tra le tabelle Sales e Currency nel cubo Operations di Contoso.  
  
```  
<AssociationSet   
    Name ="Sales_Currency_Currency_Currency_Name2"  
    Association ="Sandbox.Sales_Currency_Currency_Currency_Name2">  
    <End EntitySet ="Sales" />  
    <End EntitySet ="Currency" />  
<bi:AssociationSet />  
</AssociationSet>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
