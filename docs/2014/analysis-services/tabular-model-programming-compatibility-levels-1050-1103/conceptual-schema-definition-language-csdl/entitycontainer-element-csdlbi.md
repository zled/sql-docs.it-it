---
title: Elemento EntityContainer (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: e328558e-16b0-4d4a-a79a-fdd3c9493595
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 59be912e2be44fca6e3fd49472f0884f9dfd0782
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126581"
---
# <a name="entitycontainer-element-csdlbi"></a>Elemento EntityContainer (CSDLBI)
  L'elemento EntityContainer rappresenta un tipo complesso, in base al tipo CSDL, EntityContainer, che definisce una raccolta di entità all'interno di un singolo modello di dati. In un'applicazione Business Intelligence, il modello di dati rappresentato da EntityContainer potrebbe contenere più tabelle con una colonna collegata tramite relazioni, nonché calcoli, misure e indicatori KPI. È concettualmente simile a un database o a un'origine dati.  
  
 L'elemento EntityContainer deve specificare ognuno dei tipi di entità inclusi nel modello di dati, comprese tabelle e relazioni. Le informazioni su queste entità del modello vengono specificate elencando le entità figlio del tipo, l'elemento Entità. Per altre informazioni, vedere [Elemento EntityType &#40;CSDLBI&#41;](entitytype-element-csdlbi.md).  
  
 Le proprietà come le regole di confronto e la lingua vengono definite al livello di EntityContainer, non sui singoli oggetti. Tuttavia, le colonne e gli attributi di testo all'interno del modello possono presentare didascalie o traduzioni in altre lingue.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono descritti gli elementi e gli attributi che definiscono EntityContainer.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|nome|Sì|Nome del modello di dati.|  
|Didascalia|no|Descrizione del database o del modello di dati.|  
|Impostazioni cultura|Sì|Stringa che contiene l'identificatore delle impostazioni locali (LCID) della richiesta.|  
|CompareOptions|Sì|Ordinamento specifico della lingua e opzioni di confronto delle stringhe per il modello.|  
|DirectQueryMode|no|Enumerazione che indica la modalità di query quando il modello utilizza la modalità DirectQuery.|  
|Elemento EntitySet|Sì|[Elemento EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)|  
|Elemento AssociationSet|no|[Elemento AssociationSet &#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
  
## <a name="compareoptions-element"></a>Elemento CompareOptions  
 L'attributo CompareOptions definisce le proprietà delle regole di confronto applicate al modello di dati. Le proprietà definite da CompareOptions derivano dalle impostazioni relative a ordinamento, distinzione dei caratteri kana e distinzione tra maiuscole e minuscole definite nel database di Analysis Services in fase di progettazione del modello. Nella tabella seguente vengono descritti i valori inclusi come parte dell'attributo CompareOptions.  
  
|valore|Description|  
|-----------|-----------------|  
|IgnoreCase|Valore booleano che indica se nei confronti di stringa si devono ignorare maiuscole e minuscole.|  
|IgnoreNonSpace|Valore booleano che indica se nei confronti di stringhe si devono ignorare i caratteri di unione senza spaziatura, ad esempio i segni diacritici.|  
|IgnoreKanaType|Valore booleano che indica se nei confronti di stringa si deve ignorare il tipo Kana.|  
|IgnoreWidth|Valore booleano che indica se nei confronti di stringa si deve ignorare la larghezza caratteri.|  
  
## <a name="directquerymode"></a>DirectQueryMode  
 **DirectQueryMode**  
  
 Il tipo semplice DirectQueryMode definisce il tipo di query utilizzato per impostazione predefinita quando il modello è abilitato per recuperare direttamente i dati da un'origine dati relazionale. Questa proprietà è applicabile solo ai modelli tabulari in esecuzione in modalità DirectQuery. Nella tabella seguente sono elencati i possibili valori dell'enumerazione della modalità DirectQuery.  
  
|valore|Description|  
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
 [Elemento EntitySet &#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
  
