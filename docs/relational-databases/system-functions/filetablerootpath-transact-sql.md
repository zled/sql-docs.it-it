---
title: FileTableRootPath (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FileTableRootPath_TSQL
- FileTableRootPath
dev_langs:
- TSQL
helpviewer_keywords:
- FileTableRootPath function
ms.assetid: 0cba908a-c85c-4b09-b16a-df1cb333c629
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1c877d75e08662b95f9d22ca55b378ff03aafcec
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="filetablerootpath-transact-sql"></a>FileTableRootPath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il percorso UNC di livello radice per una tabella FileTable specifica o per il database corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FileTableRootPath ( [ ‘[schema_name.]FileTable_name’ ], @option )  
```  
  
## <a name="arguments"></a>Argomenti  
 *FileTable_name*  
 Nome dell'oggetto FileTable. *FileTable_name* è di tipo **nvarchar**. Questo parametro è facoltativo. Il valore predefinito corrisponde al database corrente. Specifica di *schema_name* anche è facoltativa. È possibile passare NULL *FileTable_name* per utilizzare il valore di parametro predefinito  
  
 *@option*  
 Espressione Integer che definisce la formattazione del componente server del percorso. *@option* Può avere uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Restituisce il nome del server convertito in formato NetBIOS, ad esempio:<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> Si tratta del valore predefinito.|  
|**1**|Restituisce il nome del server senza conversione, ad esempio:<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|Restituisce il percorso completo del server, ad esempio:<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>Tipo restituito  
 **nvarchar(4000)**  
  
 Quando il database appartiene a un gruppo di disponibilità Always On, il **FileTableRootPath** funzione restituisce il nome di rete virtuale (VNN) invece del nome computer.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Il **FileTableRootPath** funzione restituisce NULL quando viene soddisfatta una delle condizioni seguenti:  
  
-   Il valore di *FileTable_name* non è valido.  
  
-   Il chiamante non dispone delle autorizzazioni sufficienti per fare riferimento alla tabella specificata o al database corrente.  
  
-   L'opzione FILESTREAM di *database_directory* non è impostata per il database corrente.  
  
 Per altre informazioni, vedere [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="best-practices"></a>Procedure consigliate  
 Per mantenere il codice e le applicazioni indipendenti dal database e dal computer correnti, evitare di scrivere codice basato su percorsi di file assoluti. Ottenere invece il percorso completo di un file in fase di esecuzione utilizzando il **FileTableRootPath** e **GetFileNamespacePath** funzioni insieme, come illustrato nell'esempio seguente. Per impostazione predefinita, la funzione **GetFileNamespacePath** restituisce il percorso relativo del file all'interno del percorso radice per il database.  
  
```sql  
USE MyDocumentDatabase;  
  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
@fullPath = varchar(1000);  
  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath()  
FROM DocumentStore  
WHERE Name = N’document.docx’;  
```  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 Il **FileTableRootPath** funzione richiede:  
  
-   Autorizzazione SELECT per la tabella FileTable per ottenere il percorso radice di una tabella FileTable specifica.  
  
-   **db_datareader** o autorizzazione superiore per ottenere il percorso radice per il database corrente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come chiamare il **FileTableRootPath** (funzione).  
  
```  
USE MyDocumentDatabase;  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDatabase”  
SELECT FileTableRootPath();  
  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable”  
SELECT FileTableRootPath(N'dbo.MyFileTable');  
  
-- returns “\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable”  
SELECT FileTableRootPath(N'MyFileTable');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
