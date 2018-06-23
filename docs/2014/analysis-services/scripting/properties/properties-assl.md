---
title: Proprietà (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- properties [Analysis Services Scripting Language]
- Analysis Services Scripting Language, properties
- ASSL, properties
ms.assetid: 9a38cdc9-a210-421a-90e9-6391876765fa
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 72ec08342256fecbd63c791b6db6e343479bca65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069302"
---
# <a name="properties-assl"></a>Proprietà (ASSL)
  Questa sezione di riferimento contiene informazioni sulla sintassi e sull'utilizzo per ogni elemento che si comporta come una proprietà dell'oggetto nello schema ASSL (Analysis Services Scripting Language).  
  
 Anche se lo schema ASSL contiene solo elementi XML, dal punto di vista di uno sviluppatore, gli elementi descritti in questa sezione corrispondono a proprietà che descrivono oggetti.  
  
 Le Proprietà sono elementi al livello foglia nello schema ASSL e non hanno elementi figlio o elementi che corrispondono a proprietà ad esse relative.  
  
 In alcuni casi, un elemento a livello foglia nello schema che può sembrare una proprietà viene classificato come oggetto perché il tipo dell'elemento è un tipo oggetto. Ad esempio, `Source` di un oggetto `Dimension` è di tipo `DimensionBinding`.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Accedere a elemento di &#40;ASSL&#41;](access-element-assl.md)|Indica il livello di accesso concesso a un [CellPermission](../objects/cellpermission-element-assl.md) elemento.|  
|[Elemento dell'account &#40;ImpersonationInfo&#41; &#40;ASSL&#41;](account-element-impersonationinfo-assl.md)|Contiene il nome dell'account utente per il [ImpersonationInfo](../data-type/impersonationinfo-data-type-assl.md) tipo di dati.|  
|[Elemento AccountType &#40;ASSL&#41;](accounttype-element-assl.md)|Contiene il nome di un tipo di conto definito in un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento ActionID &#40;ASSL&#41;](id-element-assl.md)|Contiene il nome di un [azione](../objects/action-element-assl.md) elemento definito in un [cubo](../objects/cube-element-assl.md) elemento che viene reso disponibile in un [prospettiva](../objects/perspective-element-assl.md) elemento come un [PerspectiveAction](../data-type/action-data-type-assl.md) elemento.|  
|[Elemento Administer &#40;ASSL&#41;](administer-element-assl.md)|Indica se l'autorizzazione associata include il diritto di amministrare un elemento `Database`.|  
|[Elemento AggregateFunction &#40;ASSL&#41;](aggregatefunction-element-assl.md)|Definisce il tipo di funzione di aggregazione usata da un [misure](../objects/measure-element-assl.md) elemento.|  
|[Elemento AggregationDesignID &#40;ASSL&#41;](aggregationdesignid-element-assl.md)|Identifica la [AggregationDesign](../objects/aggregationdesign-element-assl.md) associato all'elemento il [partizione](../objects/partition-element-assl.md) elemento.|  
|[Elemento AggregationFunction &#40;ASSL&#41;](aggregationfunction-element-assl.md)|Contiene la funzione di aggregazione da usare per il tipo di account.|  
|[Elemento AggregationID &#40;ASSL&#41;](aggregationid-element-assl.md)|Identifica la definizione di aggregazione dall'elemento `AggregationDesign` usato per creare l'istanza di aggregazione.|  
|[Elemento AggregationInstanceSource &#40;ASSL&#41;](aggregationinstancesource-element-assl.md)|Identifica l'origine di dati per istanze di aggregazione definite dall'utente associate a un elemento `Partition`.|  
|[Elemento AggregationPrefix &#40;ASSL&#41;](aggregationprefix-element-assl.md)|Definisce il prefisso comune da usare per i nomi di aggregazione in tutto l'elemento padre associato.|  
|[Elemento AggregationStorage &#40;ASSL&#41;](aggregationstorage-element-assl.md)|Identifica il metodo di archiviazione per le aggregazioni.|  
|[Elemento AggregationType &#40;ASSL&#41;](aggregationtype-element-assl.md)|Definisce il tipo di aggregazione archiviata per l’elemento `Partition`.|  
|[Elemento AggregationUsage &#40;ASSL&#41;](aggregationusage-element-assl.md)|I controlli come la finestra di progettazione delle aggregazioni in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] progettare aggregazioni.|  
|[Elemento Algorithm &#40;ASSL&#41;](algorithm-element-assl.md)|Definisce l'algoritmo utilizzato da un [MiningModel](../objects/miningmodel-element-assl.md) elemento.|  
|[Elemento alias &#40;ASSL&#41;](alias-element-assl.md)|Definisce un alias per un [Account](../objects/account-element-assl.md) elemento.|  
|[Elemento AllMemberAggregationUsage &#40;ASSL&#41;](allmemberaggregationusage-element-assl.md)|Controlla il modo in cui vengono progettate le aggregazioni con Progettazione aggregazioni in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento AllMemberName &#40;ASSL&#41;](name-element-assl.md)|Contiene la didascalia, specificata nella lingua predefinita del membro totale di un [gerarchia](../objects/hierarchy-element-assl.md) elemento.|  
|[Elemento AllowBrowsing &#40;ASSL&#41;](allowbrowsing-element-assl.md)|Definisce se i membri di un [ruolo](../objects/role-element-assl.md) elemento hanno l'autorizzazione per visualizzare un `MiningModel` elemento.|  
|[Elemento AllowDrillThrough &#40;ASSL&#41;](allowdrillthrough-element-assl.md)|Determina se il drill-through è permesso sull'elemento padre.|  
|[Elemento AllowDuplicateNames &#40;ASSL&#41;](allowduplicatenames-element-assl.md)|Determina se nell’elemento `Hierarchy` è possibile usare nomi duplicati.|  
|[Elemento AllowedSet &#40;ASSL&#41;](allowedset-element-assl.md)|Contiene un'espressione set che definisce il set di autorizzazioni consentite per un elemento `Role` su un attributo.|  
|[Elemento dell'applicazione &#40;ASSL&#41;](application-element-assl.md)|Identifica l'applicazione associata a un elemento `Action`.|  
|[Elemento AssociatedMeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Contiene l'identificatore (ID) della [MeasureGroup](../objects/group-element-assl.md) associato all'elemento un [CalculationProperty](../objects/calculationproperty-element-assl.md) elemento o un [Kpi](../objects/kpi-element-assl.md) elemento.|  
|[Elemento AttributeAllMemberName &#40;ASSL&#41;](attributeallmembername-element-assl.md)|Contiene la didascalia, specificata nella lingua predefinita, del membro Totale della dimensione.|  
|[Elemento AttributeHierarchyDisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Identifica la cartella in cui viene visualizzata la gerarchia dell'attributo associata.|  
|[Elemento AttributeHierarchyEnabled &#40;ASSL&#41;](enabled-element-assl.md)|Determina se viene abilitata una gerarchia dell'attributo per l'attributo.|  
|[Elemento AttributeHierarchyOptimizedState &#40;ASSL&#41;](state-element-assl.md)|Determina il livello di ottimizzazione applicato alla gerarchia dell'attributo.|  
|[Elemento AttributeHierarchyOrdered &#40;ASSL&#41;](attributehierarchyordered-element-assl.md)|Determina se la gerarchia dell'attributo associata viene ordinata.|  
|[Elemento AttributeHierarchyVisible &#40;ASSL&#41;](visible-element-assl.md)|Determina se la gerarchia dell'attributo è visibile alle applicazioni client.|  
|[Elemento AttributeID &#40;ASSL&#41;](attributeid-element-assl.md)|Contiene l’ID dell'attributo associato all'elemento padre.|  
|[Elemento di controllo &#40;ASSL&#41;](audit-element-assl.md)|Specifica che un [traccia](../objects/trace-element-assl.md) elemento non è possibile eliminare qualsiasi evento, anche se ciò comporterà una riduzione delle prestazioni nel server.|  
|[Elemento AutoRestart &#40;ASSL&#41;](autorestart-element-assl.md)|Determina se un elemento `Trace` deve riavviarsi automaticamente quando il servizio [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] si arresta e riavvia.|  
|[Elemento BackColor &#40;ASSL&#41;](backcolor-element-assl.md)|Descrive le caratteristiche di visualizzazione dell'elemento padre correlate al colore.|  
|[Elemento CacheMode &#40;ASSL&#41;](cachemode-element-assl.md)|Determina il meccanismo di memorizzazione nella cache usato per i dati di training recuperato durante l'elaborazione di una struttura di data mining.|  
|[Elemento CalculationReference &#40;ASSL&#41;](calculationreference-element-assl.md)|Contiene il nome del set denominato o della cella calcolata in riferimento all'elemento `CalculationProperty`.|  
|[Elemento CalculationType &#40;ASSL&#41;](calculationtype-element-assl.md)|Descrive il tipo di calcolo definito nell'elemento `CalculationProperty` associato.|  
|[Elemento CalendarEndDate &#40;ASSL&#41;](calendarenddate-element-assl.md)|Definisce la data di fine del periodo di calendario per un [TimeBinding](../data-type/binding-data-type-assl.md) elemento.|  
|[Elemento CalendarLanguage &#40;ASSL&#41;](language-element-assl.md)|Definisce il linguaggio del calendario usato per l'elemento `TimeBinding`.|  
|[Elemento CalendarStartDate &#40;ASSL&#41;](calendarstartdate-element-assl.md)|Definisce la data di inizio del periodo di calendario per l’elemento `TimeBinding`.|  
|[Elemento della barra del titolo &#40;ASSL&#41;](caption-element-assl.md)|Contiene la didascalia per l'elemento padre associato.|  
|[Elemento CaptionIsMdx &#40;ASSL&#41;](captionismdx-element-assl.md)|Definisce se la didascalia per l'elemento `Action` è un'espressione Espressioni MDX (MDX).|  
|[Elemento Cardinality &#40;ASSL&#41;](cardinality-element-assl.md)|Indica la cardinalità della relazione descritta da un [AttributeRelationship](../objects/attributerelationship-element-assl.md) oppure [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md).|  
|[Elemento CaseCubeDimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Contiene l’ID della dimensione del cubo che correla la dimensione di data mining al gruppo di misure.|  
|[Elemento ClassifiedColumnID &#40;ASSL&#41;](classifiedcolumnid-element-assl.md)|Contiene l'ID di una colonna correlata classificata dal [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) elemento.|  
|[Elemento Collation &#40;ASSL&#41;](collation-element-assl.md)|Determina le regole di confronto usate dall’elemento padre.|  
|[Elemento ColumnID &#40;ColumnBinding&#41; &#40;ASSL&#41;](columnid-element-columnbinding-assl.md)|Contiene l’ID della colonna all'interno della tabella alla quale è associato l'elemento dei dati.|  
|[Elemento ColumnID &#40;EventColumn&#41; &#40;ASSL&#41;](columnid-element-eventcolumn-assl.md)|Contiene l’ID della colonna di informazioni da acquisire come parte di un evento per un elemento `Trace`.|  
|[Elemento di condizione &#40;ASSL&#41;](condition-element-assl.md)|Contiene un'espressione MDX che determina se l'elemento padre `Action` si applica alla destinazione.|  
|[Elemento ConnectionString &#40;ASSL&#41;](connectionstring-element-assl.md)|Contiene la stringa di connessione crittografata per un [DataSource](../objects/datasource-element-assl.md) elemento.|  
|[Elemento ConnectionStringSecurity &#40;ASSL&#41;](connectionstringsecurity-element-assl.md)|Specifica se la password dell'utente viene rimossa dalla stringa di connessione all'origine dati per scopi di sicurezza.|  
|[Elemento di contenuto &#40;ASSL&#41;](content-element-assl.md)|Viene descritto il contenuto della colonna nella [MiningStructure](../objects/miningstructure-element-assl.md) elemento.|  
|[Elemento CreatedTimestamp &#40;ASSL&#41;](createdtimestamp-element-assl.md)|Contiene il timestamp di creazione di sola lettura dell'elemento padre.|  
|[Elemento CubeDimensionID &#40;ASSL&#41;](cubedimensionid-element-assl.md)|Identifica la [CubeDimension](../data-type/cubedimension-data-type-assl.md) elemento associato all'elemento padre.|  
|[Elemento CubeID &#40;ASSL&#41;](cubeid-element-assl.md)|Identifica la `Cube` elemento associato a un [associazione](../data-type/binding-data-type-assl.md) elemento.|  
|[Elemento CurrentStorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Determina la modalità di archiviazione corrente per l'elemento padre.|  
|[Elemento CurrentTimeMember &#40;ASSL&#41;](../objects/member-element-assl.md)|Definisce il membro corrente di una dimensione temporale associato a un elemento `Kpi`.|  
|[Elemento DataAggregation &#40;ASSL&#41;](../objects/aggregation-element-assl.md)|Determina se l’istanza può aggregare i dati persistenti o quelli memorizzati nella cache per il `MeasureGroup`.|  
|[Elemento DatabaseID &#40;ASSL&#41;](databaseid-element-assl.md)|Identifica l'elemento `Database` associato a un elemento out-of-line `Binding`.|  
|[Elemento DataSize &#40;ASSL&#41;](datasize-element-assl.md)|Contiene la dimensione in byte di un [DataItem](../data-type/dataitem-data-type-assl.md) elemento.|  
|[Elemento DataSourceID &#40;ASSL&#41;](datasourceid-element-assl.md)|Identifica l'elemento `DataSource` associato all’elemento padre.|  
|[Elemento DataSourceImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Contiene le informazioni usate per determinare il comportamento della rappresentazione in caso di connessione all'origine dati per un elemento `Database`.|  
|[Elemento Datasourceviews &#40;ASSL&#41;](datasourceviewid-element-assl.md)|Identifica la [DataSourceView](../objects/datasourceview-element-assl.md) associato all'elemento di `Binding` elemento padre.|  
|[Elemento DataType &#40;ASSL&#41;](datatype-element-assl.md)|Definisce il tipo di dati dell'elemento associato.|  
|[Elemento DbSchemaName &#40;ASSL&#41;](dbschemaname-element-assl.md)|Contiene il nome dello schema utilizzato dall'elemento padre nella tabella identificata dal [DbTableName](dbtablename-element-assl.md) elemento.|  
|[Elemento DbTableName &#40;ASSL&#41;](dbtablename-element-assl.md)|Contiene il nome della tabella alla quale l'elemento padre è associato.|  
|[Predefinito l'elemento &#40;ASSL&#41;](default-element-assl.md)|Determina se `DrillThroughAction` è l'azione drill-through predefinita.|  
|[Elemento DefaultMeasure &#40;ASSL&#41;](defaultmeasure-element-assl.md)|Contiene un'espressione MDX (Multidimensional Expression) che definisce la misura predefinita per `Cube` o per l’elemento `Perspective`.|  
|[Elemento DefaultMember &#40;ASSL&#41;](defaultmember-element-assl.md)|Contiene un’espressione MDX che identifica il membro predefinito dell’elemento padre.|  
|[Elemento DefaultScript &#40;ASSL&#41;](defaultscript-element-assl.md)|Identifica il valore predefinito [MdxScript](../objects/mdxscript-element-assl.md) elemento il [MdxScripts](../collections/mdxscripts-element-assl.md) insieme.|  
|[Elemento DefaultValue &#40;ASSL&#41;](value-element-assl.md)|Contiene il valore predefinito di sola lettura dell'oggetto associato [ServerProperty](../objects/serverproperty-element-assl.md) elemento.|  
|[Elemento DeniedSet &#40;ASSL&#41;](deniedset-element-assl.md)|Contiene un'espressione set che definisce l'elenco di autorizzazioni negate sull'attributo associato.|  
|[Elemento DependsOnDimensionID &#40;ASSL&#41;](dependsondimensionid-element-assl.md)|Contiene l'ID di un'altra dimensione da cui dipende la dimensione padre.|  
|[Elemento Description &#40;ASSL&#41;](description-element-assl.md)|Contiene la descrizione dell'elemento padre.|  
|[Elemento DimensionID &#40;ASSL&#41;](dimensionid-element-assl.md)|Contiene l’ID della dimensione.|  
|[Elemento DiscretizationBucketCount &#40;ASSL&#41;](discretizationbucketcount-element-assl.md)|Contiene il numero di bucket per la discretizzazione.|  
|[Elemento DiscretizationMethod &#40;ASSL&#41;](discretizationmethod-element-assl.md)|Definisce il metodo da usare per la discretizzazione.|  
|[Elemento DisplayFlag &#40;ASSL&#41;](displayflag-element-assl.md)|Contiene un hint di sola lettura che indica se i componenti dell'interfaccia utente devono visualizzare l'elemento `ServerProperty` associato.|  
|[Elemento DisplayFolder &#40;ASSL&#41;](displayfolder-element-assl.md)|Specifica la cartella nella quale elencare l'elemento padre. Le applicazioni [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per sviluppatori e amministratori possono supportare l'utilizzo delle cartelle di visualizzazione per suddividere più elementi in categorie.|  
|[Elemento di distribuzione &#40;ASSL&#41;](distribution-element-assl.md)|Contiene un valore specifico del provider che descrive in che modo i valori scalari vengono distribuiti in una colonna di un elemento `MiningStructure`.|  
|[Elemento Edition &#40;ASSL&#41;](edition-element-assl.md)|Contiene l'edizione di sola lettura dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rappresentato dal [Server](../objects/server-element-assl.md) elemento.|  
|[Abilitato l'elemento &#40;ASSL&#41;](enabled-element-assl.md)|Indica se l'elemento padre è abilitato.|  
|[Elemento EndOfData &#40;ASSL&#41;](../objects/data-element-assl.md)|Indica la fine dei dati ricevuti da un [PushedDataSource](../data-type/datasource-data-type-assl.md) elemento.|  
|[Elemento EstimatedCount &#40;ASSL&#41;](estimatedcount-element-assl.md)|Contiene il numero stimato di membri per un attributo.|  
|[Elemento EstimatedPerformanceGain &#40;ASSL&#41;](estimatedperformancegain-element-assl.md)|Contiene la percentuale di sola lettura di miglioramento delle prestazioni stimato per la partizione.|  
|[Elemento EstimatedRows &#40;ASSL&#41;](estimatedrows-element-assl.md)|Contiene il numero stimato di righe rappresentate dall'elemento padre.|  
|[Elemento EstimatedSize &#40;ASSL&#41;](estimatedsize-element-assl.md)|Contiene la dimensione di sola lettura stimata, in byte, dell'elemento padre.|  
|[Elemento EventID &#40;ASSL&#41;](eventid-element-assl.md)|Identifica in modo univoco un [evento](../objects/event-element-assl.md) elemento da acquisire come parte di un `Trace` elemento.|  
|[Elemento dell'espressione &#40;ASSL&#41;](expression-element-assl.md)|Contiene un'espressione MDX che definisce il contenuto dell'elemento padre.|  
|[Elemento Filter &#40;associazione&#41; &#40;ASSL&#41;](filter-element-binding-assl.md)|Contiene un'espressione MDX che filtra il contenuto dell'elemento padre.|  
|[Elemento Filter &#40;traccia&#41; &#40;ASSL&#41;](filter-element-trace-assl.md)|Contiene un frammento del documento XML che descrive il filtro `Trace`.|  
|[Elemento FirstDayOfWeek &#40;ASSL&#41;](firstdayofweek-element-assl.md)|Definisce il primo giorno della settimana per un elemento `TimeBinding`.|  
|[Elemento FiscalFirstDayOfMonth &#40;ASSL&#41;](fiscalfirstdayofmonth-element-assl.md)|Definisce il primo giorno del mese fiscale per un elemento `TimeBinding`.|  
|[Elemento FiscalFirstMonth &#40;ASSL&#41;](fiscalfirstmonth-element-assl.md)|Definisce il primo mese del periodo fiscale per un elemento `TimeBinding`.|  
|[Elemento FiscalYearName &#40;ASSL&#41;](fiscalyearname-element-assl.md)|Definisce la convenzione di denominazione per il nome dell'anno fiscale per un elemento `TimeBinding`.|  
|[Elemento FontFlags &#40;ASSL&#41;](fontflags-element-assl.md)|Descrive le caratteristiche di visualizzazione correlate al tipo di carattere dell'elemento padre di `CalculationProperty` o `Measure`.|  
|[Elemento FontName &#40;ASSL&#41;](fontname-element-assl.md)|Descrive le caratteristiche di visualizzazione correlate al tipo di carattere dell'elemento padre di `CalculationProperty` o `Measure`.|  
|[Elemento FontSize &#40;ASSL&#41;](fontsize-element-assl.md)|Descrive le caratteristiche di visualizzazione correlate al tipo di carattere dell'elemento padre di `CalculationProperty` o `Measure`.|  
|[Elemento ForceRebuildInterval &#40;ASSL&#41;](forcerebuildinterval-element-assl.md)|Determina la quantità di tempo, da quando diventa disponibile un'immagine OLAP (MOLAP) multidimensionale aggiornata, dopo il quale viene avviata la creazione di un'immagine MOLAP in modo incondizionato.|  
|[Elemento ForeColor &#40;ASSL&#41;](forecolor-element-assl.md)|Descrive le caratteristiche di visualizzazione correlate al colore dell'elemento padre di `CalculationProperty` o `Measure`.|  
|[Elemento di formato &#40;ASSL&#41;](format-element-assl.md)|Contiene il formato obbligatorio dell'elemento `DataItem`.|  
|[Elemento FormatString &#40;ASSL&#41;](formatstring-element-assl.md)|Descrive il formato di visualizzazione per un elemento `CalculationProperty` o un elemento `Measure`.|  
|[Elemento Goal &#40;ASSL&#41;](goal-element-assl.md)|Identifica l'obiettivo desiderato in un elemento `Kpi`.|  
|[Elemento GranularityAttributeID &#40;ASSL&#41;](granularityattributeid-element-assl.md)|Contiene l'ID dell'attributo associato al padre [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md) tipo di dati.|  
|[Elemento HideMemberIf &#40;ASSL&#41;](hidememberif-element-assl.md)|Indica se e quando un membro di un livello deve essere nascosto per le applicazioni client.|  
|[Elemento HierarchyID &#40;ASSL&#41;](hierarchyid-element-assl.md)|Contiene l'ID per un [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md), o [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md) elemento.|  
|[Elemento HierarchyUniqueNameStyle &#40;ASSL&#41;](hierarchyuniquenamestyle-element-assl.md)|Determina il modo in cui vengono generati i nomi univoci delle gerarchie contenute all'interno di `CubeDimension`.|  
|[ID elemento &#40;ASSL&#41;](id-element-assl.md)|Contiene l'identificatore univoco (ID) dell’elemento padre.|  
|[Elemento IgnoreUnrelatedDimensions &#40;ASSL&#41;](../collections/dimensions-element-assl.md)|Determina se le dimensioni non correlate devono essere forzate al livello principale in caso di inclusione in una query di membri di dimensioni non correlate al gruppo di misure.|  
|[Elemento ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-element-assl.md)|Contiene le informazioni usate per determinare il comportamento della rappresentazione quando si accede a un assembly o lo si esegue.|  
|[Elemento ImpersonationInfoSecurity &#40;ASSL&#41;](impersonationinfosecurity-element-assl.md)|Contiene un valore di sola lettura che indica se viene apportata qualche modifica alle credenziali di sicurezza fornite nel tipo di dati `ImpersonationInfo`.|  
|[Elemento ImpersonationMode &#40;ASSL&#41;](impersonationmode-element-assl.md)|Contiene un valore che indica il metodo di rappresentazione per gli elementi derivato dal tipo di dati `ImpersonationInfo`.|  
|[Elemento InstanceSelection &#40;ASSL&#41;](instanceselection-element-assl.md)|Fornisce un hint alle applicazioni client sul modo in cui deve venire visualizzato un elenco di elementi, in base al numero previsto di elementi presenti nell'elenco.|  
|[Elemento IntermediateCubeDimensionID &#40;ASSL&#41;](intermediatecubedimensionid-element-assl.md)|Contiene l’ID della dimensione che correla una dimensione di riferimento a un gruppo di misure.|  
|[Elemento IntermediateGranularityAttributeID &#40;ASSL&#41;](intermediategranularityattributeid-element-assl.md)|Contiene l’ID dell'attributo di granularità nella dimensione del cubo intermedia usata per correlare una dimensione di riferimento a una dimensione intermedia.|  
|[Elemento InvalidXmlCharacters &#40;ASSL&#41;](invalidxmlcharacters-element-assl.md)|Specifica il metodo di gestione per i caratteri di XML nei dati di origine che non sono validi.|  
|[Elemento Invocation &#40;ASSL&#41;](invocation-element-assl.md)|Specifica come un `Action` deve essere richiamato.|  
|[Elemento IsAggregatable &#40;ASSL&#41;](isaggregatable-element-assl.md)|Specifica se i valori del [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) elemento può essere aggregato.|  
|[Elemento IsKey &#40;ASSL&#41;](iskey-element-assl.md)|Indica se la colonna fornisce la chiave in un elemento `MiningStructure`.|  
|[Elemento Isolation &#40;ASSL&#41;](isolation-element-assl.md)|Indica il livello di isolamento per un elemento derivato dal [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati.|  
|[Elemento KeyDuplicate &#40;ASSL&#41;](keyduplicate-element-assl.md)|Determina come [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gestisce un errore di chiave duplicata che si verifica durante l’elaborazione.|  
|[Elemento KeyErrorAction &#40;ASSL&#41;](keyerroraction-element-assl.md)|Specifica l'azione che [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] deve intraprendere quando si verifica un errore su una chiave.|  
|[Elemento KeyErrorLimit &#40;ASSL&#41;](keyerrorlimit-element-assl.md)|Contiene il numero di errori accettabili durante l'elaborazione.|  
|[Elemento KeyErrorLimitAction &#40;ASSL&#41;](keyerrorlimitaction-element-assl.md)|Specifica l'azione che [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] intraprende quando l'errore di chiave specificato nella [KeyErrorLimit](keyerrorlimit-element-assl.md) raggiungimento dell'elemento.|  
|[Elemento KeyErrorLogFile &#40;ASSL&#41;](../objects/file-element-assl.md)|Contiene il nome del file per la registrazione di errori dell'elaborazione.|  
|[Elemento KeyNotFound &#40;ASSL&#41;](keynotfound-element-assl.md)|Specifica come [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] risponde quando rileva un errore di integrità referenziale.|  
|[Elemento KeyUniquenessGuarantee &#40;ASSL&#41;](keyuniquenessguarantee-element-assl.md)|Indica se la relazione tra la chiave dell'attributo e il nome e la relazione con gli attributi correlati, è valida.|  
|[Elemento KpiID &#40;ASSL&#41;](kpiid-element-assl.md)|Contiene un ID associato a un elemento `Kpi` con un elemento `Perspective`.|  
|[Elemento di linguaggio &#40;ASSL&#41;](language-element-assl.md)|Contiene l'identificatore del linguaggio dell'elemento padre.|  
|[Elemento LastProcessed &#40;ASSL&#41;](lastprocessed-element-assl.md)|Contiene il timestamp di sola lettura che indica quando il database che contiene l'elemento padre viene elaborato per ultimo.|  
|[Elemento LastSchemaUpdate &#40;ASSL&#41;](lastschemaupdate-element-assl.md)|Contiene il timestamp dell'aggiornamento di metadati di sola lettura dell'elemento padre.|  
|[Elemento LastUpdate &#40;ASSL&#41;](lastupdate-element-assl.md)|Contiene un timestamp di sola lettura che indica l'ultimo orario in cui il `Database` associato o alcuni degli oggetti principali che il database contiene sono stati modificati.|  
|[Elemento latency &#40;ASSL&#41;](latency-element-assl.md)|Definisce il "periodo di tolleranza" tra la prima notifica e il momento in cui le immagini MOLAP vengono distrutte.|  
|[Elemento LogFileAppend &#40;ASSL&#41;](logfileappend-element-assl.md)|Determina se l'elemento `Trace` aggiunge la registrazione restituita al file di log esistente, o lo sovrascrive.|  
|[Elemento LogFileName &#40;ASSL&#41;](logfilename-element-assl.md)|Contiene il nome del file di log per l’elemento `Trace`.|  
|[Elemento LogFileRollover &#40;ASSL&#41;](logfilerollover-element-assl.md)|Specifica se la registrazione di `Trace` output deve passare a un nuovo file o deve arrestarsi quando dimensione massima file di log specificato nel [LogFileSize](logfilesize-element-assl.md) viene raggiunto.|  
|[Elemento LogFileSize &#40;ASSL&#41;](logfilesize-element-assl.md)|Specifica le dimensioni massime del file di log, in megabyte.|  
|[Elemento ManagedProvider &#40;ASSL&#41;](managedprovider-element-assl.md)|Contiene il nome del provider gestito usato da un elemento derivato dal tipo di dati `DataSource`.|  
|[Elemento ManufacturingExtraMonthQuarter &#40;ASSL&#41;](manufacturingextramonthquarter-element-assl.md)|Definisce il mese del periodo di produzione al quale viene assegnato un mese aggiuntivo per un elemento `TimeBinding`.|  
|[Elemento ManufacturingFirstMonth &#40;ASSL&#41;](manufacturingfirstmonth-element-assl.md)|Definisce il primo mese di produzione per un elemento `TimeBinding`.|  
|[Elemento ManufacturingFirstWeekOfMonth &#40;ASSL&#41;](manufacturingfirstweekofmonth-element-assl.md)|Definisce la prima settimana del mese di produzione per un elemento `TimeBinding`.|  
|[Elemento MasterDatasourceID &#40;ASSL&#41;](masterdatasourceid-element-assl.md)|Contiene l’ID di un’origine dati master per un elemento `Database`.|  
|[Elemento Materialization &#40;ASSL&#41;](materialization-element-assl.md)|Indica il tipo di relazione tra il gruppo di misure e la dimensione di riferimento.|  
|[Elemento MaxActiveConnections &#40;ASSL&#41;](maxactiveconnections-element-assl.md)|Contiene il numero massimo di connessioni simultanee consentite da un elemento derivato dal tipo di dati `DataSource`.|  
|[Elemento MdxMissingMemberMode &#40;ASSL&#41;](mdxmissingmembermode-element-assl.md)|Determina la modalità di gestione dei membri mancanti per le istruzioni MDX.|  
|[Elemento MeasureExpression &#40;ASSL&#41;](measureexpression-element-assl.md)|Contiene l'espressione MDX che definisce una misura.|  
|[Elemento MeasureGroupID &#40;ASSL&#41;](measuregroupid-element-assl.md)|Associa un `MeasureGroup` all'elemento padre, associazione o associazione out-of-line.|  
|[Elemento MeasureID &#40;ASSL&#41;](measureid-element-assl.md)|Associa un elemento `Measure` all'elemento padre.|  
|[Elemento Measurequalification &#40;ASSL&#41;](measurequalificaton-element-assl.md)|Determina se un prefisso viene applicato alle misure in `MeasureGroup`.|  
|[Elemento MemberNamesUnique &#40;ASSL&#41;](membernamesunique-element-assl.md)|Determina se i nomi dei membri sottostanti l'elemento padre devono essere univoci.|  
|[Elemento MemberUniqueNameStyle &#40;ASSL&#41;](memberuniquenamestyle-element-assl.md)|Determina il modo in cui vengono generati i nomi univoci dei membri delle gerarchie contenute all'interno dell’elemento `CubeDimension`.|  
|[Elemento MembersWithData &#40;ASSL&#41;](memberswithdata-element-assl.md)|Determina se visualizzare i membri dei dati per i membri non foglia nell'attributo padre.|  
|[Elemento MembersWithDataCaption &#40;ASSL&#41;](memberswithdatacaption-element-assl.md)|Fornisce una stringa modello usata per la creazione di didascalie per i membri dei dati generati dal sistema.|  
|[Elemento MimeType &#40;ASSL&#41;](mimetype-element-assl.md)|Contiene il tipo MIME (Multipurpose Internet Mail Extensions), se applicabile, dei dati rappresentati dall'elemento `DataItem` padre.|  
|[Elemento MiningModelID &#40;ASSL&#41;](miningmodelid-element-assl.md)|Associa un modello di data mining a una dimensione di data mining.|  
|[Nome di elemento &#40;ASSL&#41;](name-element-assl.md)|Contiene il nome dell'elemento padre.|  
|[Elemento NamingTemplate &#40;ASSL&#41;](namingtemplate-element-assl.md)|Definisce come vengono denominati i livelli in una gerarchia padre-figlio costruita da un elemento padre `DimensionAttribute`.|  
|[Elemento NonEmptyBehavior &#40;ASSL&#41;](nonemptybehavior-element-assl.md)|Determina il comportamento non vuoto associato al padre dell'elemento `CalculationProperty`.|  
|[Elemento NotificationTechnique &#40;ASSL&#41;](notificationtechnique-element-assl.md)|Specifica se [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o un'applicazione client esterna elabora le notifiche.|  
|[Elemento NullKeyConvertedToUnknown &#40;ASSL&#41;](nullkeyconvertedtounknown-element-assl.md)|Specifica l'azione da intraprendere quando si verifica un errore di conversione null.|  
|[Elemento NullKeyNotAllowed &#40;ASSL&#41;](nullkeynotallowed-element-assl.md)|Determina come il motore di elaborazione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gestisce un errore di chiave null verificato durante l’elaborazione.|  
|[Elemento NullProcessing &#40;ASSL&#41;](nullprocessing-element-assl.md)|Definisce come vengono elaborati i valori null.|  
|[Elemento OnlineMode &#40;ASSL&#41;](onlinemode-element-assl.md)|Specifica se il database ritorna immediatamente online quando la ricompilazione della cache è iniziata, o solo quando la ricompilazione della cache è completa.|  
|[Elemento OptimizedState &#40;ASSL&#41;](state-element-assl.md)|Determina il livello di ottimizzazione applicato alla gerarchia.|  
|[Elemento optionality &#40;ASSL&#41;](optionality-element-assl.md)|Indica la natura facoltativa dei membri per un elemento `AttributeRelationship`.|  
|[Elemento OrderBy &#40;ASSL&#41;](orderby-element-assl.md)|Descrive in che modo ordinare i membri contenuti nell'attributo.|  
|[Elemento OrderByAttributeID &#40;ASSL&#41;](orderbyattributeid-element-assl.md)|Identifica un altro attributo in base al quale ordinare i membri del [dimensione](../data-type/dimensionattribute-data-type-assl.md) attributo.|  
|[Elemento Ordinal &#40;ASSL&#41;](ordinal-element-assl.md)|Indica il numero ordinale da associare alle raccolte, ad esempio chiavi e conversioni.|  
|[Elemento OverrideBehavior &#40;ASSL&#41;](overridebehavior-element-assl.md)|Indica il comportamento di override della relazione descritta da un elemento `AttributeRelationship`.|  
|[Elemento PartitionID &#40;ASSL&#41;](partitionid-element-assl.md)|Associa un elemento `Partition` a un elemento padre, un’associazione, o un'associazione out-of-line.|  
|[Elemento password &#40;ASSL&#41;](password-element-assl.md)|Contiene la password dell'account utente per l'elemento `ImpersonationInfo`.|  
|[Elemento Path &#40;ASSL&#41;](path-element-assl.md)|Contiene il percorso, fornito da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], di un report utilizzato per il [ReportAction](../data-type/reportaction-data-type-assl.md) elemento.|  
|[Elemento PendingValue &#40;ASSL&#41;](pendingvalue-element-assl.md)|Contiene il valore in sospeso di sola lettura dell'elemento `ServerProperty` associato.|  
|[Elemento PermissionSet &#40;ASSL&#41;](permissionset-element-assl.md)|Identifica il set di autorizzazioni associato un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] assembly .NET Framework.|  
|[Elemento Persistence &#40;ASSL&#41;](persistence-element-assl.md)|Determina quali parti dei dati di origine associato sono dinamiche e vengono verificate per gli aggiornamenti usando la frequenza specificata per il [RefreshPolicy](refreshpolicy-element-assl.md) elemento.|  
|[Elaborare l'elemento &#40;ASSL&#41;](process-element-assl.md)|Determina se un utente può elaborare il proprietario dell'elemento padre.|  
|[Elemento ProcessingMode &#40;ASSL&#41;](processingmode-element-assl.md)|Indica se l'istanza deve essere indicizzata e aggregata durante o dopo l'elaborazione.|  
|[Elemento ProcessingPriority &#40;ASSL&#41;](processingpriority-element-assl.md)|Determina la priorità di elaborazione dell’oggetto padre durante le operazioni in background, ad esempio aggregazione lenta, indicizzazione o clustering,.|  
|[Elemento ProcessingQuery &#40;ASSL&#41;](query-element-assl.md)|Contiene il testo con parametri della query da eseguire per la notifica dello stato di elaborazione incrementale.|  
|[Elemento ProductName &#40;ASSL&#41;](productname-element-assl.md)|Contiene il nome di prodotto di sola lettura dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] associato a un elemento `Server`.|  
|[Elemento query &#40;ASSL&#41;](query-element-assl.md)|Contiene il testo della query che esegue la notifica.|  
|[Elemento QueryDefinition &#40;ASSL&#41;](querydefinition-element-assl.md)|Contiene un'espressione opaca per una query associata a un `DataSource` elemento in un [QueryBinding](../data-type/querybinding-data-type-assl.md) elemento.|  
|[Leggere l'elemento &#40;ASSL&#41;](read-element-assl.md)|Determina se è possono leggere i dati o metadati per un determinato [CubeDimensionPermission](../data-type/permission-data-type-assl.md) oppure [autorizzazione](../data-type/permission-data-type-assl.md) elemento.|  
|[Elemento ReadDefinition &#40;ASSL&#41;](readdefinition-element-assl.md)|Determina se i membri possono leggere la definizione del database o la definizione di oggetti nel database.|  
|[Elemento ReadSourceData &#40;ASSL&#41;](readsourcedata-element-assl.md)|Determina il modo in cui vengono generati i nomi univoci delle gerarchie contenute all'interno di `CubePermission`.|  
|[Elemento RefreshInterval &#40;ASSL&#41;](refreshinterval-element-assl.md)|Specifica che l'intervallo durante il quale i dati del limite sono associati all'elemento padre è aggiornato.|  
|[Elemento RefreshPolicy &#40;ASSL&#41;](refreshpolicy-element-assl.md)|Determina la frequenza parte dinamica del gruppo di misura o dimensione (come specificato dal [persistenza](persistence-element-assl.md) elemento) è selezionata per le modifiche.|  
|[Elemento RelationshipType &#40;ASSL&#41;](relationshiptype-element-assl.md)|Indica se le relazioni tra membri per un `AttributeRelationship` possono essere modificate.|  
|[Elemento RemoteDatasourceID &#40;ASSL&#41;](remotedatasourceid-element-assl.md)|Specifica l’ID dell'origine dati OLAP che punta all'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che archivia la partizione remota.|  
|[Elemento ReportingFirstMonth &#40;ASSL&#41;](reportingfirstmonth-element-assl.md)|Definisce il primo mese di report per l'elemento `TimeBinding`.|  
|[Elemento ReportingFirstWeekOfMonth &#40;ASSL&#41;](reportingfirstweekofmonth-element-assl.md)|Definisce la prima settimana del mese di report per l'elemento `TimeBinding`.|  
|[Elemento ReportingWeekToMonthPattern &#40;ASSL&#41;](reportingweektomonthpattern-element-assl.md)|Definisce il modello di report settimana-a-mese per l'elemento `TimeBinding`.|  
|[Elemento ReportServer &#40;ASSL&#41;](reportserver-element-assl.md)|Contiene il nome dell’istanza [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] usata da `ReportAction`.|  
|[Elemento RequiresRestart &#40;ASSL&#41;](requiresrestart-element-assl.md)|Contiene un valore di sola lettura associato a un elemento `ServerProperty` che determina se la modifica del valore della proprietà server richiede che l'istanza venga riavviata per applicare la modifica.|  
|[Elemento RoleID &#40;ASSL&#41;](roleid-element-assl.md)|Identifica il ruolo per il quale sono definite le autorizzazioni.|  
|[Elemento radice &#40;ASSL&#41;](root-element-assl.md)|Contiene i dati (set di righe) per un'origine dati.|  
|[Elemento RootMemberIf &#40;ASSL&#41;](rootmemberif-element-assl.md)|Determina il modo in cui vengono identificati il membro o i membri radice di un attributo padre.|  
|[Elemento schema &#40;ASSL&#41;](schema-element-assl.md)|Contiene lo schema della vista origine dati.|  
|[Elemento ScriptCacheProcessingMode &#40;ASSL&#41;](scriptcacheprocessingmode-element-assl.md)|Indica se il server deve compilare la cache script durante o dopo l'elaborazione.|  
|[Elemento SilenceInterval &#40;ASSL&#41;](silenceinterval-element-assl.md)|Definisce la quantità minima di tempo che l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] usano come pausa prima di avviare il processo di imaging MOLAP.|  
|[Elemento SilenceOverrideInterval &#40;ASSL&#41;](silenceoverrideinterval-element-assl.md)|Definisce la quantità di tempo che deve passare dopo la notifica iniziale prima che MOLAP imaging inizi.|  
|[Elemento Slice &#40;ASSL&#41;](slice-element-assl.md)|Contiene un'espressione MDX che definisce la sezione contenuta in una partizione.|  
|[Elemento SolveOrder &#40;ASSL&#41;](solveorder-element-assl.md)|Indica l'ordine di valutazione nel quale l'elemento `CalculationProperty` viene applicato a un membro calcolato o a una definizione della cella calcolata.|  
|[Elemento Source &#40;associazione&#41; &#40;ASSL&#41;](source-element-binding-assl.md)|Identifica l’origine dei dati a cui è associato l’elemento padre.|  
|[Elemento Source &#40;ComAssembly&#41; &#40;ASSL&#41;](source-element-comassembly-assl.md)|Contiene il nome file o identificatore a livello di codice (ProgID) per un componente COM (Component Object Model).|  
|[Elemento Source &#40;misura&#41; &#40;ASSL&#41;](source-element-measure-assl.md)|Contiene i dettagli dell’origine contenente il valore dell'elemento `Measure`.|  
|[Elemento SourceAttributeID &#40;ASSL&#41;](sourceattributeid-element-assl.md)|Contiene l'ID dell'attributo di origine in cui il [livello](../objects/level-element-assl.md) si basa l'elemento.|  
|[Elemento SourceColumnID &#40;ASSL&#41;](sourcecolumnid-element-assl.md)|Contiene l’ID della colonna della struttura di data mining di origine nell'elemento `MiningStructure` predecessore.|  
|[Elemento di stato &#40;ASSL&#41;](state-element-assl.md)|Contiene un valore di sola lettura che descrive lo stato dell'elaborazione corrente dell'elemento padre.|  
|[Elemento Status &#40;ASSL&#41;](status-element-assl.md)|Contiene un'espressione MDX che restituisce un indicatore di stato per un elemento `Kpi`.|  
|[Elemento StatusGraphic &#40;ASSL&#41;](statusgraphic-element-assl.md)|Contiene la rappresentazione grafica consigliata dello stato dell'elemento `Kpi`.|  
|[Elemento StopTime &#40;ASSL&#41;](stoptime-element-assl.md)|Specifica data e ora in cui un elemento `Trace` si deve arrestare|  
|[Elemento StorageLocation &#40;ASSL&#41;](storagelocation-element-assl.md)|Contiene il percorso di archiviazione del file system per il contenuto dell'elemento padre.|  
|[Elemento StorageMode &#40;ASSL&#41;](storagemode-element-assl.md)|Determina la modalità di archiviazione per l’elemento padre.|  
|[Elemento TableID &#40;ASSL&#41;](tableid-element-assl.md)|Contiene l’ID della tabella (dall’elemento `DataSourceView`) associata all'elemento padre.|  
|[Elemento di destinazione &#40;ASSL&#41;](target-element-assl.md)|Identifica la destinazione dell'elemento `Action`.|  
|[Elemento TargetType &#40;ASSL&#41;](targettype-element-assl.md)|Identifica il tipo di elemento dell'elemento identificato nel [destinazione](target-element-assl.md) elemento.|  
|[Elemento di testo &#40;ASSL&#41;](text-element-assl.md)|Contiene il testo di un [comando](../objects/command-element-assl.md) elemento.|  
|[Elemento timeout &#40;ASSL&#41;](timeout-element-assl.md)|Specifica l'ora, in secondi, dopo la quale un tentativo di recuperare i dati restituisce un timeout.|  
|[Elemento di tendenza &#40;ASSL&#41;](trend-element-assl.md)|Contiene un'espressione MDX che restituisce un indicatore della tendenza per un elemento `Kpi`.|  
|[Elemento TrendGraphic &#40;ASSL&#41;](trendgraphic-element-assl.md)|Contiene la rappresentazione grafica consigliata della tendenza dell'elemento `Kpi`.|  
|[Elemento trimming &#40;ASSL&#41;](trimming-element-assl.md)|Specifica come i dati vengono rimossi dall'origine dati.|  
|[Elemento Type &#40;azione&#41; &#40;ASSL&#41;](type-element-action-assl.md)|Contiene il tipo dell'elemento `Action`.|  
|[Elemento Type &#40;associazione&#41; &#40;ASSL&#41;](type-element-binding-assl.md)|Contiene il tipo dell'associazione attributo.|  
|[Elemento Type &#40;ClrAssemblyFile&#41; &#40;ASSL&#41;](type-element-clrassemblyfile-assl.md)|Specifica il tipo di file di uno dei file che appartengono a un assembly .NET Framework.|  
|[Elemento Type &#40;dimensione&#41; &#40;ASSL&#41;](type-element-dimension-assl.md)|Fornisce informazioni sul contenuto della dimensione.|  
|[Elemento Type &#40;DimensionAttribute&#41; &#40;ASSL&#41;](type-element-dimensionattribute-assl.md)|Contiene il tipo dell'attributo.|  
|[Elemento Type &#40;MeasureGroup&#41; &#40;ASSL&#41;](type-element-measuregroup-assl.md)|Specifica il tipo di `MeasureGroup`.|  
|[Elemento Type &#40;MeasureGroupAttribute&#41; &#40;ASSL&#41;](type-element-measuregroupattribute-assl.md)|Contiene il tipo di un [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md) elemento.|  
|[Elemento Type &#40;MiningStructureColumn&#41; &#40;ASSL&#41;](type-element-miningstructurecolumn-assl.md)|Contiene il tipo del [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) elemento.|  
|[Elemento Type &#40;partizioni&#41; &#40;ASSL&#41;](type-element-partition-assl.md)|Contiene il tipo dell'elemento `Partition`.|  
|[Elemento Type &#40;PerspectiveCalculation&#41; &#40;ASSL&#41;](type-element-perspectivecalculation-assl.md)|Indica il tipo del [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) elemento.|  
|[Elemento UnknownMember &#40;ASSL&#41;](unknownmember-element-assl.md)|Indica se il membro sconosciuto è visibile.|  
|[Elemento UnknownMemberName &#40;ASSL&#41;](unknownmembername-element-assl.md)|Contiene la didascalia, nella lingua predefinita della dimensione, per il membro sconosciuto della dimensione.|  
|[Elemento Usage &#40;DimensionAttribute&#41; &#40;ASSL&#41;](usage-element-dimensionattribute-assl.md)|Descrive la modalità di utilizzo di un attributo.|  
|[Elemento Usage &#40;MiningModelColumn&#41; &#40;ASSL&#41;](usage-element-miningmodelcolumn-assl.md)|Descrive come la colonna associata nel padre `MiningStructure` viene usata.|  
|[Valore elemento &#40;ASSL&#41;](value-element-assl.md)|Contiene il valore dell'elemento padre.|  
|[Elemento Version &#40;ASSL&#41;](version-element-assl.md)|Contiene il numero di versione di sola lettura dell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rappresentato dall'elemento `Server`.|  
|[Elemento Visibility &#40;ASSL&#41;](visibility-element-assl.md)|Definisce la visibilità di un [annotazione](../objects/annotation-element-assl.md) elemento.|  
|[Elemento Visible &#40;ASSL&#41;](visible-element-assl.md)|Determina la visibilità dell’elemento padre.|  
|[Elemento VisualTotals &#40;ASSL&#41;](visualtotals-element-assl.md)|Contiene un'espressione MDX che determina se i totali visualizzati vengono visualizzati per i membri di questo attributo.|  
|[Scrivere l'elemento &#40;ASSL&#41;](write-element-assl.md)|Determina se i dati o i metadati possono essere scritti per un elemento specificato `CubeDimensionPermission` o `Permission`.|  
|[Elemento WriteEnabled &#40;ASSL&#41;](writeenabled-element-assl.md)|Indica se i writeback della dimensione sono disponibili, in base alle autorizzazioni di sicurezza.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia Analysis Services Scripting Language XML elemento &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  