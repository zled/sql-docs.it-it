---
title: sp_article_validation (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8eabbaf95392de7e5389fdd54f8724045682ec2a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32991568"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inizializza una richiesta di convalida dei dati per l'articolo specificato. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione e nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione che include l'articolo. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo da convalidare. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@rowcount_only=**] *type_of_check_requested*  
 Indica se per la tabella viene restituito solo il conteggio delle righe. *type_of_check_requested* viene **smallint**, il valore predefinito è **1**.  
  
 Se **0**, eseguire un conteggio delle righe e un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 checksum compatibile.  
  
 Se **1**, eseguire solo un controllo del conteggio delle righe.  
  
 Se **2**, eseguire un conteggio delle righe e checksum binario.  
  
 [  **@full_or_fast=**] *full_or_fast*  
 Metodo utilizzato per il conteggio delle righe. *full_or_fast* viene **tinyint**, e può essere uno dei valori seguenti.  
  
|**Valore**|**Description**|  
|---------------|---------------------|  
|**0**|Esegue un conteggio completo tramite COUNT(*).|  
|**1**|Esegue un conteggio rapido in **sysindexes**. Il conteggio delle righe in **sysindexes** è più veloce rispetto al conteggio delle righe nella tabella effettiva. Tuttavia, **sysindexes** viene aggiornato in modo differito, e il conteggio delle righe potrebbe non essere accurata.|  
|**2** (impostazione predefinita)|Esegue un conteggio rapido condizionale eseguendo innanzitutto un tentativo con il metodo rapido. Se il metodo rapido evidenzia delle differenze, viene applicato il metodo completo. Se *expected_rowcount* è NULL e la stored procedure viene utilizzata per ottenere il valore, viene utilizzato sempre un Count completo.|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 Indica se l'esecuzione dell'agente di distribuzione viene interrotta immediatamente al termine della convalida. *shutdown_agent* viene **bit**, il valore predefinito è **0**. Se **0**, l'agente di distribuzione non viene arrestato. Se **1**, l'agente di distribuzione viene interrotta al termine della convalida dell'articolo.  
  
 [ **@subscription_level=**] *subscription_level*  
 Indica se la convalida viene prelevata o meno da un set di Sottoscrittori. *subscription_level* viene **bit**, il valore predefinito è **0**. Se **0**, la convalida viene applicata a tutti i sottoscrittori. Se **1**, la convalida viene applicata solo a un subset dei sottoscrittori specificati tramite chiamate a **sp_marksubscriptionvalidation** nella transazione aperta corrente.  
  
 [  **@reserved=**] *riservato*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@publisher**=] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato quando si richiede la convalida in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_article_validation** viene utilizzata nella replica transazionale.  
  
 **sp_article_validation** fa sì che le informazioni di convalida di sull'articolo specificato e invia una richiesta di convalida nel log delle transazioni. Quando l'agente di distribuzione riceve la richiesta, confronta le informazioni di convalida incluse nella richiesta con quelle della tabella del Sottoscrittore. I risultati della convalida vengono visualizzati negli avvisi di Monitoraggio replica e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo gli utenti con autorizzazioni SELEZIONANO ALL nella tabella di origine per l'articolo convalidato può eseguire **sp_article_validation**.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalida dei dati replicati](../../relational-databases/replication/validate-replicated-data.md)   
 [sp_marksubscriptionvalidation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
