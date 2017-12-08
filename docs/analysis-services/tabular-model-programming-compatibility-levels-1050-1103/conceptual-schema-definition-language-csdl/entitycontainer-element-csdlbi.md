---
title: Elemento EntityContainer (CSDLBI) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
applies_to: SQL Server 2016 Preview
ms.assetid: e328558e-16b0-4d4a-a79a-fdd3c9493595
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e5328a9c360fa4465e0bcf53bd0f017447c7c113
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="entitycontainer-element-csdlbi"></a>Elemento EntityContainer (CSDLBI)
  L'elemento EntityContainer rappresenta un tipo complesso, in base al tipo CSDL, EntityContainer, che definisce una raccolta di entità all'interno di un singolo modello di dati. In un'applicazione Business Intelligence, il modello di dati rappresentato da EntityContainer potrebbe contenere più tabelle con una colonna collegata tramite relazioni, nonché calcoli, misure e indicatori KPI. È concettualmente simile a un database o a un'origine dati.  
  
 L'elemento EntityContainer deve specificare ognuno dei tipi di entità inclusi nel modello di dati, comprese tabelle e relazioni. Le informazioni su queste entità del modello vengono specificate elencando le entità figlio del tipo, l'elemento Entità. Per altre informazioni, vedere [Elemento EntityType &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md).  
  
 Le proprietà come le regole di confronto e la lingua vengono definite al livello di EntityContainer, non sui singoli oggetti. Tuttavia, le colonne e gli attributi di testo all'interno del modello possono presentare didascalie o traduzioni in altre lingue.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono descritti gli elementi e gli attributi che definiscono EntityContainer.  
  
|Nome|Obbligatorio|Descrizione|  
|----------|-----------------|-----------------|  
|Nome|Sì|Nome del modello di dati.|  
|Caption|No|Descrizione del database o del modello di dati.|  
|Impostazioni cultura|Sì|Stringa che contiene l'identificatore delle impostazioni locali (LCID) della richiesta.|  
|CompareOptions|Sì|Ordinamento specifico della lingua e opzioni di confronto delle stringhe per il modello.|  
|DirectQueryMode|No|Enumerazione che indica la modalità di query quando il modello utilizza la modalità DirectQuery.|  
|Elemento EntitySet|Sì|[Elemento EntitySet &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)|  
|Elemento AssociationSet|No|[Elemento AssociationSet &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/associationset-element-csdlbi.md)|  
  
## <a name="compareoptions-element"></a>Elemento CompareOptions  
 L'attributo CompareOptions definisce le proprietà delle regole di confronto applicate al modello di dati. Le proprietà definite da CompareOptions derivano dalle impostazioni relative a ordinamento, distinzione dei caratteri kana e distinzione tra maiuscole e minuscole definite nel database di Analysis Services in fase di progettazione del modello. Nella tabella seguente vengono descritti i valori inclusi come parte dell'attributo CompareOptions.  
  
|Valore|Description|  
|-----------|-----------------|  
|IgnoreCase|Valore booleano che indica se nei confronti di stringa si devono ignorare maiuscole e minuscole.|  
|IgnoreNonSpace|Valore booleano che indica se nei confronti di stringhe si devono ignorare i caratteri di unione senza spaziatura, ad esempio i segni diacritici.|  
|IgnoreKanaType|Valore booleano che indica se nei confronti di stringa si deve ignorare il tipo Kana.|  
|IgnoreWidth|Valore booleano che indica se nei confronti di stringa si deve ignorare la larghezza caratteri.|  
  
## <a name="directquerymode"></a>DirectQueryMode  
 **DirectQueryMode**  
  
 Il tipo semplice DirectQueryMode definisce il tipo di query utilizzato per impostazione predefinita quando il modello è abilitato per recuperare direttamente i dati da un'origine dati relazionale. Questa proprietà è applicabile solo ai modelli tabulari in esecuzione in modalità DirectQuery. Nella tabella seguente sono elencati i possibili valori dell'enumerazione della modalità DirectQuery.  
  
|Valore|Description|  
|-----------|-----------------|  
|InMemory|Indica che le query eseguite sul modello utilizzano i dati nella cache.|  
|InMemoryWithDirectQuery|Indica che le query eseguite sul modello utilizzano per impostazione predefinita i dati dell'origine dati relazionale.|  
|DirectQueryWithInMemory|Indica che le query eseguite sul modello utilizzano per impostazione predefinita i dati nella cache.|  
|DirectQuery|Indica che le query eseguite sul modello utilizzano solo i dell'origine dati relazionale.|  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene rappresentata una parte del modello di dati tabulare AdventureWorks.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
       Name="DimEmployee"   
       EntityType="Sandbox.DimEmployee">  
   <bi:EntitySet />  
   </EntitySet>  
  
   <EntitySet   
     Name="DimProduct"   
       EntityType="Sandbox.DimProduct">  
    <bi:EntitySet />  
    </EntitySet>  
  
<bi:EntityContainer Caption="AWSimple" Culture="en-US">  
  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato un estratto del cubo Operations di Contoso.  
  
```  
  
<EntityContainer   
     Name="Sandbox">  
   <EntitySet   
      Name="Bike"   
      EntityType="Sandbox.Bike">  
    <bi:EntitySet Hidden="true" />  
   </EntitySet>  
…  
<bi:EntityContainer   
   Caption="CSDLTest"   
   Culture="en-US">  
<bi:CompareOptions   
   IgnoreCase="true" />  
</bi:EntityContainer>  
</EntityContainer>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EntitySet &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entityset-element-csdlbi.md)  
  
  
