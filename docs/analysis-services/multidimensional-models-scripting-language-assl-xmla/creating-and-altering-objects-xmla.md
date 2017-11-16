---
title: Creazione e modifica di oggetti (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- objects [XML for Analysis]
- subordinate objects [XML for Analysis]
- XML for Analysis, objects
- modifying objects
- removing objects
- deleting objects
- XMLA, objects
ms.assetid: a2080867-e130-440c-92eb-f768869f34a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4b96c43a4004e69969af12d83798f9fe76fc801c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="creating-and-altering-objects-xmla"></a>Creazione e modifica di oggetti (XMLA)
  Gli oggetti principali possono essere creati, modificati ed eliminati in modo indipendente. Di seguito vengono elencati gli oggetti principali:  
  
-   Server  
  
-   Database  
  
-   Dimensioni  
  
-   Cubi  
  
-   Gruppi di misure  
  
-   Partizioni  
  
-   Prospettive  
  
-   Modelli di data mining  
  
-   Ruoli  
  
-   Comandi associati a un server o a un database  
  
-   Origini dei dati  
  
 Utilizzare il [crea](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md) comando per creare un oggetto principale in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) comando per modificare un oggetto principale esistente in un'istanza. Entrambi i comandi vengono eseguiti utilizzando il [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
## <a name="creating-objects"></a>Creazione di oggetti  
 Quando si creano oggetti usando il **crea** (metodo), è necessario innanzitutto identificare l'oggetto padre che contiene il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetto da creare. Identificare l'oggetto padre, fornendo un riferimento all'oggetto nel [ParentObject](../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) proprietà del **crea** comando. Ogni riferimento all'oggetto contiene gli identificatori di oggetto necessari per identificare in modo univoco l'oggetto padre per il **crea** comando. Per ulteriori informazioni sui riferimenti a oggetti, vedere [definizione e identificazione di oggetti &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Si supponga ad esempio che sia necessario fornire un riferimento a un oggetto per un cubo per creare un nuovo gruppo di misure per il cubo stesso. Il riferimento all'oggetto per il cubo nel **ParentObject** proprietà contiene un identificatore del database sia un identificatore del cubo, come l'identificatore del cubo stesso potrebbe essere usato in un database diverso.  
  
 Il [ObjectDefinition](../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md) elemento contiene elementi di Analysis Services Scripting Language (ASSL) che definiscono l'oggetto principale da creare. Per ulteriori informazioni su ASSL, vedere [allo sviluppo con Analysis Services Scripting Language &#40; ASSL &#41; ](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Se si imposta la **AllowOverwrite** attributo del **crea** comando su true, è possibile sovrascrivere un oggetto principale esistente con l'identificatore specificato. In caso contrario, se un oggetto principale con l'identificatore specificato esiste già nell'oggetto padre si verifica un errore.  
  
 Per ulteriori informazioni sul **crea** command, vedere [elemento Create &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md).  
  
### <a name="creating-session-objects"></a>Creazione di oggetti di sessione  
 Gli oggetti di sessione sono oggetti temporanei disponibili solo nella sessione esplicita o implicita utilizzata da un'applicazione client che vengono eliminati quando la sessione è terminata. È possibile creare oggetti di sessione impostando il **ambito** attributo del **crea** comando *sessione*.  
  
> [!NOTE]  
>  Quando si utilizza il *sessione* impostazione, il **ObjectDefinition** elemento può contenere solo [dimensione](../../analysis-services/scripting/objects/dimension-element-assl.md), [cubo](../../analysis-services/scripting/objects/cube-element-assl.md), o [ MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) elementi ASSL.  
  
## <a name="altering-objects"></a>Modifica di oggetti  
 Quando si modificano oggetti tramite il **Alter** (metodo), è necessario innanzitutto identificare l'oggetto da modificare, fornendo un riferimento all'oggetto nel [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà del **Alter**comando. Ogni riferimento all'oggetto contiene gli identificatori di oggetto necessari per identificare in modo univoco l'oggetto per il **Alter** comando. Per ulteriori informazioni sui riferimenti a oggetti, vedere [definizione e identificazione di oggetti &#40; XMLA &#41; ](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md).  
  
 Si supponga ad esempio che sia necessario fornire un riferimento a un oggetto per un cubo per modificarne la struttura. Il riferimento all'oggetto per il cubo nel **oggetto** proprietà contiene un identificatore del database sia un identificatore del cubo, come l'identificatore del cubo stesso potrebbe essere usato in un database diverso.  
  
 Il **ObjectDefinition** elemento contiene elementi ASSL che definiscono l'oggetto principale da modificare. Per ulteriori informazioni su ASSL, vedere [allo sviluppo con Analysis Services Scripting Language &#40; ASSL &#41; ](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
 Se si imposta la **AllowCreate** attributo del **Alter** comando su true, è possibile creare l'oggetto principale specificato se l'oggetto non esiste. In caso contrario, se un oggetto principale specificato non esiste si verifica un errore.  
  
### <a name="using-the-objectexpansion-attribute"></a>Utilizzo dell'attributo ObjectExpansion  
 Se si modificano solo le proprietà dell'oggetto principale senza ridefinire gli oggetti secondari contenuti in quello principale, è possibile impostare il **ObjectExpansion** attributo del **Alter** comando *ObjectProperties*. Il **ObjectDefinition** proprietà quindi solo deve contenere gli elementi per le proprietà dell'oggetto principale e **Alter** comando lascia gli oggetti secondari associati all'oggetto principale.  
  
 Per ridefinire gli oggetti secondari per un oggetto principale, è necessario impostare il **ObjectExpansion** attributo *ExpandFull* e la definizione dell'oggetto deve includere tutti gli oggetti secondari contenuti in quello principale. Se il **ObjectDefinition** proprietà del **Alter** comando non include un oggetto secondario contenuto dall'oggetto principale in modo esplicito, viene eliminato l'oggetto secondario non è stato incluso.  
  
### <a name="altering-session-objects"></a>Modifica di oggetti di sessione  
 Per modificare gli oggetti di sessione creati il **crea** comando, impostare il **ambito** attributo del **Alter** comando *sessione*.  
  
> [!NOTE]  
>  Quando si utilizza il *sessione* impostazione, il **ObjectDefinition** elemento può contenere solo [dimensione](../../analysis-services/scripting/objects/dimension-element-assl.md), [cubo](../../analysis-services/scripting/objects/cube-element-assl.md), o [ MiningModel](../../analysis-services/scripting/objects/miningmodel-element-assl.md) elementi ASSL.  
  
## <a name="creating-or-altering-subordinate-objects"></a>Creazione o modifica di oggetti subordinati  
 Sebbene un **crea** o **Alter** comando Crea o modifica di un solo oggetto principale in primo piano, l'oggetto principale creato o modificato può contenere definizioni all'interno di inclusione  **ObjectDefinition** proprietà per altri oggetti principali e secondari subordinati. Ad esempio, se si definisce un cubo, specificare il database padre in **ParentObject**e nella definizione del cubo in **ObjectDefinition** è possibile definire gruppi di misure per il cubo e all'interno di misure gruppi è possibile definire partizioni per ogni gruppo di misure. Un oggetto secondario può essere definito solo sotto l'oggetto principale che lo contiene. Per ulteriori informazioni sugli oggetti principali e secondari, vedere [gli oggetti di Database &#40; Analysis Services - dati multidimensionali &#41; ](../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 L'esempio seguente crea un'origine dati relazionale che fa riferimento il [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
### <a name="code"></a>Codice  
  
```  
<Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    </ParentObject>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ImpersonationInfo>  
                <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
            </ImpersonationInfo>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT0S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Create>  
```  
  
### <a name="description"></a>Description  
 Nell'esempio seguente viene modificata l'origine dati relazionale creata nell'esempio precedente per impostare il timeout per la query per l'origine dati su 30 secondi.  
  
### <a name="code"></a>Codice  
  
```  
<Alter ObjectExpansion="ObjectProperties" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DataSourceID>AdventureWorksDW2012</DataSourceID>  
    </Object>  
    <ObjectDefinition>  
        <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
            <ID>AdventureWorksDW2012</ID>  
            <Name>AdventureWorksDW2012</Name>  
            <ConnectionString>Data Source=fr-dwk-02;Initial Catalog=AdventureWorksDW2008R2;Integrated Security=True</ConnectionString>  
            <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
            <Timeout>PT30S</Timeout>  
        </DataSource>  
    </ObjectDefinition>  
</Alter>  
```  
  
### <a name="comments"></a>Commenti  
 Il **ObjectExpansion** attributo del **Alter** comando è stato impostato su *ObjectProperties*. Questa impostazione consente di [ImpersonationInfo](../../analysis-services/scripting/properties/impersonationinfo-element-assl.md) elemento, un oggetto secondario, da escludere dall'origine dati definita **ObjectDefinition**. Le impostazioni di rappresentazione per tale origine dati rimangono pertanto configurate sull'account del servizio, come specificato nel primo esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [Esegui metodo &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Lo sviluppo con Analysis Services Scripting Language &#40; ASSL &#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

