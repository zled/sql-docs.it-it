---
title: Usare il formato nativo Unicode per importare o esportare dati (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d05e69dd4a094e3f361098583adf3aed7899a018
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137961"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a>Utilizzare il formato Unicode nativo per importare o esportare dati (SQL Server)
  Il formato Unicode nativo risulta particolarmente utile quando è necessario copiare informazioni da un'installazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un'altra. L'utilizzo del formato nativo per i dati non carattere consente di risparmiare tempo evitando di dover eseguire la conversione dei tipi di dati in formato carattere e viceversa. L'utilizzo del formato carattere Unicode per tutti i dati di tipo carattere consente di evitare la perdita dei caratteri estesi durante il trasferimento bulk dei dati tra server che utilizzano tabelle codici diverse. Un file di dati in formato nativo Unicode è leggibile con qualsiasi metodo di importazione bulk.  
  
 Il formato nativo Unicode è consigliato per i trasferimenti bulk di dati tra più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando un file di dati che include caratteri estesi o DBCS. Per i dati non carattere, il formato nativo Unicode utilizza i tipi di dati (database) nativi. Per dati di tipo carattere, ad esempio `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)`, e `ntext`, il formato nativo Unicode utilizza il formato di dati carattere Unicode.  
  
 I dati `sql_variant` memorizzati come SQLVARIANT in un file di dati in formato nativo Unicode vengono gestiti in modo analogo a quanto avviene per un file di dati in formato nativo, fatta eccezione per il fatto che i valori `char` e `varchar` sono convertiti in `nchar` e `nvarchar`, raddoppiando lo spazio necessario per le colonne interessate. I metadati originali vengono mantenuti e i valori vengono convertiti originale `char` e `varchar` del tipo di dati durante l'importazione bulk in una colonna di tabella.  
  
## <a name="command-options-for-unicode-native-format"></a>Opzioni di comando per il formato nativo Unicode  
 È possibile importare dati in formato nativo Unicode in una tabella usando **bcp**, BULK INSERT o INSERT... SELECT \* FROM OPENROWSET(BULK...). Per un comando **bcp** o un'istruzione BULK INSERT, è possibile specificare il formato dati nella riga di comando. Per un'istruzione INSERT ... SELECT * FROM OPENROWSET(BULK...) è necessario specificare il formato dei dati in un file di formato.  
  
 Il formato nativo Unicode è supportato dalle seguenti opzioni:  
  
|Comando|Opzione|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Fa sì che il **bcp** i tipi di utilità per utilizzare il formato nativo Unicode, che usa dati (database) nativi per tutti i dati non carattere e il formato carattere Unicode per tutti i caratteri (`char`, `nchar`, `varchar`, `nvarchar`, `text`, e `ntext`) dei dati.|  
|BULK INSERT|DATAFILETYPE **='** widenative **'**|Utilizzare il formato Unicode nativo per l'importazione bulk dei dati.|  
  
 Per altre informazioni, vedere [Utilità bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) o [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  In alternativa, è possibile definire la formattazione di ogni singolo campo in un file di formato. Per altre informazioni, vedere [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti mostrano come eseguire l'esportazione in blocco di dati nativi usando **bcp** e l'importazione in blocco degli stessi dati usando BULK INSERT.  
  
### <a name="sample-table"></a>Tabella di esempio  
 Gli esempi richiedono la creazione di una tabella denominata **myTestUniNativeData** nel database di esempio **AdventureWorks** all'interno dello schema **dbo**. Prima di eseguire le procedure illustrate negli esempi, è necessario creare la tabella. Nell'editor di query di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] eseguire:  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Per popolare la tabella e visualizzare il contenuto risultante, eseguire le istruzioni seguenti:  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Utilizzo del comando bcp per l'esportazione bulk di dati nativi  
 Per esportare i dati dalla tabella al file di dati, usare **bcp** con l'opzione **out** e i qualificatori seguenti:  
  
|Qualificatori|Description|  
|----------------|-----------------|  
|**-N**|Specifica i tipi di dati nativi.|  
|**-T**|Specifica che l'utilità **bcp** si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con una connessione trusted che usa la sicurezza integrata. Se non si specifica **-T** , è necessario specificare **-U** e **-P** per eseguire correttamente l'accesso.|  
  
 Nel seguente esempio viene eseguita l'esportazione bulk dei dati in formato nativo dalla tabella `myTestUniNativeData` in un nuovo file di dati denominato `myTestUniNativeData-N.Dat`. Al prompt dei comandi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows digitare:  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Utilizzo dell'istruzione BULK INSERT per l'importazione bulk di dati nativi  
 Nell'esempio seguente si utilizza BULK INSERT per importare i dati dal file di dati `myTestUniNativeData-N.Dat` nella tabella `myTestUniNativeData`. Nell'editor di query di [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] eseguire:  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per utilizzare formati di dati per l'importazione o l'esportazione bulk**  
  
-   [Importare dati in formato nativo e carattere da versioni precedenti di SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Usare il formato carattere per importare o esportare dati &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo del formato nativo per importare o esportare dati &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato carattere Unicode per importare o esportare dati &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
