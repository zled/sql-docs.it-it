---
title: Esempio di lettura di dati di grandi dimensioni con una stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69c9989cf9edd1714a70d5b7e0f7745988dcb59d
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279029"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Esempio di lettura di dati di grandi dimensioni con una stored procedure
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questa applicazione di esempio di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] illustra come recuperare un parametro OUT di grandi dimensioni da una stored procedure.  
  
 Il file di codice per questo esempio è denominato ExecuteStoredProcedure.java ed è disponibile nel percorso seguente:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*linguaggio*> \samples\adaptive  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, è necessario accedere al database di esempio di [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. È anche necessario impostare classpath per includere il file con estensione jar mssql-jdbc. Per altre informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Con [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono inclusi file di libreria di classi mssql-jdbc da usare a seconda delle impostazioni Java Runtime Environment (JRE) preferite. Per altre informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
 Creare la stored procedure seguente nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:  
  
```sql
CREATE PROCEDURE GetLargeDataValue   
  (@Document_ID int,   
   @Document_ID_out int OUTPUT,   
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  
  
AS   
BEGIN    
   SELECT @Document_ID_out = DocumentID,   
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary   
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il codice esegue una connessione al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Tramite il codice di esempio vengono quindi creati i dati di esempio e viene aggiornata la tabella Production.Document utilizzando una query con parametri. Viene quindi ottenuta la modalità di buffer adattivo usando il metodo [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) della classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) e viene eseguita la stored procedure GetLargeDataValue. A partire da Microsoft JDBC Driver versione 2.0, il valore predefinito della proprietà di connessione responseBuffering è "adaptive".  
  
 Infine, tramite il codice di esempio vengono visualizzati i dati restituiti con i parametri OUT e viene illustrato come usare i metodi `mark` e `reset` sul flusso per rileggere qualsiasi parte dei dati.  
  
 [!code[JDBC#UsingAdaptiveBuffering2](../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di dati di grandi dimensioni](../../connect/jdbc/working-with-large-data.md)  
  
  
