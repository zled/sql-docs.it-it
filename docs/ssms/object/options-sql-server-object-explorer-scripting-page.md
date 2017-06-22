---
title: Opzioni (Esplora oggetti di SQL Server - pagina Generazione script) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d5353c0732833516e95cc734a2d7bbe0f1258554
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="options-sql-server-object-explorer---scripting-page"></a>Opzioni (Esplora oggetti di SQL Server - pagina Generazione script)
Usare questa pagina per impostare le opzioni di scripting valide per i comandi seguenti dei menu di scelta rapida degli oggetti in **Esplora oggetti**:  
  
-   Comandi **Modifica** per tabelle e viste utente.  
  
-   Comandi **Crea script<object> per** per oggetti creati dall'utente.  
  
-   Comandi **Modifica** per oggetti creati dall'utente.  
  
-   Questa pagina consente inoltre di impostare i valori predefiniti per le opzioni di creazione di script per **Generazione guidata script di SQL Server**.  
  
## <a name="remarks"></a>Osservazioni  
I comandi **Modifica** e **Cambia** potrebbero produrre risultati diversi rispetto al comando **Crea script <object> per** con la stessa impostazione dell'opzione. I comandi **Modifica** e **Cambia** sono infatti stati creati per modificare oggetti nel database corrente durante una sessione dell'editor di query. Il comando **Crea script<object> per** è invece stato creato per generare uno script affinché possa essere usato in seguito per la creazione di oggetti.  
  
## <a name="options"></a>Opzioni  
Specificare le opzioni di scripting selezionando le impostazioni desiderate tra quelle disponibili nell'elenco visualizzato a destra di ciascuna opzione.  
  
### <a name="general-scripting-options"></a>Opzioni generali di scripting  
**Delimita singole istruzioni**  
Consente di separare istruzioni [!INCLUDE[tsql](../../includes/tsql_md.md)] singole utilizzando un separatore batch. Per modificare il separatore batch predefinito per l' **editor di query**, scegliere **Strumenti**/**Opzioni**/**Esecuzione query**/**SQL Server**/**Generale**/**Separatore batch**. Il valore predefinito è False. Per altre informazioni, vedere [GO (Transact-SQL)](http://msdn.microsoft.com/en-us/b2ca6791-3a07-4209-ba8e-2248a92dd738).  
  
**Includi intestazioni descrittive**  
Consente di aggiungere commenti descrittivi allo script dividendolo in sezioni per ogni oggetto. Il valore predefinito è True. Per altre informazioni, vedere [/*...*/ (Comment) (Transact-SQL)](http://msdn.microsoft.com/en-us/4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c).  
  
**Includi opzioni vardecimal**  
Consente di includere le opzioni per l'archiviazione vardecimal. Il valore predefinito è False. Per altre informazioni, vedere [sp_db_vardecimal_storage_format (Transact-SQL)](http://msdn.microsoft.com/en-us/9920b2f7-b802-4003-913c-978c17ae4542).  
  
**Genera script per il rilevamento modifiche**  
Consente di includere nello script le informazioni sul rilevamento delle modifiche.  
  
**Script per versione server**  
Consente di creare uno script eseguibile nella versione selezionata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Non è possibile creare script per versioni precedenti per le nuove funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] . Alcuni script creati per [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] non possono essere eseguiti in server con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]o in un database con un' [impostazione del livello di compatibilità del database](http://msdn.microsoft.com/en-us/ca5fd220-d5ea-4182-8950-55d4101a86f6)precedente.  
  
**Script per cataloghi full-text**  
Consente di includere uno script per cataloghi full-text. Il valore predefinito è False. Per altre informazioni, vedere [CREATE FULLTEXT CATALOG (Transact-SQL)](http://msdn.microsoft.com/en-us/d7a8bd93-e2d7-4a40-82ef-39069e65523b).  
  
**Script per USE <database>**  
Aggiunge l'istruzione USE DATABASE allo script per creare oggetti di database nel contesto del database di **Esplora oggetti** corrente. Se si prevede di utilizzare lo script in un database diverso, selezionare False per omettere tale istruzione. Il valore predefinito è True. Per altre informazioni, vedere [USE (Transact-SQL)](http://msdn.microsoft.com/en-us/c05acac8-c063-4770-8e36-d7f71d500b10).  
  
### <a name="object-scripting-options"></a>Opzioni di scripting per gli oggetti  
**Genera script per oggetti dipendenti**  
Consente di generare uno script per oggetti aggiuntivi, richiesti quando viene eseguito lo script per l'oggetto selezionato. Il valore predefinito è False.  
  
**Includi clausola IF NOT EXISTS**  
Consente di includere un'istruzione per verificare che ogni oggetto non sia presente nel database prima del tentativo di crearlo. Il valore predefinito è False. Per altre informazioni, vedere [IF...ELSE (Transact-SQL)](http://msdn.microsoft.com/en-us/676c881f-dee1-417a-bc51-55da62398e81) e [EXISTS (Transact-SQL)](http://msdn.microsoft.com/en-us/b6510a65-ac38-4296-a3d5-640db0c27631).  
  
**Schema per qualifica dei nomi degli oggetti**  
Consente di qualificare il nome degli oggetti con lo schema dell'oggetto. Il valore predefinito è False. Per altre informazioni, vedere [Creazione di uno schema di database](http://msdn.microsoft.com/en-us/ed2a5522-f4d2-4111-95a4-d3e1e5081739).  
  
**Script per proprietà estese**  
Consente di includere le proprietà estese nello script qualora l'oggetto disponga di proprietà estese. Il valore predefinito è False. Per altre informazioni, vedere [sp_addextendedproperty (Transact-SQL)](http://msdn.microsoft.com/en-us/565483ea-875b-4133-b327-d0006d2d7b4c).  
  
**Proprietario script**  
Consente di includere il proprietario nello script generato. Il valore predefinito è False.  
  
**Script per autorizzazioni**  
Consente di includere autorizzazioni sugli oggetti di database nello script. Il valore predefinito è True. Per altre informazioni, vedere [Autorizzazioni](http://msdn.microsoft.com/en-us/f28e3dea-24e6-4a81-877b-02ec4c7e36b9).  
  
### <a name="tableview-options"></a>Opzioni tabella/vista  
Le opzioni seguenti si applicano solo agli script per tabelle o viste.  
  
**Converti tipi di dati definiti dall'utente in tipi di base**  
Consente di convertire i tipi di dati definiti dall'utente nei tipi di base da cui sono stati creati. Utilizzare True se il tipo di dati definito dall'utente nel database di origine non è presente nel database in cui lo script verrà eseguito. Utilizzare False per mantenere i tipi di dati definiti dall'utente. Il valore predefinito è False. Per altre informazioni, vedere [CREATE TYPE (Transact-SQL)](http://msdn.microsoft.com/en-us/2202236b-e09f-40a1-bbc7-b8cff7488905).  
  
**Genera comandi SET ANSI PADDING**  
Consente di aggiungere l'istruzione SET ANSI_PADDING prima e dopo ogni istruzione CREATE TABLE. Il valore predefinito è True. Per altre informazioni, vedere [SET ANSI_PADDING (Transact-SQL)](http://msdn.microsoft.com/en-us/92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0).  
  
**Includi regole di confronto**  
Consente di includere le regole di confronto nella definizione della colonna. Il valore predefinito è True. Per altre informazioni, vedere [Collation and Unicode Support](http://msdn.microsoft.com/en-us/92d34f48-fa2b-47c5-89d3-a4c39b0f39eb).  
  
**Includi proprietà IDENTITY**  
Consente di includere definizioni per il valore di inizializzazione di IDENTITY e l'incremento di IDENTITY. Il valore predefinito è True. Per altre informazioni, vedere [IDENTITY (Property) (Transact-SQL)](http://msdn.microsoft.com/en-us/8429134f-c821-4033-a07c-f782a48d501c).  
  
**Schema per qualifica dei riferimenti alle chiavi esterne**  
Consente di aggiungere il nome dello schema ai riferimenti alle tabelle per i vincoli FOREIGN KEY. Il valore predefinito è True.  
  
**Script per associazione di valori predefiniti e regole**  
Includere le chiamate alle stored procedure di associazione **sp_bindefault** e **sp_bindrule** . Il valore predefinito è True. Per altre informazioni, vedere [sp_bindefault (Transact-SQL)](http://msdn.microsoft.com/en-us/3da70c10-68d0-4c16-94a5-9e84c4a520f6) e [sp_bindrule (Transact-SQL)](http://msdn.microsoft.com/en-us/2606073e-c52f-498d-a923-5026b9d97e67).  
  
**Script per vincoli CHECK**  
Aggiunge [vincoli CHECK](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e) allo script. Il valore predefinito è True.  
  
**Script per valori predefiniti**  
Consente di includere i valori predefiniti delle colonne nello script. Il valore predefinito è False. Per altre informazioni, vedere [CREATE DEFAULT (Transact-SQL)](http://msdn.microsoft.com/en-us/08475db4-7d90-486a-814c-01a99d783d41).  
  
**Script per filegroup**  
Consente di specificare il filegroup nella clausola ON per le definizioni di tabella. Il valore predefinito è False. Per altre informazioni, vedere [CREATE TABLE (Transact-SQL)](http://msdn.microsoft.com/en-us/1e068443-b9ea-486a-804f-ce7b6e048e8b).  
  
**Script per chiavi esterne**  
Include [vincoli FOREIGN KEY](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd) nello script. Il valore predefinito è False.  
  
**Script per indici full-text**  
Consente di includere indici full-text nello script. Il valore predefinito è False. Per altre informazioni, vedere [CREATE FULLTEXT INDEX (Transact-SQL)](http://msdn.microsoft.com/en-us/8b80390f-5f8b-4e66-9bcc-cabd653c19fd).  
  
**Script per indici**  
Consente di includere indici cluster, non cluster e XML nello script. Il valore predefinito è True. Per altre informazioni, vedere [CREATE INDEX (Transact-SQL)](http://msdn.microsoft.com/en-us/d2297805-412b-47b5-aeeb-53388349a5b9).  
  
**Script per schemi di partizione**  
Consente di includere schemi di partizione di tabelle nello script. Il valore predefinito è False. Per altre informazioni, vedere [CREATE PARTITION SCHEME (Transact-SQL)](http://msdn.microsoft.com/en-us/5b21c53a-b4f4-4988-89a2-801f512126e4).  
  
**Script per chiavi primarie**  
Include [vincoli primari e FOREIGN KEY](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd) nello script. Il valore predefinito è True.  
  
**Script per statistiche**  
Consente di includere statistiche definite dall'utente nello script. Il valore predefinito è False. Per altre informazioni, vedere [CREATE STATISTICS (Transact-SQL)](http://msdn.microsoft.com/en-us/b23e2f6b-076c-4e6d-9281-764bdb616ad2).  
  
**Script per trigger**  
Consente di includere trigger nello script. Il valore predefinito è False. Per altre informazioni, vedere [CREATE TRIGGER (Transact-SQL)](http://msdn.microsoft.com/en-us/edeced03-decd-44c3-8c74-2c02f801d3e7).  
  
**Script per chiavi univoche**  
Include [vincoli UNIQUE e CHECK](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e) nello script. Il valore predefinito è False.  
  
**Script per colonne vista**  
Consente di dichiarare colonne di viste in intestazioni di viste. Il valore predefinito è False. Per altre informazioni, vedere [CREATE VIEW (Transact-SQL)](http://msdn.microsoft.com/en-us/aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9).  
  
**ScriptDriIncludeSystemNames**  
Consente di includere nomi di vincoli generati dal sistema per applicare l'integrità referenziale dichiarativa. Il valore predefinito è False. Per altre informazioni, vedere [REFERENTIAL_CONSTRAINTS (Transact-SQL)](http://msdn.microsoft.com/en-us/5d358f18-0a85-4b55-af4b-98d5f4cd1020).  
  
## <a name="see-also"></a>Vedere anche  
[Generazione di script (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/9711c617-3c68-4e5a-aea3-befc64d51524)  
  

