---
title: ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 19d2d42ff513020b5d4bb9492f0714893101bdcb
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="alter-database-scoped-configuration-transact-sql"></a>ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questa istruzione consente di alcuni database le impostazioni di configurazione di **singoli database** livello. Questa istruzione è disponibile sia in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Tali impostazioni sono:  
  
- Cancellare la cache delle procedure.  
  
- Impostare il parametro MAXDOP su un valore arbitrario (1,2,...) per il database primario in base a ciò che è più adatto per il database specifico e impostare un valore diverso (ad esempio 0) per tutti i database secondari usati (ad esempio per le query di report).  
  
- Impostare il modello di stima della cardinalità di Query Optimizer su un livello di compatibilità, indipendentemente dal database.  
  
- Abilitare o disabilitare l'analisi dei parametri a livello di database.
  
- Abilitare o disabilitare gli hotfix di ottimizzazione query a livello di database.

- Abilitare o disabilitare la cache delle identità a livello di database.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER DATABASE SCOPED CONFIGURATION  
{        
     {  [ FOR SECONDARY] SET <set_options>  }    
}  
| CLEAR PROCEDURE_CACHE  
| SET IDENTITY_CACHE = { ON | OFF }
[;]    
  
< set_options > ::=    
{  
    MAXDOP = { <value> | PRIMARY}    
    | LEGACY_CARDINALITY_ESTIMATION = { ON | OFF | PRIMARY}    
    | PARAMETER_SNIFFING = { ON | OFF | PRIMARY}    
    | QUERY_OPTIMIZER_HOTFIXES = { ON | OFF | PRIMARY}    
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 
PER I DATABASE SECONDARI  
 
Specifica le impostazioni per i database secondari (tutti i database secondari devono avere valori identici).  
  
MAXDOP  **=**  {\<valore > | PRIMARIO}  
**\<valore >**  
  
Specifica il valore predefinito MAXDOP impostazione che deve essere utilizzato per le istruzioni. 0 è il valore predefinito e indica che la configurazione del server verrà utilizzata. Esegue l'override di MAXDOP nell'ambito del database (a meno che non è impostata su 0) di **massimo grado di parallelismo** impostato a livello di server da sp_configure. Hint per la query può comunque eseguire l'override del database con ambito MAXDOP per ottimizzare le query specifiche che è necessario modificare questa impostazione. Tutte queste impostazioni sono limitate di MAXDOP impostate per il gruppo di carico di lavoro.   

Grazie all'opzione max degree of parallelism è possibile limitare il numero di processori da utilizzare nell'esecuzione di piani paralleli. SQL Server considera piani di esecuzione parallela per query, operazioni di indice data definition language (DDL), inserimento parallelo, in linea alter column, collectiion statistiche parallela e popolamento dei cursori statici e basati su keyset.
 
Per impostare questa opzione a livello di istanza, vedere [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). 

> [!TIP] 
> A tale scopo a livello di query, aggiungere il **MAXDOP** [hint per la query](../../t-sql/queries/hints-transact-sql-query.md).  
  
PRIMARY  
  
Può essere impostato solo per i database secondari, mentre il database nel sistema primario e indica che la configurazione sarà quello impostato per il database primario. Se la configurazione per le principali modifiche, il valore nel database secondario verrà modificato di conseguenza senza la necessità di impostare i database secondari valore in modo esplicito. **PRIMARIO** è l'impostazione predefinita per i database secondari.  
  
LEGACY_CARDINALITY_ESTIMATION  **=**  {ON | **OFF** | PRIMARIO}  

Consente di impostare il modello di stima della cardinalità di query optimizer di SQL Server 2012 e versione precedente, indipendentemente dal livello di compatibilità del database. Il valore predefinito è **OFF**, che imposta il modello di stima della cardinalità di query optimizer in base al livello di compatibilità del database. L'impostazione di **ON** equivale ad abilitare [Flag di traccia 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

> [!TIP] 
> A tale scopo a livello di query, aggiungere il **QUERYTRACEON** [hint per la query](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, aggiungere il **HINT USE** [hint per la query](../../t-sql/queries/hints-transact-sql-query.md) anziché utilizzare il flag di traccia. 
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database nel server primario e specifica che l'impostazione del modello query optimizer cardinalità stima in tutti i database secondari sarà il valore impostato per il database primario. Se la configurazione del server primario per il modello di stima della cardinalità di query optimizer viene modificata, è possibile che il valore nel database secondario verrà modificato di conseguenza. **PRIMARIO** è l'impostazione predefinita per i database secondari.  
  
PARAMETER_SNIFFING  **=**  { **ON** | OFF | PRIMARIO}  

Abilita o disabilita [lo sniffing dei parametri](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing). Il valore predefinito è ON. Equivale a [Flag di traccia 4136](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> A tale scopo a livello di query, vedere il **OPTIMIZE FOR UNKNOWN** [hint per la query](../../t-sql/queries/hints-transact-sql-query.md). A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, il **HINT USE** [hint per la query](../../t-sql/queries/hints-transact-sql-query.md) è disponibile. 
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database nel server primario e specifica che il valore per questa impostazione su tutti i database secondari sarà il valore impostato per il database primario. Se la configurazione del server primario per l'utilizzo di [lo sniffing dei parametri](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing) modifiche, il valore nel database secondario verrà modificato di conseguenza senza la necessità di impostare i database secondari valore in modo esplicito. Questo è l'impostazione predefinita per i database secondari.  
  
QUERY_OPTIMIZER_HOTFIXES  **=**  {ON | **OFF** | PRIMARIO}  

Abilita o disabilita gli hotfix di ottimizzazione di query indipendentemente dal livello di compatibilità del database. Il valore predefinito è **OFF**. Ciò equivale ad abilitare [Flag di traccia 4199](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).   

> [!TIP] 
> A tale scopo a livello di query, aggiungere il **QUERYTRACEON** [hint per la query](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1, per eseguire questa operazione a livello di query, aggiungere l'HINT USE [hint per la query](../../t-sql/queries/hints-transact-sql-query.md) anziché utilizzare il flag di traccia.  
  
PRIMARY  
  
Questo valore è valido solo per i database secondari, mentre il database nel server primario e specifica che il valore per questa impostazione su tutti i database secondari sarà il valore impostato per il database primario. Se la configurazione per le principali modifiche, il valore nel database secondario verrà modificato di conseguenza senza la necessità di impostare i database secondari valore in modo esplicito. Questo è l'impostazione predefinita per i database secondari.  
  
CANCELLA PROCEDURE_CACHE  

Cancella la cache delle procedure per il database. Può essere eseguito sia nel database primario e secondari.  

IDENTITY_CACHE = { **ON** | OFF}  

**Si applica a**: 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica) 

Abilita o disabilita la cache delle identità a livello di database. Il valore predefinito è **ON**. La memorizzazione nella cache di identità viene utilizzato per migliorare le prestazioni di inserimento in tabelle con colonne Identity. Per evitare interruzioni nei valori della colonna Identity nei casi in cui il server viene riavviato in modo imprevisto o viene eseguito il failover a un server secondario, disabilitare l'opzione IDENTITY_CACHE. Questa opzione è simile a esistente SQL Server Trace Flag 272, ad eccezione del fatto che può essere impostata a livello di database, anziché solo a livello di server.   

> [!NOTE] 
> Questa opzione può essere impostata solo per il database primario. Per ulteriori informazioni, vedere [colonne Identity](create-table-transact-sql-identity-property.md).  
>

##  <a name="Permissions"></a> Autorizzazioni  
 È necessario modificare qualsiasi configurazione di ambito DATABASE   
nel database. Questa autorizzazione può essere concessa da un utente con autorizzazione CONTROL per un database  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Sebbene sia possibile configurare i database secondari per le impostazioni di configurazione di ambito diverso dal loro primario, tutti i database secondari utilizzerà la stessa configurazione. Impossibile configurare impostazioni diverse per singoli database secondari.  
  
 Eseguire l'istruzione verrà cancellato la cache delle procedure nel database corrente, il che significa che saranno necessario ricompilare tutte le query.  
  
 Per le query di nome 3 parti, le impostazioni per la connessione al database corrente per la query verrà presa in considerazione diversi per i moduli SQL (ad esempio, procedure, funzioni e trigger) che vengono compilati nel contesto del database corrente e pertanto verranno utilizzate le opzioni di database in cui risiedono.  
  
 L'evento ALTER_DATABASE_SCOPED_CONFIGURATION viene aggiunto come un evento DDL che può essere usato per la generazione di un trigger DDL. Questo è un figlio del gruppo ALTER_DATABASE_EVENTS trigger.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 **MAXDOP**  
  
 Impostazioni granulari possono eseguire l'override di quelli globali e governor tale risorsa è possibile chiudere tutte le altre impostazioni MAXDOP.  La logica per l'impostazione di MAXDOP è la seguente:  
  
-   Hint per la query esegue l'override di sp_configure sia l'opzione di database con ambito. Se il gruppo di risorse MAXDOP è impostato per il gruppo di carico:  
  
    -   Se l'hint per la query è impostata su 0 che viene sottoposto a override dall'impostazione di resource governor.  
  
    -   Se l'hint per la query non 0, il valore è limitata da resource governor impostazione.  
  
-   Il database con ambito impostare (a meno che non è uguale a 0) sostituisce l'impostazione di sp_configure, a meno che non vi è un hint per la query e vengono limitate dall'impostazione di resource governor.  
  
-   L'impostazione di sp_configure viene sottoposto a override dall'impostazione di resource governor.  
  
 **QUERY_OPTIMIZER_HOTFIXES**  
  
 Quando l'hint QUERYTRACEON viene utilizzato per abilitare l'utilità di ottimizzazione query legacy o hotfix di query optimizer, sarebbe una condizione OR tra l'hint di query e la configurazione con ambito database, l'impostazione, vale a dire che se uno è abilitata, le opzioni verranno applicate.  
  
 **GeoDR**  
  
 I database secondari leggibili, ad esempio i gruppi di disponibilità AlwaysOn e replica geografica del, utilizzano il valore secondario controllando lo stato del database. Anche se è non ricompilare il failover e tecnicamente il nuovo database primario con le query che utilizzano le impostazioni di secondarie, l'idea è che l'impostazione tra server primario e secondario variano solo quando il carico di lavoro è diverso, pertanto le query memorizzate nella cache utilizzando le impostazioni ottimali, mentre le nuove query selezionerà le nuove impostazioni che sono appropriate per loro.  
  
 **DacFx**  
  
 Poiché una nuova funzionalità di Database SQL di Azure e SQL Server 2016 che interessa lo schema del database, ALTER DATABASE SCOPED CONFIGURATION esportazioni dello schema (con o senza dati) non sarà in grado di essere importati in una versione precedente di SQL Server, ad esempio [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o < C2 > [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] . Ad esempio, un'esportazione in un [DACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_3) o [BACPAC](https://msdn.microsoft.com/library/ee210546.aspx#Anchor_4) da un [!INCLUDE[ssSDS](../../includes/sssds-md.md)] o [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] database in cui questa nuova funzionalità non sarebbe in grado di essere importati in un server di livello inferiore.  
  
## <a name="metadata"></a>Metadati  

Il [database_scoped_configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) vista di sistema vengono fornite informazioni sulle configurazioni con ambite all'interno di un database. Opzioni di configurazione con ambito database visualizzato solo nella database_scoped_configurations come se fossero gli override per le impostazioni predefinite a livello di server. Il [Configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) vista di sistema vengono mostrate solo le impostazioni a livello di server.  
  
## <a name="examples"></a>Esempi  
Questi esempi illustrano l'utilizzo di ALTER DATABASE SCOPED CONFIGURATION  
  
### <a name="a-grant-permission"></a>A. Concedere l'autorizzazione  

In questo esempio concedere l'autorizzazione necessaria per eseguire ALTER DATABASE SCOPED CONFIGURATION     
all'utente [Joe].  
  
```tsql  
GRANT ALTER ANY DATABASE SCOPED CONFIGURATION to [Joe] ;  
```  
  
### <a name="b-set-maxdop"></a>B. Set di MAXDOP  

In questo esempio imposta MAXDOP = 1 per un database primario e MAXDOP = 4 per un database secondario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET MAXDOP = 1 ;  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=4 ;  
```  
  
In questo esempio imposta MAXDOP per un database secondario per corrispondere a quello impostato per il database primario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY ;
```  
  
### <a name="c-set-legacycardinalityestimation"></a>C. Set LEGACY_CARDINALITY_ESTIMATION  

In questo esempio imposta LEGACY_CARDINALITY_ESTIMATION su ON per un database secondario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=ON ;  
```  
  
In questo esempio imposta LEGACY_CARDINALITY_ESTIMATION per un database secondario, come per il database primario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET LEGACY_CARDINALITY_ESTIMATION=PRIMARY ;  
```  
  
### <a name="d-set-parametersniffing"></a>D. Set PARAMETER_SNIFFING  

In questo esempio imposta PARAMETER_SNIFFING su OFF per un database primario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET PARAMETER_SNIFFING =OFF ;  
```  
  
In questo esempio imposta PARAMETER_SNIFFING su OFF per un database primario in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING=OFF ;  
```  
  
In questo esempio imposta PARAMETER_SNIFFING per database secondario perché si trova nel database primario   
in uno scenario di replica geografica.  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET PARAMETER_SNIFFING =PRIMARY ;  
```  
  
### <a name="e-set-queryoptimizerhotfixes"></a>E. Set QUERY_OPTIMIZER_HOTFIXES  

Impostare QUERY_OPTIMIZER_HOTFIXES su ON per un database primario   
in uno scenario di replica geografica.  

```tsql  
ALTER DATABASE SCOPED CONFIGURATION SET QUERY_OPTIMIZER_HOTFIXES=ON ;  
```  
  
### <a name="f-clear-procedure-cache"></a>F. Cancellare la Cache delle Procedure  

In questo esempio cancella la cache delle procedure (possibile solo per un database primario).  
  
```tsql  
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE ;  
```  

### <a name="g-set-identitycache"></a>G. Set IDENTITY_CACHE

**Si applica a**: 2017 e Azure SQL Database di SQL Server (funzionalità è in anteprima pubblica) 

In questo esempio disabilita la cache delle identità.

```tsql 
ALTER DATABASE SCOPED CONFIGURATION SET IDENTITY_CACHE=OFF ; 
```

## <a name="additional-resources"></a>Risorse aggiuntive

### <a name="maxdop-resources"></a>Risorse MAXDOP 
* [Indicazioni e linee guida per l'opzione di configurazione "max degree of parallelism" in SQL Server](https://support.microsoft.com/en-us/kb/2806535) 

### <a name="legacycardinalityestimation-resources"></a>Risorse LEGACY_CARDINALITY_ESTIMATION    
* [Stima della cardinalità (SQL Server)](../../relational-databases/performance/cardinality-estimation-sql-server.md)
* [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator](https://msdn.microsoft.com/library/dn673537.aspx) (Ottimizzazione dei piani di query con la stima di cardinalità di SQL Server 2014)

### <a name="parametersniffing-resources"></a>Risorse PARAMETER_SNIFFING    
* ["Dell'odore parametro!"](https://blogs.msdn.microsoft.com/queryoptteam/2006/03/31/i-smell-a-parameter/)

### <a name="queryoptimizerhotfixes-resources"></a>Risorse QUERY_OPTIMIZER_HOTFIXES    
* [SQL Server query optimizer hotfix trace flag 4199 modello di manutenzione](https://support.microsoft.com/en-us/kb/974006)

## <a name="more-information"></a>Ulteriori informazioni  
 [Sys. database_scoped_configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [Viste del catalogo di database e file &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Flag di traccia &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)   
 [Sys. Configurations &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)  
  
  

