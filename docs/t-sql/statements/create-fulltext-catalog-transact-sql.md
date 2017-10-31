---
title: CREARE il catalogo full-text (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CATALOG_TSQL
- CREATE_FULLTEXT_TSQL
- FULLTEXT_TSQL
- FULLTEXT CATALOG
- CREATE FULLTEXT CATALOG
- CREATE_FULLTEXT_CATALOG_TSQL
- CATALOG
- FULLTEXT_CATALOG_TSQL
- CREATE FULLTEXT
- FULLTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- CREATE FULLTEXT CATALOG statement
ms.assetid: d7a8bd93-e2d7-4a40-82ef-39069e65523b
caps.latest.revision: 60
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: f08bdaeaacb970c839ea1d7bb31c44f454daadf8
ms.contentlocale: it-it
ms.lasthandoff: 09/13/2017

---
# <a name="create-fulltext-catalog-transact-sql"></a>CREATE FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un catalogo full-text per un database. Un unico catalogo full-text può contenere numerosi indici full-text, ma un indice full-text può essere incluso in un solo catalogo full-text. Ogni database può contenere zero o più cataloghi full-text.  
  
 Non è possibile creare i cataloghi full-text di **master**, **modello**, o **tempdb** database.  
  
> [!IMPORTANT]  
>  A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] un catalogo full-text è un oggetto virtuale che non appartiene ad alcun filegroup. Un catalogo full-text è un concetto logico che fa riferimento a un gruppo di indici full-text.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE FULLTEXT CATALOG catalog_name  
     [ON FILEGROUP filegroup ]  
     [IN PATH 'rootpath']  
     [WITH <catalog_option>]  
     [AS DEFAULT]  
     [AUTHORIZATION owner_name ]  
  
<catalog_option>::=  
     ACCENT_SENSITIVITY = {ON|OFF}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *catalog_name*  
 Nome del nuovo catalogo. Il nome del catalogo deve essere univoco nel database corrente, ovvero diverso da tutti i nomi di catalogo già esistenti. Anche il nome del file corrispondente al catalogo full-text (vedere ON FILEGROUP) deve essere univoco rispetto a tutti i file nel database. Se il nome specificato per il catalogo è già utilizzato per un altro catalogo nel database, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà restituito un errore.  
  
 La lunghezza del nome del catalogo non deve superare i 120 caratteri.  
  
 ON FILEGROUP *filegroup*  
 A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], questa clausola non ha alcun effetto.  
  
 NEL percorso **'***rootpath***'**  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], questa clausola non ha alcun effetto.  
  
 ACCENT_SENSITIVITY = {ON|OFF}  
 Specifica se per il catalogo viene applicata la distinzione tra caratteri accentati e non accentati per l'indicizzazione full-text. Se si modifica questa proprietà, l'indice deve essere ricompilato. Per impostazione predefinita, viene utilizzata l'impostazione per la distinzione tra caratteri accentati e non accentati specificata nelle regole di confronto del database. Per visualizzare le regole di confronto del database, utilizzare il **Sys. Databases** vista del catalogo.  
  
 Per determinare l'impostazione della proprietà di lettura e non accentati di un catalogo full-text, utilizzare la funzione FULLTEXTCATALOGPROPERTY con il **accentsensitivity** valore di proprietà e *catalog_name*. Se il valore restituito è '1', il catalogo full-text supporta la distinzione tra caratteri accentati e non accentati. Se il valore è '0', per il catalogo non è attiva tale distinzione.  
  
 AS DEFAULT  
 Specifica che il catalogo è il catalogo predefinito. Quando si creano indici full-text senza specificare un catalogo full-text in modo esplicito, viene utilizzato il catalogo predefinito. Se un catalogo full-text esistente è già contrassegnato AS DEFAULT, l'impostazione di AS DEFAULT per il nuovo catalogo renderà quest'ultimo il catalogo full-text predefinito.  
  
 AUTORIZZAZIONE *owner_name*  
 Imposta il proprietario del catalogo full-text sul nome di un utente o ruolo di database. Se *owner_name* è un ruolo, il ruolo deve essere il nome di un ruolo che l'utente corrente è un membro di o l'utente che esegue l'istruzione deve essere il proprietario del database o l'amministratore di sistema.  
  
 Se *owner_name* è un nome utente, il nome utente deve essere uno dei seguenti:  
  
-   Nome dell'utente che esegue l'istruzione.  
  
-   Nome di un utente per il quale l'utente che esegue il comando dispone delle autorizzazioni di rappresentazione.  
  
-   Oppure, l'utente che esegue il comando deve essere il proprietario del database o un amministratore di sistema.  
  
 *owner_name* deve inoltre disporre dell'autorizzazione TAKE OWNERSHIP nel catalogo full-text specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Gli ID dei cataloghi full-text iniziano da 00005 e vengono incrementati di un'unità per ogni catalogo creato.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve disporre dell'autorizzazione CREATE FULLTEXT CATALOG sul database oppure essere un membro del **db_owner**, o **db_ddladmin** ruoli predefiniti del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono creati un catalogo full-text e un indice full-text.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FULLTEXT CATALOG ftCatalog AS DEFAULT;  
GO  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume) KEY INDEX PK_JobCandidate_JobCandidateID;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. fulltext_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [ELIMINARE il catalogo full-text &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)   
 
  
  

