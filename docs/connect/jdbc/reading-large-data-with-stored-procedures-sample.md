---
title: Lettura di dati di grandi dimensioni con Stored procedure esempio | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
ms.openlocfilehash: 00387faec988fde6bdfa310ed96723f2bc226bfa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>Esempio di lettura di dati di grandi dimensioni con una stored procedure
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] applicazione di esempio viene illustrato come recuperare un parametro OUT grandi dimensioni da una stored procedure.  
  
 Il file di codice per questo esempio è denominato executeStoredProcedure.java ed è disponibile nel seguente percorso:  
  
 \<*directory di installazione*> \sqljdbc_\<*versione*>\\<*language*> \samples\adaptive  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire questa applicazione di esempio, sarà necessario l'accesso per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. nonché impostare il classpath per includere il file sqljdbc.jar o sqljdbc4.jar. Se nel classpath manca una voce per il file sqljdbc.jar o sqljdbc4.jar, nell'applicazione di esempio verrà generata un'eccezione comune di classe non trovata. Per ulteriori informazioni su come impostare il classpath, vedere [utilizza il Driver JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce sqljdbc.jar e sqljdbc4.jar file della libreria di classe da utilizzare a seconda delle impostazioni preferite di Java Runtime Environment (JRE). Per ulteriori informazioni sui file JAR da scegliere, vedere [requisiti di sistema per il Driver JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
 È inoltre necessario creare la stored procedure seguente nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
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
 Nell'esempio seguente, il codice di esempio stabilisce una connessione per il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database. Tramite il codice di esempio vengono quindi creati i dati di esempio e viene aggiornata la tabella Production.Document utilizzando una query con parametri. Quindi, nell'esempio di codice ottiene la modalità di buffer adattivo utilizzando il [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe ed esegue la stored procedure GetLargeDataValue. A partire da Microsoft JDBC Driver versione 2.0, il valore predefinito della proprietà di connessione responseBuffering è "adaptive".  
  
 Infine, il codice di esempio consente di visualizzare i dati restituiti con i parametri OUT e viene inoltre illustrato come utilizzare il `mark` e `reset` metodi sul flusso per rileggere qualsiasi parte dei dati.  
  
 [!code[JDBC#UsingAdaptiveBuffering2](../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di dati di grandi dimensioni](../../connect/jdbc/working-with-large-data.md)  
  
  
