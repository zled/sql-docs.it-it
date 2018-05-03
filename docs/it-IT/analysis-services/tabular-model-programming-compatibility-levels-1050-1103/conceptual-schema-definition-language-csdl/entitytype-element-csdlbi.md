---
title: Elemento EntityType (CSDLBI) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 076af372460c4df87b5e46376a9649c080090c02
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="entitytype-element-csdlbi"></a>Elemento EntityType (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Il **EntityType** elemento è un tipo complesso che rappresenta la struttura di un'entità di alto livello, ad esempio un cliente o un ordine, in un modello di dati. Il **bi: EntityType** elemento estende la definizione di [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) utilizzato nel [Entity Data Framework](http://msdn.microsoft.com/library/bb399567.aspx).  
  
 Un elemento EntityType deve essere specificato per ognuna delle entità incluse nel modello di dati. I sottoelementi di EntityType descrivono le colonne e le misure nella tabella. Le relazioni tra tabelle vengono incluse nel **EntityContainer**.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente sono elencati gli elementi e attributi che definiscono il **EntityType** elemento. Vedere anche gli attributi applicabili al [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) elemento.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Sommario|No|Stringa contenente i possibili tipi di dati in una colonna. Il valore è derivato dal valore di DimensionAttributeTypeEnumType nel modello di dati.<br /><br /> Se il valore di DimensionAttributeTypeEnumType è "ExtendedType", il valore del contenuto è derivato dall'elemento ExtendedType di DimensionAttribute. Il client non è necessario per rispondere a tali valori.|  
|DefaultDetails|No|Elenco di riferimenti a proprietà che rappresentano il set di colonne nella tabella.<br /><br /> Vedere [elemento DefaultDetails & #40; CSDLBI & #41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/defaultdetails-element-csdlbi.md).|  
|DefaultImage|No|Riferimento a una colonna contenente l'immagine che illustra l'entità.<br /><br /> Nei modelli multidimensionali, questo elemento corrisponde a un attributo binario dell'attributo della dimensione. Se questo attributo è presente, l'elemento deve contenere un solo elemento MemberRef.<br /><br /> Vedere [elemento MemberRef & #40; CSDLBI & #41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DefaultMeasure|No|Riferimento a una misura dell'entità che deve essere utilizzato come impostazione predefinita durante l'esecuzione dei calcoli dell'entità. Se omesso, il valore predefinito è SUM.<br /><br /> Vedere [elemento MemberRef & #40; CSDLBI & #41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/memberref-element-csdlbi.md).|  
|DisplayKey|No|Elenco di riferimenti a colonne o estremità del ruolo che costituiscono un identificatore sicuro che identifica in modo univoco un'istanza di entità.<br /><br /> Vedere [elemento DisplayKey & #40; CSDLBI & #41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/displaykey-element-csdlbi.md).|  
|Gerarchia|No|Elenco delle gerarchie nel modello.<br /><br /> Vedere [gerarchia elemento & #40; CSDLBI & #41; ](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).|  
|ReferenceName|Sì|Identificatore che può essere utilizzato per fare riferimento a questa entità in una query DAX (Data Analysis Expressions).<br /><br /> Se tale attributo non è presente, viene utilizzato il nome completo del campo dell'entità.|  
|SortMembers|No|Elenco di proprietà utilizzato per l'ordinamento. L'attributo SortDirection indica se l'ordinamento è crescente o decrescente.|  
  
## <a name="contents-element"></a>Elemento Contents  
 Il **contenuto** elemento è un tipo semplice che descrive il tipo di dati nell'entità.  
  
 Il contenuto dell'entità (colonna) può essere uno dei valori seguenti:  
  
|Value|Description|  
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
 **Tabulare**  
  
 Nel seguente esempio viene illustrata una parte della rappresentazione CSDLBI versione 1.1 della tabella Geography utilizzata nel modello tabulare AdventureWorks. La colonna RowNumber è una colonna nascosta che viene generata automaticamente come un identificatore di riga nei modelli tabulari e pertanto dispone dell'attributo Contents, **RowNumber**.  
  
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
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
