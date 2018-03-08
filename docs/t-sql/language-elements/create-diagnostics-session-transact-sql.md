---
title: CREATE DIAGNOSTICS SESSION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d869ed18b07f824ffa4cc3fc8b746ded5242ed99
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-diagnostics-session-transact-sql"></a>CREATE DIAGNOSTICS SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Le sessioni di diagnostica consentono di salvare le informazioni di diagnostica dettagliate definite dall'utente, sulle prestazioni del sistema o di query.  
  
 Le sessioni di diagnostica vengono in genere utilizzate per eseguire il debug delle prestazioni per una query specifica o per monitorare il funzionamento di un componente specifico di dispositivo durante l'operazione di dispositivo.  
  
> [!NOTE]  
>  È necessario conoscere il linguaggio XML per utilizzare le sessioni di diagnostica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Creating a new diagnostics session:  
CREATE DIAGNOSTICS SESSION diagnostics_name AS N’{<session_xml>}’;  
  
<session_xml>::  
<Session>  
   [ <MaxItemCount>max_item_count_num</MaxItemCount> ]  
   <Filter>  
      { \<Event Name=”event_name”/>  
         [ <Where>\<filter_property_name Name=”value” ComparisonType="comp_type"/></Where> ] [ ,...n ]  
      } [ ,...n ]  
   </Filter> ]   
   <Capture>  
      \<Property Name=”property_name”/> [ ,...n ]  
   </Capture>  
<Session>  
  
Retrieving results for a diagnostics session:  
SELECT * FROM master.sysdiag.diagnostics_name ;  
  
Removing results for a diagnostics session:  
DROP DIAGNOSTICS SESSION diagnostics_name ;  
```  
  
## <a name="arguments"></a>Argomenti  
 *diagnostics_name*  
 Il nome della sessione di diagnostica. I nomi di sessione di diagnostica possono contenere caratteri a-z, A-Z e 0-9 solo. Inoltre, i nomi di sessione di diagnostica devono iniziare con un carattere. *diagnostics_name* è limitato a 127 caratteri.  
  
 *max_item_count_num*  
 Il numero di eventi che deve essere mantenuta in una vista. Ad esempio, se si specifica di 100, 100 eventi più recenti corrispondenti ai criteri di filtro verranno resa persistente per la sessione di diagnostica. Se vengono trovati meno di 100 eventi, la sessione di diagnostica conterrà minore di 100 eventi. *max_item_count_num* deve essere almeno pari a 100 e minore o uguale a 100.000.  
  
 *event_name*  
 Definisce gli eventi effettivi per raccogliere i dati della sessione di diagnostica.  *EVENT_NAME* è uno degli eventi elencati in [sys.pdw_diag_events](http://msdn.microsoft.com/en-us/d813aac0-cea1-4f53-b8e8-d26824bc2587) in `sys.pdw_diag_events.is_enabled='True'`.  
  
 *filter_property_name*  
 Il nome della proprietà su cui si desidera limitare i risultati. Se si desidera limitare in base all'id di sessione, ad esempio *filter_property_name* deve essere *SessionId*. Vedere *property_name* sotto per un elenco di valori potenziali per *filter_property_name*.  
  
 *Valore*  
 Un valore da valutare rispetto *filter_property_name*. Il tipo di valore deve corrispondere al tipo di proprietà. Ad esempio, se il tipo della proprietà è di tipo decimal, il tipo di *valore* deve essere decimale.  
  
 *comp_type*  
 Il tipo di confronto. Possibili valori sono: uguale a, EqualsOrGreaterThan, EqualsOrLessThan, GreaterThan, LessThan, diverso da, Contains, RegEx  
  
 *property_name*  
 Proprietà correlate all'evento.  I nomi di proprietà possono essere parte del tag di acquisizione o utilizzato come parte di criteri di filtro.  
  
|Nome proprietà|Description|  
|-------------------|-----------------|  
|UserName|Un nome utente (account di accesso).|  
|SessionId|Un ID sessione.|  
|QueryId|Un ID di query.|  
|CommandType|Un tipo di comando.|  
|CommandText|Testo all'interno di un comando di elaborazione.|  
|Tipo operazione|Il tipo di operazione per l'evento.|  
|Durata|La durata dell'evento.|  
|SPID|L'ID di processo del servizio.|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni utente è consentito un massimo di 10 sessioni simultanee di diagnostica. Vedere [sys.pdw_diag_sessions](http://msdn.microsoft.com/en-us/ca111ddc-2787-4205-baf0-1a242c0257a9) per un elenco delle sessioni correnti e drop non necessari tramite sessioni `DROP DIAGNOSTICS SESSION`.  
  
 Le sessioni di diagnostica continuerà a raccogliere i metadati fino all'eliminazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **ALTER SERVER STATE** autorizzazione.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso sulla tabella sessioni di diagnostica.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-diagnostics-session"></a>A. Creazione di una sessione di diagnostica  
 Questo esempio viene creata una sessione di diagnostica per registrare le metriche delle prestazioni del motore di database. Nell'esempio viene creata una sessione di diagnostica che è in attesa di eventi di Query del motore in esecuzione e di fine e un blocco eventi DMS. Ciò che viene restituito è il testo del comando, nome computer, l'id della richiesta (id di query) e la sessione di cui è stato creato l'evento.  
  
```  
CREATE DIAGNOSTICS SESSION MYDIAGSESSION AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:EngineQueryRunningEvent" />  
      <Event Name="DmsCoreInstrumentation:DmsBlockingQueueEnqueueBeginEvent" />  
      <Where>  
         <SessionId Value="381" ComparisonType="NotEquals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Query.CommandText" />  
      <Property Name="MachineName" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Alias" />  
      <Property Name="Duration" />  
      <Property Name="Session.SessionId" />  
   </Capture>  
</Session>';  
```  
  
 Dopo la creazione della sessione di diagnostica, eseguire una query.  
  
```  
SELECT COUNT(EmployeeKey) FROM AdventureWorksPDW2012..FactSalesQuota;  
```  
  
 Selezionando dallo schema sysdiag quindi visualizzare i risultati della sessione di diagnostica.  
  
```  
SELECT * FROM master.sysdiag.MYDIAGSESSION;  
```  
  
 Si noti che lo schema sysdiag contiene una visualizzazione che è il nome di sessione di diagnostica.  
  
 Per visualizzare solo l'attività per la connessione, aggiungere il `Session.SPID` proprietà e aggiungere `WHERE [Session.SPID] = @@spid;` alla query.  
  
 Quando si è concluso la sessione di diagnostica, rimuoverla mediante il **DROP diagnostica** comando.  
  
```  
DROP DIAGNOSTICS SESSION MYDIAGSESSION;  
```  
  
### <a name="b-alternative-diagnostic-session"></a>B. Sessione di diagnostica alternativa  
 Un altro esempio con proprietà leggermente diverse.  
  
```  
-- Determine the session_id of your current session  
SELECT TOP 1 session_id();  
-- Replace \<*session_number*> in the code below with the numbers in your session_id  
CREATE DIAGNOSTICS SESSION PdwOptimizationDiagnostics AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:MemoGenerationBeginEvent" />  
      <Event Name="EngineInstrumentation:MemoGenerationEndEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationBeginEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationEndEvent" />  
      <Event Name="DSQLInstrumentation:BuildRelOpContextTreeBeginEvent" />  
      <Event Name="DSQLInstrumentation:PostPlanGenModifiersEndEvent" />  
      <Where>  
         <SessionId Value="\<*session_number*>" ComparisonType="Equals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Session.SessionId" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Query.CommandText" />  
      <Property Name="Name" />  
      <Property Name="DateTimePublished" />  
      <Property Name="DateTimePublished.Ticks" />  
  </Capture>  
</Session>';  
```  
  
 Eseguire una query, ad esempio:  
  
```  
USE ssawPDW;  
GO  
SELECT * FROM dbo.FactFinance;  
```  
  
 La query seguente restituisce l'intervallo di autorizzazione:  
  
```  
SELECT *   
FROM master.sysdiag.PdwOptimizationDiagnostics   
ORDER BY DateTimePublished;  
```  
  
 Quando si è concluso la sessione di diagnostica, rimuoverla mediante il **DROP diagnostica** comando.  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  
