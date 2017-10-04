---
title: CREARE DATABASE (Parallel Data Warehouse) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 52a55d6c275388e03e3f7be09d265a3b918f583f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-parallel-data-warehouse"></a>CREARE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Crea un nuovo database in un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] accessorio. Utilizzare questa istruzione per creare tutti i file associati a un database dello strumento e per impostare dimensioni massime e le opzioni di aumento automatico per le tabelle di database e log delle transazioni.  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Nome del nuovo database. Per ulteriori informazioni sui nomi di database consentiti, vedere l'argomento "Regole di denominazione di oggetti" e "Nomi riservati di Database" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 AUMENTO AUTOMATICO DELLE DIMENSIONI = ON | **OFF**  
 Specifica se il *replicated_size*, *distributed_size*, e *log_size* parametri per questo database aumenterà automaticamente in base alle esigenze oltre i relativi specificato dimensioni. Valore predefinito è **OFF**.  
  
 Se l'aumento automatico dimensioni sono impostata su ON, *replicated_size*, *distributed_size*, e *log_size* aumenteranno come obbligatorio (non in blocchi di dimensioni iniziali specificate) con ogni inserimento di dati, aggiornamento o altre azioni che richiede più spazio di archiviazione che è già stato allocato.  
  
 Se l'aumento automatico dimensioni sono impostata su OFF, le dimensioni non aumenterà automaticamente. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]verrà restituito un errore durante il tentativo di un'azione che richiede *replicated_size*, *distributed_size*, o *log_size* di crescere oltre il valore specificato.  
  
 Aumento automatico delle dimensioni è ON per tutte le dimensioni o OFF per tutte le dimensioni. Non è ad esempio possibile impostare durante l'aumento automatico delle dimensioni *log_size*, ma non impostarlo per *replicated_size*.  
  
 *replicated_size* [GB]  
 Un numero positivo. Imposta le dimensioni (in GB integer o decimale) per lo spazio totale allocato per le tabelle replicate e i corrispondenti dati *in ogni nodo di calcolo*. Per minimo e massimo *replicated_size* requisiti, vedere "Valori minimo e massimo" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se l'aumento automatico dimensioni sono impostata su ON, le tabelle replicate verranno consentite di crescere oltre questo limite.  
  
 Se l'aumento automatico dimensioni sono impostata su OFF, verrà restituito un errore se un utente tenta di creare una nuova tabella replicata, inserimento dati in un oggetto esistente replicati tabella oppure aggiornare un oggetto esistente replicati nella tabella in modo da aumenta le dimensioni di oltre *replicated_size*.  
  
 *distributed_size* [GB]  
 Un numero positivo. La dimensione, espressa in gigabyte integer o decimale, per lo spazio totale allocato alle tabelle distribuite (e i corrispondenti dati) *tra il dispositivo*. Per minimo e massimo *distributed_size* requisiti, vedere "Valori minimo e massimo" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se l'aumento automatico dimensioni sono impostata su ON, le tabelle distribuite saranno consentite di crescere oltre questo limite.  
  
 Se l'aumento automatico dimensioni sono impostata su OFF, verrà restituito un errore se un utente tenta di creare una nuova tabella distribuita, inserimento dei dati in un oggetto esistente distribuito tabella oppure aggiorna una tabella esistente distribuita in modo da aumenta le dimensioni di oltre *distributed_size* .  
  
 *log_size* [GB]  
 Un numero positivo. Le dimensioni (in GB integer o decimale) per il log delle transazioni *tra il dispositivo*.  
  
 Per minimo e massimo *log_size* requisiti, vedere "Valori minimo e massimo" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Se l'aumento automatico dimensioni sono impostata su ON, il file di log è consentito di crescere oltre questo limite. Utilizzare il [DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) istruzione per ridurre le dimensioni dei file di log fino alle dimensioni originali.  
  
 Se l'aumento automatico dimensioni sono impostata su OFF, verrà restituito un errore all'utente per qualsiasi azione che aumenta le dimensioni del log in un singolo nodo di calcolo oltre *log_size*.  
  
## <a name="permissions"></a>Permissions  
 Richiede il **CREATE ANY DATABASE** disporre dell'autorizzazione per il database master o l'appartenenza di **sysadmin** ruolo predefinito del server.  
  
 Nell'esempio seguente viene fornita l'autorizzazione per creare un database per l'utente del database Fay.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Osservazioni generali  
 I database vengono creati con livello di compatibilità 120, ovvero la compatibilità del livelli per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. In questo modo il database sarà in grado di utilizzare tutte le [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] funzionalità che utilizzano PDW.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 L'istruzione CREATE DATABASE non è consentito in una transazione esplicita. Per ulteriori informazioni, vedere [istruzioni](../../t-sql/statements/statements.md).  
  
 Per informazioni sui vincoli minimi e massimo nei database, vedere "Valori minimo e massimo" nel [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Al momento della creazione di un database, è necessario sufficiente spazio libero *in ogni nodo di calcolo* per allocare il totale combinato delle dimensioni seguenti:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]database con tabelle, le dimensioni di *replicated_table_size*.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]database con tabelle, le dimensioni di (*distributed_table_size* / numero di nodi di calcolo).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le dimensioni del log (*log_size* / numero di nodi di calcolo).  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso per l'oggetto DATABASE.  
  
## <a name="metadata"></a>Metadati  
 Dopo questa operazione ha esito positivo, una voce per il database verrà visualizzata la [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e [Sys. Objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)viste dei metadati.  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Esempi di creazione di database Basic  
 L'esempio seguente crea il database `mytest` con un'allocazione di archiviazione di 100 GB per ogni nodo di calcolo per le tabelle replicate, 500 GB per ogni dispositivo per le tabelle distribuite e 100 GB per ogni dispositivo per il log delle transazioni. In questo esempio, l'aumento automatico è disattivata per impostazione predefinita.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 L'esempio seguente crea il database `mytest` con gli stessi parametri come sopra, tranne che l'aumento automatico è attivato. In questo modo il database possono estendersi oltre i parametri di dimensione specificato.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>B. Creazione di un database con dimensioni di gigabyte parziale  
 L'esempio seguente crea il database `mytest`, con l'aumento automatico dimensioni off, un'allocazione di archiviazione di 1,5 GB per ogni nodo di calcolo per le tabelle replicate, 5,25 GB per ogni dispositivo per le tabelle distribuite e 10 GB per ogni dispositivo per il log delle transazioni.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40; Parallel Data Warehouse &#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
