---
title: ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ALTER_DATABASE_SCOPED_CONFIGURATION
- ALTER_DATABASE_SCOPED_CONFIGURATION_TSQL
- DATABASE_SCOPED_CONFIGURATION_TSQL
- SCOPED_CONFIGURATION_TSQL
- SCOPED_TSQL
- ALTER_DATABASE_SCOPED_TSQL
- DATABASE_SCOPED_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CONFIGURATION statement
- configuration [SQL Server], ALTER DATABASE SCOPED CONFIGURATION statement
ms.assetid: 63373c2f-9a0b-431b-b9d2-6fa35641571a
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f9eb68c07f9e163dfba699627e41ea825b041540
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questa istruzione consente di alcuni database le impostazioni di configurazione di **singoli database** livello. Questa istruzione è disponibile in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Tali impostazioni sono:  
  
- Cancellare la cache delle procedure.  
- Impostare il parametro MAXDOP su un valore arbitrario (1,2,...) per il database primario in base a ciò che è adatto per un particolare database e imposta un valore diverso (ad esempio, 0) per tutti i database secondari usati di (ad esempio per le query di report).  
- Impostare il modello di stima della cardinalità di Query Optimizer su un livello di compatibilità, indipendentemente dal database.  
- Abilitare o disabilitare l'analisi dei parametri a livello di database.
- Abilitare o disabilitare gli hotfix di ottimizzazione query a livello di database.
- Abilitare o disabilitare la cache delle identità a livello di database.
- Abilitare o disabilitare uno stub del piano compilato per essere memorizzati nella cache quando un batch viene compilato per la prima volta.    
  
 ![icona di collegamento](../../database-engine/configure-windows/media/topic-link.gif "icona collegamento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET < set_options >
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}
    | IDENTITY_CACHE = { ON | OFF }
    | OPTIMIZE_FOR_AD_HOC_WORKLOADS = { ON | OFF }
}  
```  
  
## <a name="arguments"></a>Argomenti  
 
PER I DATABASE SECONDARI  
 
Specifica le impostazioni per i database secondari (tutti i database secondari devono avere valori identici).  
  
MAXDOP  **=**  {\<valore > | PRIMARY}  
**\<valore >**  
  
Specifica il valore predefinito per l'impostazione MAXDOP utilizzato per le istruzioni. 0 è il valore predefinito e indica che verrà utilizzata la configurazione del server. MAXDOP a livello di database esegue l'override (a meno che non sia 0) di **massimo grado di parallelismo** impostato a livello di server con sp_configure. L'hint per la query può eseguire comunque l'override di MAXDOP impostato a livello di database. Per ottimizzare una query specifica è necessario infatti modificare tale o   

Grazie all'opzione max degree of parallelism è possibile limitare il numero di processori da utilizzare nell'esecuzione di piani paralleli. SQL Server considera piani di esecuzione parallela per query, operazioni di indice data definition language (DDL), inserimento parallelo, modifica online per colonna, raccolta di statistiche parallela e popolamento dei cursori statici e basati su keyset.
 
Per impostare questa opzione a livello di istanza, vedere [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). 

> [!TIP] 
> A livello di query è possibile aggiungere lo [hint](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**.  
  
PRIMARY  
  
Può essere impostato solo per i database secondari, mentre il database è sul primario, e indica che la configurazione sarà quella impostata per il database primario. Se la configurazione per il primario cambia, il valore nei database secondari verrà modificato di conseguenza senza la necessità di impostarli in modo esplicito. **PRIMARY** è l'impostazione predefinita per i database secondari.  
  
LEGACY_CARDINALITY_ESTIMATION  **=**  {ON | **OFF** | PRIMARY}  

Consente di impostare il modello di stima della cardinalità di query optimizer su SQL Server 2012 e versione precedente, indipendentemente dal livello di compatibilità del database. Il valore predefinito è **OFF**, che imposta il modello di stima della cardinalità in base al livello di compatibilità del database. Impostare su **ON** equivale ad abilitare il [flag di traccia 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

> [!TIP] 
> A livello di query, aggiungere l'[hint per la query](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) **QUERYTRACEON**. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, aggiungere l'[hint per la query](../../t-sql/queries/hints-transact-sql-query.md) **HINT USE** anziché utilizzare il flag di traccia. 
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database è sul primario, e specifica che l'impostazione del modello di stima di cardinalità per il query optimizer in tutti i database secondari sarà quello impostato per il database primario. Se la configurazione del modello di stima di cardinalità per il query optimizer sul primario cambia, il valore nei database secondari verrà modificato di conseguenza. **PRIMARY** è l'impostazione predefinita per i database secondari.
  
PARAMETER_SNIFFING  **=**  { **ON** | OFF | PRIMARIO}  

Abilita o disabilita [lo sniffing dei parametri](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). Il valore predefinito è ON. Equivale a [Flag di traccia 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> A livello di query, vedere l'[hint per la query](../../t-sql/queries/hints-transact-sql-query.md) **OPTIMIZE FOR UNKNOWN**. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, usare l'[hint per la query](../../t-sql/queries/hints-transact-sql-query.md) **HINT USE**. 
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database è sul primario, e specifica che il valore per questa impostazione su tutti i database secondari sarà il valore impostato per il database primario. Se la configurazione del primario per l'utilizzo dello [sniffing dei parametri](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) cambia, il valore nel database secondario verrà modificato di conseguenza senza la necessità di impostarlo in modo esplicito. Questo è l'impostazione predefinita per i database secondari.
  
QUERY_OPTIMIZER_HOTFIXES  **=**  {ON | **OFF** | PRIMARIO}  

Abilita o disabilita gli hotfix di ottimizzazione di query indipendentemente dal livello di compatibilità del database. Il valore predefinito è **OFF**, che disabilita gli hotfix di ottimizzazione che sono stati rilasciati dopo che è stato introdotto il massimo livello di compatibilità disponibile per una versione specifica di query (post-RTM). L'impostazione su **ON** equivale ad abilitare il [flag di traccia 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> A livello di query, aggiungere l'[hint per la query](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) **QUERYTRACEON**. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, aggiungere l'[hint per la query](../../t-sql/queries/hints-transact-sql-query.md) **HINT USE** anziché utilizzare il flag di traccia.  
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database nel server primario e specifica che il valore per questa impostazione su tutti i database secondari è il valore impostato per il database primario. Se la configurazione per le principali modifiche, il valore nel database secondario viene modificato di conseguenza senza la necessità di impostare i database secondari valore in modo esplicito. Questo è l'impostazione predefinita per i database secondari.  
  
CLEAR PROCEDURE_CACHE  

Cancella la cache delle procedure (piano) per il database. Può essere eseguito sia nel database primario e secondari.  

IDENTITY_CACHE  **=**  { **ON** | OFF}  

**Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

Abilita o disabilita la cache delle identità a livello di database. Il valore predefinito è **ON**. La memorizzazione nella cache di identità viene utilizzata per migliorare le prestazioni di inserimento in tabelle con colonne identity. Per evitare interruzioni nei valori di una colonna identity nei casi in cui il server viene riavviato in modo imprevisto o viene eseguito il failover a un server secondario, disabilitare l'opzione IDENTITY_CACHE. Questa opzione è simile al [flag di traccia 272](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md), ad eccezione del fatto che può essere impostata a livello di database, anziché solo a livello di server.   

> [!NOTE] 
> Questa opzione può essere impostata solo per il database primario. Per ulteriori informazioni, vedere [colonne identity](create-table-transact-sql-identity-property.md).   

OPTIMIZE_FOR_AD_HOC_WORKLOADS **=** { ON | **OFF** }  

**Si applica a**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

Abilita o disabilita un stub del piano compilato per essere memorizzati nella cache quando un batch viene compilato per la prima volta. Il valore predefinito è OFF. Dopo la configurazione con ambito database che optimize_for_ad_hoc_workloads è abilitato per un database, uno stub del piano compilato verrà archiviata nella cache quando un batch viene compilata per la prima volta. Gli stub piano avere un footprint di memoria più piccolo rispetto alle dimensioni del piano compilato completo.  Se un batch viene compilato o eseguito di nuovo, lo stub del piano compilato verrà rimosso e sostituito con un piano compilato completo.

##  <a name="Permissions"></a> Autorizzazioni  
 Richiede ALTER ANY DATABASE SCOPE CONFIGURATION. Questa autorizzazione può essere concessa da un utente con autorizzazione CONTROL per un database.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Sebbene sia possibile configurare i database secondari per le impostazioni di configurazione di ambito diverso dal loro primario, tutti i database secondari utilizzano la stessa configurazione. Impossibile configurare impostazioni diverse per singoli database secondari.  
  
 Eseguire questa istruzione consente di cancellare la cache delle procedure nel database corrente, il che significa che è necessario ricompilare tutte le query.  
  
 Per le query di nome 3 parti, le impostazioni per la connessione al database corrente per la query viene presa in considerazione diversi per i moduli SQL (ad esempio procedure, funzioni e trigger) che vengono compilati nel contesto del database corrente e quindi utilizza le opzioni del database in cui risiedono.  
  
 L'evento ALTER_DATABASE_SCOPED_CONFIGURATION viene aggiunto come un evento DDL che può essere usato per la generazione di un trigger DDL. Questo è un figlio del gruppo ALTER_DATABASE_EVENTS trigger.  
 
 Configurazione delle impostazioni verranno proseguite con il database con ambito database. Ciò significa che quando un database viene ripristinato o collegato, le impostazioni di configurazione esistenti rimangono.
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
**MAXDOP**  
  
 Le impostazioni granulari possono eseguire l'override delle globali e il resource governor può limitare tutte le altre impostazioni MAXDOP. La logica per l'impostazione di MAXDOP è la seguente:  
  
-   L'hint per la query esegue l'override sia di quanto impostato con sp_configure sia con l'opzione a livello di database. Se il gruppo di risorse MAXDOP è impostato per il gruppo di carico: 
  
    -   Se l'hint per la query è impostata su 0, viene sottoposto a override dall'impostazione di resource governor.  
  
    - Se l'hint per la query non è 0, il valore è limitato dall'impostazione nel resource governor.  
  
-   Il setting a livello di database (se diverso da 0) sostituisce l'impostazione di sp_configure, a meno che non vi sia un hint per la query e che sia limitata dall'impostazione nel resource governor.  
  
-   L'impostazione di sp_configure viene sottoposta a override dall'impostazione nel resource governor.  
  
**QUERY_OPTIMIZER_HOTFIXES**  
  
 Quando l'hint QUERYTRACEON viene utilizzato per abilitare l'utilità di ottimizzazione query legacy o hotfix di query optimizer, sarebbe una condizione OR tra l'hint di query e la configurazione con ambito database, l'impostazione, vale a dire che se uno è abilitata, le opzioni sono valide.  
  
**GeoDR**  
  
 I database secondari leggibili, ad esempio i gruppi di disponibilità AlwaysOn e replica geografica del, utilizzano il valore secondario controllando lo stato del database. Anche se recompile non si verifica in caso di failover e tecnicamente il nuovo database primario con le query che utilizzano le impostazioni di secondarie, l'idea è che l'impostazione tra server primario e secondario variano solo quando il carico di lavoro è diverso, pertanto le query memorizzate nella cache utilizzando le impostazioni ottimali, mentre le nuove query selezionare le nuove impostazioni che sono appropriate per loro.  
  
**DacFx**  
  
 Poiché con ambito DATABASE ALTER configurazione è una nuova funzionalità di Database SQL di Azure e SQL Server che inizia con SQL Server 2016 che interessa lo schema del database, l'esportazione dello schema (con o senza dati) non sono in grado di essere importati in una versione precedente di SQL Server ad esempio [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)]. Ad esempio, un'esportazione in un [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) o [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) da un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] database in cui questa nuova funzionalità non sarebbe in grado di essere importati in un server di livello inferiore.  
  
## <a name="metadata"></a>Metadati  

La vista di sistema [sys.database_scoped_configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) fornisce informazioni sulle configurazioni a livello di un database. Le opzioni di configurazione a livello di database nella database_scoped_configurations sono gli override delle impostazioni predefinite a livello di server. La vista [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) mostra solo le impostazioni a livello di server.  
  
## <a name="examples"></a>Esempi  
Questi esempi illustrano l'utilizzo di ALTER DATABASE SCOPED CONFIGURATION  
  
### <a name="a-grant-permission"></a>A. Concedere l'autorizzazione  

In questo esempio viene mostrato come concedere l'autorizzazione necessaria per eseguire ALTER DATABASE SCOPED CONFIGURATION     
all'utente [Joe].  
  
```sql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. Set di MAXDOP  

In questo esempio si imposta MAXDOP = 1 per un database primario e MAXDOP = 4 per un database secondario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
In questo esempio si imposta MAXDOP su un database secondario per farlo corrispondere a quello sul database primario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. Set LEGACY_CARDINALITY_ESTIMATION  

In questo esempio si imposta LEGACY_CARDINALITY_ESTIMATION su ON su un database secondario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
In questo esempio si imposta LEGACY_CARDINALITY_ESTIMATION su un database secondario, come per il database primario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. Set PARAMETER_SNIFFING  

In questo esempio si imposta PARAMETER_SNIFFING su OFF su un database primario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
In questo esempio si imposta PARAMETER_SNIFFING su OFF su un database primario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
In questo esempio imposta PARAMETER_SNIFFING per database secondario perché si trova nel database primario in uno scenario di replica geografica.  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. Set QUERY_OPTIMIZER_HOTFIXES  

Impostare QUERY_OPTIMIZER_HOTFIXES su ON per un database primario in uno scenario di replica geografica.  

```sql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. Cancellare la Cache delle Procedure  

In questo esempio si cancella la cache delle procedure (possibile solo per un database primario).  
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. Set IDENTITY_CACHE

**Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e [!INCLUDE[ssSDS](../../includes/sssds-md.md)] (funzionalità è in anteprima pubblica) 

In questo esempio si disabilita la cache delle identità.

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

### <a name="h-set-optimizeforadhocworkloads"></a>H. Set OPTIMIZE_FOR_AD_HOC_WORKLOADS

**Si applica a**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 

Questo esempio viene abilitato uno stub del piano compilato essere memorizzati nella cache quando un batch viene compilato per la prima volta.

```sql 
ALTER DATABASE SCOPED CONFIGURATION SET OPTIMIZE_FOR_AD_HOC_WORKLOADS = ON;
```

## <a name="additional-resources"></a>Risorse aggiuntive

### <a name="maxdop-resources"></a>Risorse MAXDOP 
* [Grado di parallelismo](../../relational-databases/query-processing-architecture-guide.md#DOP)
* [Indicazioni e linee guida per l'opzione di configurazione "max degree of parallelism" in SQL Server](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>Risorse LEGACY_CARDINALITY_ESTIMATION    
* [Stima della cardinalità (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](https://msdn.microsoft.com/library/dn673537.aspx) (Ottimizzazione dei piani di query con la stima di cardinalità di SQL Server 2014)

### <a name="parametersniffing-resources"></a>Risorse PARAMETER_SNIFFING    
* [Analisi dei parametri](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)
* ["I smell a parameter!"](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>Risorse QUERY_OPTIMIZER_HOTFIXES    
* [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
* [SQL Server query optimizer hotfix trace flag 4199 modello di manutenzione](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>Ulteriori informazioni  
 [sys.database_scoped_configurations](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [Viste di database e i file del catalogo](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Opzioni di configurazione server](../../database-engine/configure-windows/server-configuration-options-sql-server.md) [Sys. Configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
 
