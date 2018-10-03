---
title: Elemento EntityType (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3d1db1998e91eedf4ebc8f759550b2088a29d03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139991"
---
# <a name="entitytype-element-csdlbi"></a>Elemento EntityType (CSDLBI)
  L'elemento `EntityType` è un tipo complesso che rappresenta la struttura di un'entità ad alto livello, ad esempio un cliente o un ordine, nel modello di dati. Il `bi:EntityType` elemento estende la definizione di [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) utilizzata nel [Entity Data Framework](/dotnet/framework/data/adonet/ef/overview).  
  
 Un elemento EntityType deve essere specificato per ognuna delle entità incluse nel modello di dati. I sottoelementi di EntityType descrivono le colonne e le misure nella tabella. Le relazioni tra le tabelle sono definite in `EntityContainer`.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento `EntityType`. Vedere anche gli attributi applicabili per il [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) elemento.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Sommario|no|Stringa contenente i possibili tipi di dati in una colonna. Il valore è derivato dal valore di DimensionAttributeTypeEnumType nel modello di dati.<br /><br /> Se il valore di DimensionAttributeTypeEnumType è "ExtendedType", il valore del contenuto è derivato dall'elemento ExtendedType di DimensionAttribute. Il client non è necessario per rispondere a tali valori.|  
|DefaultDetails|no|Elenco di riferimenti a proprietà che rappresentano il set di colonne nella tabella.<br /><br /> Visualizzare [elemento DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md).|  
|DefaultImage|no|Riferimento a una colonna contenente l'immagine che illustra l'entità.<br /><br /> Nei modelli multidimensionali, questo elemento corrisponde a un attributo binario dell'attributo della dimensione. Se questo attributo è presente, l'elemento deve contenere un solo elemento MemberRef.<br /><br /> Visualizzare [elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DefaultMeasure|no|Riferimento a una misura dell'entità che deve essere utilizzato come impostazione predefinita durante l'esecuzione dei calcoli dell'entità. Se omesso, il valore predefinito è SUM.<br /><br /> Visualizzare [elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DisplayKey|no|Elenco di riferimenti a colonne o estremità del ruolo che costituiscono un identificatore sicuro che identifica in modo univoco un'istanza di entità.<br /><br /> Visualizzare [elemento DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md).|  
|Gerarchia|no|Elenco delle gerarchie nel modello.<br /><br /> Visualizzare [elemento Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md).|  
|ReferenceName|Sì|Identificatore che può essere utilizzato per fare riferimento a questa entità in una query DAX (Data Analysis Expressions).<br /><br /> Se tale attributo non è presente, viene utilizzato il nome completo del campo dell'entità.|  
|SortMembers|no|Elenco di proprietà utilizzato per l'ordinamento. L'attributo SortDirection indica se l'ordinamento è crescente o decrescente.|  
  
## <a name="contents-element"></a>Elemento Contents  
 L'elemento `Contents` è un tipo semplice che descrive il tipo di dati dell'entità.  
  
 Il contenuto dell'entità (colonna) può essere uno dei valori seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|Regular|Non altrimenti definito.|  
|Time|Attributi che rappresentano periodi di tempo, ad esempio anni, semestri, trimestri, mesi o giorni.|  
|Geography|Attributi che rappresentano informazioni geografiche, ad esempio città o CAP.|  
|Organization|Attributi che rappresentano informazioni sull'organizzazione, ad esempio dipendenti o filiali.|  
|BillOfMaterials|Attributi che rappresentano informazioni relative alle scorte o alla produzione, ad esempio elenchi di parti di prodotti.|  
|Accounts|Attributi che rappresentano un grafico dei conti per la creazione di rapporti finanziari.|  
|Customers|Attributi che rappresentano informazioni sui clienti o sui contatti.|  
|Products|Attributi che rappresentano informazioni sui prodotti.|  
|Scenario|Attributi che rappresentano informazioni di pianificazione o di analisi strategica.|  
|Quantitative|Attributi che rappresentano informazioni sulle quantità.|  
|Utilità|Attributi che rappresentano informazioni di vario tipo.|  
|Currency|Contiene i dati e i metadati della valuta.|  
|Rates|Attributi che rappresentano informazioni sui tassi valutari.|  
|Channel|Attributi che rappresentano informazioni sui canali.|  
|Promotion|Attributi che rappresentano informazioni sulle promozioni marketing.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nel seguente esempio viene illustrata una parte della rappresentazione CSDLBI versione 1.1 della tabella Geography utilizzata nel modello tabulare AdventureWorks. La colonna RowNumber è una colonna nascosta che viene generata automaticamente come identificatore di riga nei modelli tabulari e pertanto dispone dell'attributo Contents, `RowNumber`.  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente vengono illustrati gli elementi EntityType di CSDLBI versione 1.1 che rappresentano una parte della dimensione temporale del cubo Operations di Contoso.  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
