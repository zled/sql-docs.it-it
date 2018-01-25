---
title: CREARE il gruppo di carico di lavoro (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WORKLOAD GROUP
- WORKLOAD_GROUP_TSQL
- CREATE WORKLOAD GROUP
- CREATE_WORKLOAD_GROUP_TSQL
dev_langs: TSQL
helpviewer_keywords: CREATE WORKLOAD GROUP statement
ms.assetid: d949e540-9517-4bca-8117-ad8358848baa
caps.latest.revision: "47"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cec1360259d78679fab31a45a074d5fbbf3779b5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-workload-group-transact-sql"></a>CREATE WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un gruppo del carico di lavoro di Resource Governor e lo associa al pool di risorse di Resource Governor. Resource Governor non è disponibile in ogni edizione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE WORKLOAD GROUP group_name  
[ WITH  
    ( [ IMPORTANCE = { LOW | MEDIUM | HIGH } ]  
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]  
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]  
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]   
      [ [ , ] MAX_DOP = value ]  
      [ [ , ] GROUP_MAX_REQUESTS = value ] )  
 ]  
[ USING {   
    [ pool_name | "default" ]    
    [ [ , ] EXTERNAL external_pool_name | "default" ] ]   
    } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *group_name*  
 Nome definito dall'utente per il gruppo di carico di lavoro. *nome_gruppo* è un valore alfanumerico, può essere fino a 128 caratteri, deve essere univoco all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e deve essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 IMPORTANZA = {BASSO | **MEDIA** | ELEVATA}  
 Specifica l'importanza relativa di una richiesta nel gruppo del carico di lavoro. L'importanza è compresa fra le seguenti, MEDIUM è l'impostazione predefinita:  
  
-   LOW  
-   MEDIUM (valore predefinito)    
-   HIGH  
  
> [!NOTE]  
> Internamente, ogni impostazione dell'importanza viene memorizzata come un numero utilizzato per i calcoli.  
  
 IMPORTANCE è locale al pool di risorse. I gruppi di carico di lavoro con diversa importanza e interni allo stesso pool di risorse influiscono l'uno sull'altro, ma non sui gruppi di carico di lavoro in un altro pool di risorse.  
  
 REQUEST_MAX_MEMORY_GRANT_PERCENT =*value*  
 Specifica la quantità massima di memoria che una singola richiesta può accettare dal pool. La percentuale è relativa alla dimensioni del pool di risorse specificata da MAX_MEMORY_PERCENT.  
  
> [!NOTE]  
> La quantità specificata si riferisce solo alla memoria di concessione per l'esecuzione della query.  
  
 *valore* deve essere 0 o un numero intero positivo. L'intervallo consentito per *valore* è compreso tra 0 e 100. L'impostazione predefinita per *valore* è 25.  
  
 Si noti quanto segue:  
  
-   Impostazione *valore* su 0 impedisce che le query con operazioni SORT e HASH JOIN nei gruppi del carico di lavoro definiti dall'utente in esecuzione.  
  
-   Non è consigliabile impostazione *valore* maggiore di 70 perché il server potrebbe essere Impossibile riservare memoria disponibile insufficiente se vengono eseguite altre query simultanee. È possibile che venga restituito l'errore di timeout query 8645.  
  
> [!NOTE]  
>  Se i requisiti di memoria della query superano il limite specificato da questo parametro, il server effettua le operazioni seguenti:  
>   
>  Per i gruppi di carico di lavoro definiti dall'utente, il server tenta di ridurre il grado di parallelismo delle query fino a quando i requisiti di memoria non rientrano nel limite o fino a quando il grado di parallelismo non è uguale a 1. Se i requisiti di memoria delle query sono ancora superiori al limite, si verifica l'errore 8657.  
>   
>  Per i gruppi di carico di lavoro interni e predefiniti, il server permette alla query di ottenere la memoria necessaria.  
>   
>  In entrambi i casi, è possibile che si verifichi l'errore di timeout 8645 se il server non dispone di memoria fisica sufficiente.  
  
 REQUEST_MAX_CPU_TIME_SEC =*value*  
 Viene specificato il tempo massimo della CPU, in secondi, utilizzabile da una richiesta. *valore* deve essere 0 o un numero intero positivo. L'impostazione predefinita per *valore* è 0, ovvero un tempo illimitato.  
  
> [!NOTE]  
> Per impostazione predefinita, Resource Governor non impedirà una richiesta di continuare se viene superato il tempo massimo. ma verrà generato un evento. Per ulteriori informazioni, vedere [CPU soglia di questa classe di evento](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).  

> [!IMPORTANT]
> A partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 e l'utilizzo di [2422 flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md), Resource Governor verrà interrotta una richiesta quando viene superato il tempo massimo. 
  
 REQUEST_MEMORY_GRANT_TIMEOUT_SEC =*value*  
 Specifica il tempo massimo, in secondi, che una query può attendere prima che una concessione di memoria (memoria buffer di lavoro) diventi disponibile.  
  
> [!NOTE]  
>  L'esecuzione della query può riuscire anche in caso di timeout relativo alla concessione di memoria. L'esito negativo di una query si verifica solo se sono in esecuzione più query simultaneamente. In caso contrario, la query può ottenere solo la minima concessione di memoria, con una conseguente riduzione delle prestazioni.  
  
 *valore* deve essere 0 o un numero intero positivo. L'impostazione predefinita per *valore*, 0, utilizza un calcolo interno basato sul costo della query per determinare il tempo massimo.  
  
 MAX_DOP =*value*  
 Viene specificato il grado massimo di parallelismo (DOP) per le richieste parallele. *valore* deve essere 0 o un numero intero positivo. L'intervallo consentito per *valore* è compreso tra 0 e 64. L'impostazione predefinita per *valore*, 0, utilizza l'impostazione globale. MAX_DOP viene gestito nel modo seguente:  
  
-   MAX_DOP, inteso come hint per la query, è efficace fintanto che non supera il valore MAX_DOP del gruppo del carico di lavoro. Se l'hint per la query MAXDOP supera il valore configurato con Resource Governor, nel motore di database viene utilizzato il valore MAXDOP di Resource Governor.  
  
-   MAX_DOP, inteso come hint per la query, ha sempre la precedenza sull'opzione "max degree of parallelism" di sp_configure.  
  
-   Il valore MAX_DOP del gruppo di carico di lavoro ha sempre la precedenza sull'opzione "max degree of parallelism" di sp_configure.  
  
-   Se la query viene contrassegnata come seriale in fase di compilazione, durante l'esecuzione non potrà ritornare a parallela, indipendentemente dal gruppo del carico di lavoro o dall'impostazione sp_configure.  
  
-   Dopo la configurazione di DOP, è possibile diminuire solo la richiesta di memoria concessa. La riconfigurazione del gruppo di carico di lavoro non è visibile durante l'attesa nella coda della memoria concessa.  
  
 GROUP_MAX_REQUESTS =*value*  
 Viene specificato il numero massimo di richieste simultanee eseguibili nel gruppo del carico di lavoro. *valore* deve essere 0 o un numero intero positivo. L'impostazione predefinita per *valore*, 0 consente richieste illimitate. Quando viene raggiunto il numero massimo di richieste simultanee, un utente in quel gruppo può effettuare l'accesso, ma viene posizionato in uno stato di attesa fino a quando le richieste simultanee non sono inferiori al valore specificato.  
  
 Utilizzare { *pool_name* | **"default"** }  
 Associa il gruppo di carico con il pool di risorse definiti dall'utente identificato da *pool_name*. In questo modo, il gruppo del carico di lavoro viene inserito nel pool di risorse. Se *pool_name* non viene specificato, o se l'argomento USING non è utilizzato, il gruppo di carico di lavoro viene inserito nel pool predefinito di Resource Governor.  
  
 "default" è una parola riservata e, se utilizzata con USING, deve essere delimitata da virgolette ("") o parentesi quadre ([]).  
  
> [!NOTE]  
>  Per i gruppi di carico di lavoro e i pool di risorse predefiniti vengono utilizzati sempre nomi scritti in lettere minuscole, ad esempio "default". Questo aspetto deve essere preso in considerazione per i server in cui vengono utilizzate regole di confronto con distinzione tra maiuscole e minuscole. In server con regole di confronto senza distinzione tra maiuscole e minuscole, ad esempio SQL_Latin1_General_CP1_CI_AS, le parole "default" e "Default" vengono considerate uguali.  
  
 External_pool_name esterno | "default"  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 Gruppo di carico di lavoro è possibile specificare un pool di risorse esterne. È possibile definire un gruppo di carico di lavoro e associare i pool di 2:  
  
-   Un pool di risorse per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] carichi di lavoro e query  
  
-   Un pool di risorse esterne per i processi esterni. Per ulteriori informazioni, vedere [sp_execute_external_script &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 REQUEST_MEMORY_GRANT_PERCENT: per la creazione dell'indice è possibile utilizzare più memoria per area di lavoro di quella concessa inizialmente al fine di ottenere prestazioni ottimali. Tale gestione particolare è supportata da Resource Governor in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. La concessione iniziale, così come qualsiasi concessione supplementare, è tuttavia limitata dalle impostazioni del pool di risorse e del gruppo di carico di lavoro.  
  
 **Creazione dell'indice in una tabella partizionata**  
  
 La quantità di memoria utilizzata per la creazione dell'indice in una tabella partizionata non allineata è proporzionale al numero di partizioni coinvolte. Se la memoria totale necessaria supera il limite per query (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposto dal gruppo di carico di lavoro di Resource Governor, la creazione dell'indice potrebbe non riuscire. Poiché il gruppo di carico di lavoro "default" consente a una query di superare il limite per query con la memoria minima necessaria, l'utente potrebbe essere in grado di eseguire la stessa creazione dell'indice in un gruppo di carico di lavoro "default", se nel pool di risorse "default" è configurata una quantità di memoria totale sufficiente per eseguire la query.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio riportato di seguito viene mostrato come creare un gruppo del carico di lavoro denominato `newReports`. Utilizza le impostazioni predefinite di Resource Governor ed è contenuto nel pool predefinito di Resource Governor. Nell'esempio viene specificato il pool `default`, ma questo non è necessario.  
  
```  
CREATE WORKLOAD GROUP newReports  
    USING "default" ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

