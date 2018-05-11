---
title: CREATE DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a7cef1f977e59e8145a57c806d7edaeb262b1275
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="create-database-parallel-data-warehouse"></a>CREATE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crea un nuovo database in un'appliance [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Usare questa istruzione per creare tutti i file associati a un database di appliance e per impostare le opzioni relative alle dimensioni massime e all'aumento automatico per le tabelle e i log delle transazioni del database stesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE DATABASE database_name   
WITH (   
    [ AUTOGROW = ON | OFF , ]   
    REPLICATED_SIZE = replicated_size [ GB ] ,  
    DISTRIBUTED_SIZE = distributed_size [ GB ] ,  
    LOG_SIZE = log_size [ GB ] )  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del nuovo database. Per altre informazioni sui nomi di database consentiti, vedere le sezioni relative alle regole di denominazione degli oggetti e ai nomi di database riservati nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 AUTOGROW = ON | **OFF**  
 Specifica se i parametri *replicated_size*, *distributed_size* e *log_size* per il database possono aumentare automaticamente in base alle esigenze oltre le dimensioni specificate. Il valore predefinito è **OFF**.  
  
 Se AUTOGROW corrisponde a ON, *replicated_size*, *distributed_size* e *log_size* aumenteranno secondo necessità (non in blocchi delle dimensioni specificate inizialmente) a ogni inserimento o aggiornamento di dati o quando vengono eseguite altre azioni che richiedono più spazio di archiviazione di quanto ne sia già stato allocato.  
  
 Se AUTOGROW corrisponde a OFF, le dimensioni non aumenteranno automaticamente. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] restituisce un errore se si tenta di eseguire un'azione che richiede l'aumento di *replicated_size*, *distributed_size* o *log_size* oltre i rispettivi valori specificati.  
  
 L'impostazione di AUTOGROW (ON o OFF) si applica a tutte le dimensioni. Non è ad esempio possibile impostare AUTOGROW su ON per *log_size* ma non per *replicated_size*.  
  
 *replicated_size* [ GB ]  
 Numero positivo. Imposta le dimensioni (in GB, con un valore intero o decimale) per lo spazio totale allocato per le tabelle replicate e per i dati corrispondenti *in ogni nodo di calcolo*. Per i requisiti minimo e massimo di *replicated_size*, vedere la sezione corrispondente nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se AUTOGROW corrisponde a ON, è consentito l'aumento delle tabelle replicate oltre il limite impostato.  
  
 Se AUTOGROW corrisponde a OFF, verrà restituito un errore se un utente tenta di creare una nuova tabella replicata, di inserire dati in una tabella replicata esistente o di aggiornare quest'ultima in modo tale da aumentarne le dimensioni oltre il valore di *replicated_size*.  
  
 *distributed_size* [ GB ]  
 Numero positivo. Dimensioni (in GB, con un valore intero o decimale) per lo spazio totale allocato per le tabelle distribuite e per i dati corrispondenti *nell'intera appliance*. Per i requisiti minimo e massimo di *distributed_size*, vedere la sezione corrispondente nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se AUTOGROW corrisponde a ON, è consentito l'aumento delle tabelle distribuite oltre il limite impostato.  
  
 Se AUTOGROW corrisponde a OFF, verrà restituito un errore se un utente tenta di creare una nuova tabella distribuita, di inserire dati in una tabella distribuita esistente o di aggiornare quest'ultima in modo tale da aumentarne le dimensioni oltre il valore di *distributed_size*.  
  
 *log_size* [ GB ]  
 Numero positivo. Dimensioni (in GB, con un valore intero o decimale) per il log delle transazioni *nell'intera appliance*.  
  
 Per i requisiti minimo e massimo di *log_size*, vedere la sezione corrispondente nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se AUTOGROW corrisponde a ON, è consentito l'aumento del file di log oltre il limite impostato. Usare l'istruzione [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) per ridurre le dimensioni dei file di log fino alle dimensioni originali.  
  
 Se AUTOGROW corrisponde a OFF, verrà restituito un errore per qualsiasi azione che aumenti le dimensioni del log in un singolo nodo di calcolo oltre il valore di *log_size*.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione **CREATE ANY DATABASE** nel database master o l'appartenenza al ruolo predefinito del server **sysadmin**.  
  
 Nell'esempio seguente viene fornita l'autorizzazione per creare un database per l'utente del database Fay.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I database vengono creati con livello di compatibilità 120, corrispondente al livello di compatibilità per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. In questo modo il database sarà in grado di usare tutte le funzionalità [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] che usano PDW.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 L'istruzione CREATE DATABASE non è consentita in una transazione esplicita. Per altre informazioni, vedere [Istruzioni](../../t-sql/statements/statements.md).  
  
 Per informazioni sui vincoli minimi e massimi nei database, vedere la sezione relativa ai valori minimi e massimi nella [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Al momento della creazione di un database, deve essere disponibile spazio sufficiente *in ogni nodo di calcolo* per allocare il totale combinato delle dimensioni seguenti:  
  
-   Database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con tabelle di dimensioni corrispondenti a *replicated_table_size*.  
  
-   Database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con tabelle di dimensioni corrispondenti a (*distributed_table_size*/numero di nodi di calcolo).  
  
-   Log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] delle dimensioni corrispondenti a (*log_size*/numero di nodi di calcolo).  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Consente di acquisire un blocco condiviso per l'oggetto DATABASE.  
  
## <a name="metadata"></a>Metadati  
 Al termine di questa operazione, nelle viste di metadati [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) viene visualizzata una voce per questo database.  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Esempi di creazione di database di base  
 L'esempio seguente crea il database `mytest` con un'allocazione dello spazio di archiviazione pari a 100 GB per ogni nodo di calcolo per le tabelle replicate, 500 GB per appliance per le tabelle distribuite e 100 GB per appliance per il log delle transazioni. In questo esempio, AUTOGROW è OFF per impostazione predefinita.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 L'esempio seguente crea il database `mytest` con gli stessi parametri dell'esempio precedente, ad eccezione di AUTOGROW, che è ON. Ciò consente al database di aumentare oltre i parametri di dimensione specificati.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>B. Creazione di un database con dimensioni in GB parziali  
 L'esempio seguente crea il database `mytest` con AUTOGROW OFF, un'allocazione dello spazio di archiviazione pari a 1,5 GB per ogni nodo di calcolo per le tabelle replicate, 5,25 GB per appliance per le tabelle distribuite e 10 GB per appliance per il log delle transazioni.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
