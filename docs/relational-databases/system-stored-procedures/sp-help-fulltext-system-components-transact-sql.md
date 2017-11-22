---
title: sp_help_fulltext_system_components (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_components_TSQL
- sp_help_fulltext_components
dev_langs: TSQL
helpviewer_keywords: sp_help_fulltext_system_components
ms.assetid: ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce
caps.latest.revision: "52"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26fe1082febf06892e1f6fb601f121c6b66fdf10
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpfulltextsystemcomponents-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Restituisce informazioni per i word breaker, il filtro e i gestori di protocollo registrati. **sp_help_fulltext_system_components** restituisce inoltre un elenco di identificatori dei database e cataloghi full-text che hanno utilizzato il componente specificato.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_fulltext_system_components   
         { 'all'| [ @component_type = ] 'component_type' }  
    , [ @param = ] 'param'  
```  
  
## <a name="arguments"></a>Argomenti  
 'all'  
 Restituisce informazioni per tutti i componenti full-text.  
  
 [  **@component_type=** ] *component_type*  
 Specifica il tipo di componente. *component_type* può essere uno dei seguenti:  
  
-   **Word breaker**  
  
-   **filter**  
  
-   **gestore di protocollo**  
  
-   **FullPath**  
  
 Se viene specificato un percorso completo, *param* deve essere specificato anche con il percorso completo per il componente DLL, altrimenti viene restituito un messaggio di errore.  
  
 [  **@param=** ] *param*  
 In base al tipo di componente, i possibili valori sono i seguenti: identificatore delle impostazioni locali (LCID), estensione di file con prefisso ".", nome completo del componente del gestore di protocollo o percorso completo della DLL del componente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Il set di risultati seguente viene restituito per i componenti di sistema.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**componentType**|**sysname**|Tipo di componente. I tipi validi sono:<br /><br /> filter<br /><br /> protocol handler<br /><br /> wordbreaker|  
|**componentname**|**sysname**|Nome del componente.|  
|**CLSID**|**uniqueidentifier**|Identificatore della classe del componente.|  
|**FullPath**|**nvarchar(256)**|Percorso della posizione del componente.<br /><br /> NULL = il chiamante non è un membro di **serveradmin** ruolo predefinito del server.|  
|**version**|**nvarchar (30)**|Versione del componente.|  
|**produttore**|**sysname**|Nome del produttore del componente.|  
  
 Il set di risultati seguente viene restituito solo se uno o più di un catalogo full-text esistente che utilizza *component_type*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**DBID**|**int**|ID del database.|  
|**ftcatid**|**int**|ID del catalogo full-text.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **pubblica** ruolo; tuttavia, gli utenti possono solo visualizzare o meno informazioni sui cataloghi full-text per cui dispongono dell'autorizzazione VIEW DEFINITION. Solo i membri del **serveradmin** ruolo predefinito del server è possibile visualizzare valori di **fullpath** colonna.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo è di particolare importanza durante la preparazione per un aggiornamento. Eseguire la stored procedure all'interno di un particolare database e utilizzare l'output per determinare se l'aggiornamento avrà effetti su un particolare catalogo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-all-full-text-system-components"></a>A. Elenco di tutti i componenti di sistema full-text  
 Nell'esempio seguente vengono elencati tutti i componenti di sistema full-text registrati sull'istanza server.  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>B. Elenco di word breaker  
 Nell'esempio seguente vengono elencati tutti i word breaker registrati sull'istanza del servizio.  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>C. Determinazione della registrazione di un word breaker specifico  
 Nell'esempio seguente viene elencato il word breaker per la lingua turca (LCID = 1055) se è stato installato nel sistema e registrato sull'istanza del servizio. Questo esempio vengono specificati i nomi di parametro,  **@component_type**  e  **@param** .  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 Per impostazione predefinita, questo word breaker non è installato, pertanto il set di risultati è vuoto.  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>D. Determinazione della registrazione di un filtro specifico  
 Nell'esempio seguente viene elencato il filtro per il componente xdoc se è stato manualmente installato nel sistema e registrato sull'istanza del server.  
  
```  
EXEC sp_help_fulltext_system_components 'filter', '.xdoc';  
GO  
```  
  
 Per impostazione predefinita, questo filtro non è installato, pertanto il set di risultati è vuoto.  
  
### <a name="e-listing-a-specific-dll-file"></a>E. Elenco di un file dll specifico  
 Nell'esempio seguente viene elencato un file con estensione ddl specifico, `nlhtml.dll`, installato per impostazione predefinita.  
  
```  
EXEC sp_help_fulltext_system_components 'fullpath',   
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\nlhtml.dll';  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione o modifica di Word breaker e filtri registrati](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [Configurazione e gestione di word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurazione e gestione di filtri per la ricerca](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Ricerca full-Text e semantica Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
