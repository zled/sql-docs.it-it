---
title: Specificare il tipo di archiviazione di file tramite bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 68630ac6e4a2ffad9079ed620e8d7d9660bf6381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064445"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>Specifica del tipo di archiviazione di file tramite bcp (SQL Server)
  Il *tipo di archiviazione di file* indica la modalità con la quale vengono archiviati i dati in un file. I dati possono essere esportati in un file di dati come tipo di tabella di database (formato nativo), nella relativa rappresentazione di caratteri (formato carattere) oppure come qualsiasi tipo di dati in cui la conversione implicita supportata; ad esempio copiare un `smallint` come un `int`. I tipi di dati definiti dall'utente vengono esportati utilizzando il tipo di dati di base corrispondente.  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>Richiesta del tipo di archiviazione di dati con bcp  
 Se un comando interattivo **bcp** include l'opzione **in** o **out** senza l'opzione relativa al file di formato (**-f**) o al formato dei dati (**-n**, **-c**, **-w**o **-N**), viene richiesto il tipo di archiviazione di file di ogni campo di dati, come illustrato di seguito:  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 La risposta dell'utente a questa richiesta dipende dall'operazione eseguita, come illustrato di seguito:  
  
-   Per eseguire l'esportazione bulk dei dati da un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un file di dati nel formato di archiviazione più compatto (formato nativo), accettare i tipi di archiviazione di file predefiniti visualizzati dall'utilità **bcp**. Per un elenco dei tipi di archiviazione di file nativi, vedere "Tipi di archiviazione di file nativi" più avanti in questo argomento.  
  
-   Per l'esportazione bulk dei dati da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un file di dati in formato carattere, specificare `char` come tipo di archiviazione di file per tutte le colonne nella tabella.  
  
-   Per l'importazione bulk dei dati a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un file di dati, specificare il tipo di archiviazione file `char` per i tipi archiviati con il carattere di formato e, per i dati archiviati in formato nativo, specificare uno dei tipi di archiviazione di file, come appropriato:  
  
    |tipo di archiviazione di file|Parametro da specificare nel prompt dei comandi|  
    |-----------------------|-----------------------------|  
    |`char` <sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text` <sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image` <sup>2</sup>|`I`[`mage`]|  
    |`datetime`|**d[ate]**|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|**f[loat]**|  
    |`real`|`r`|  
    |`Int`|**i[nt]**|  
    |`bigint`|`B[igint]`|  
    |`smallint`|**s[mallint]**|  
    |`tinyint`|**t[inyint]**|  
    |`money`|**m[oney]**|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |`UDT` (tipo di dati definito dall'utente)|`U`|  
    |`XML`|`X`|  
  
     <sup>1</sup> l'interazione tra lunghezza del campo, lunghezza del prefisso e i caratteri di terminazione determina la quantità di spazio di archiviazione allocata in un file di dati per i dati non carattere esportati come il `char` tipo di archiviazione di file.  
  
     <sup>2</sup> il `ntext`, `text`, e `image` tipi di dati verranno rimossi in una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di utilizzare questi tipi di dati in nuovi progetti di sviluppo e pianificare la modifica delle applicazioni che ne fanno uso. Uso `nvarchar(max)`, `varchar(max)`, e `varbinary(max)` invece.  
  
## <a name="native-file-storage-types"></a>Tipi di archiviazione di file nativi  
 I tipi di archiviazione di file nativi vengono registrati nel file di formato come tipo di dati del file host corrispondente.  
  
|tipo di archiviazione di file|Tipo di dati del file host|  
|-----------------------|-------------------------|  
|`char` <sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text` <sup>2</sup>|SQLCHAR|  
|`ntext` <sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image` <sup>2</sup>|SQLBINARY|  
|`datetime`|SQLDATETIME|  
|`smalldatetime`|SQLDATETIM4|  
|`decimal`|SQLDECIMAL|  
|`numeric`|SQLNUMERIC|  
|`float`|SQLFLT8|  
|`real`|SQLFLT4|  
|`int`|SQLINT|  
|`bigint`|SQLBIGINT|  
|`smallint`|SQLSMALLINT|  
|`tinyint`|SQLTINYINT|  
|`money`|SQLMONEY|  
|`smallmoney`|SQLMONEY4|  
|`bit`|SQLBIT|  
|`uniqueidentifier`|SQLUNIQUEID|  
|`sql_variant`|SQLVARIANT|  
|`timestamp`|SQLBINARY|  
|UDT (tipo di dati definito dall'utente)|SQLUDT|  
  
 <sup>1</sup> file di dati che vengono archiviati con il carattere di formato `char` come tipo di archiviazione file. Per questi file di dati di tipo carattere SQLCHAR costituisce pertanto l'unico tipo di dati incluso in file di formato.  
  
 <sup>2</sup> non è possibile importazione bulk in `text`, `ntext`, e `image` colonne con valori predefiniti.  
  
## <a name="additional-considerations-for-file-storage-types"></a>Ulteriori considerazioni sui tipi di archiviazione di file  
 Quando si esegue l'esportazione bulk da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un file di dati:  
  
-   È sempre possibile specificare il tipo di archiviazione di file `char`.  
  
-   Se si immette un tipo di archiviazione di file che rappresenta una conversione implicita non valida, **bcp** ha esito negativo; ad esempio, tuttavia è possibile specificare `int` per `smallint` dati, se si specifica `smallint` per `int` dati, risultato di errori di overflow.  
  
-   Se i tipi di dati non carattere, ad esempio `float`, `money`, `datetime`, oppure `int` vengono archiviate come tipi di database, i dati vengono scritti nel file di dati nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] formato nativo.  
  
    > [!NOTE]  
    >  Dopo l'impostazione interattiva di tutti i campi in un comando **bcp**, viene richiesto di salvare le risposte relative a ogni campo in un file di formato non XML. Per altre informazioni sui file di formato non XML, vedere [File in formato non XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità bcp](../../tools/bcp-utility.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Specificare la lunghezza del campo tramite bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Specificare la lunghezza del prefisso nei file di dati con bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
