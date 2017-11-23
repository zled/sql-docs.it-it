---
title: Conversioni di tipi di informazioni sui dati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
caps.latest.revision: "34"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ba1a10fc33dc5e80fb300eaa31e849692c55041
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="understanding-data-type-conversions"></a>Informazioni sulle conversioni dei tipi di dati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per semplificare la conversione dei tipi di dati del linguaggio di programmazione Java [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce conversioni del tipo di dati come richiesto dalla specifica JDBC. Per offrire maggiore flessibilità, tutti i tipi sono convertibili da e verso **oggetto**, **stringa**, e **byte []** tipi di dati.  
  
## <a name="getter-method-conversions"></a>Conversioni dei metodi di richiamo  
 In base il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati, il grafico seguente contiene la mappa di conversione del driver JDBC per get\<tipo > metodi () il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe e le conversioni supportate per get\< Tipo > metodi di [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe.  
  
 ![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")  
  
 Sono disponibili tre categorie di conversione supportate dai metodi di richiamo del driver JDBC:  
  
-   **Senza perdita di dati (x)**: conversioni nei casi in cui il tipo di richiamo è uguale o inferiore rispetto al tipo di server sottostante. Ad esempio, quando si chiama getBigDecimal in una colonna decimale del server sottostante, non è necessaria alcuna conversione.  
  
-   **Convertito (y)**: le conversioni da tipi di server numerici nei tipi di linguaggio Java in cui la conversione è regolare e segue le regole di conversione del linguaggio Java. In tali conversioni, la precisione viene sempre troncata, mai arrotondata, e l'overflow viene gestito come modulo del tipo di destinazione inferiore. Ad esempio, la chiamata getInt su un oggetto sottostante **decimale** colonna che contiene "1,9999 il valore" restituito sarà "1", o se sottostante **decimale** valore è "3000000000", quindi il **int** valore causa un overflow in "-1294967296".  
  
-   **Dipendente dai dati (z)**: le conversioni da tipi di caratteri sottostanti in tipi numerici richiedono che i tipi di caratteri contengano valori che possono essere convertiti in tale tipo. Non vengono eseguite altre conversioni. Se è troppo grande per il tipo di richiamo, il valore non sarà valido. Ad esempio, se getInt viene chiamato su una colonna varchar (50) che contiene "53", il valore viene restituito come un **int**; ma se il valore sottostante è "xyz" o "3000000000", viene generato un errore.  
  
 Se getString viene chiamato su un **binario**, **varbinary**, **varbinary (max)**, o **immagine** del tipo di dati di colonna, il valore viene restituito come un valore di stringa esadecimale.  
  
## <a name="updater-method-conversions"></a>Conversioni dei metodi di aggiornamento  
 Per i dati passati all'aggiornamento di Java tipizzati\<tipo > metodi () il [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe, applicano le seguenti conversioni.  
  
 ![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")  
  
 Sono disponibili tre categorie di conversione supportate dai metodi di aggiornamento del driver JDBC:  
  
-   **Senza perdita di dati (x)**: conversioni nei casi in cui il tipo di aggiornamento è uguale o inferiore rispetto al tipo di server sottostante. Ad esempio, quando si esegue la chiamata a updateBigDecimal in una colonna decimale del server sottostante, la conversione non è necessaria.  
  
-   **Convertito (y)**: le conversioni da tipi di server numerici nei tipi di linguaggio Java in cui la conversione è regolare e segue le regole di conversione del linguaggio Java. In tali conversioni, la precisione viene sempre troncata, mai arrotondata, e l'overflow viene gestito come modulo del tipo di destinazione, ovvero quello inferiore. Ad esempio, la chiamata updateDecimal su un oggetto sottostante **int** colonna che contiene "1,9999 il valore" restituito sarà "1", o se sottostante **decimale** valore è "3000000000", quindi il **int**valore causa un overflow in "-1294967296".  
  
-   **Dipendente dai dati (z)**: le conversioni dai tipi di dati di origine sottostanti in tipi di dati di destinazione richiedono che è possono convertire i valori contenuti nei tipi di destinazione. Non vengono eseguite altre conversioni. Se è troppo grande per il tipo di richiamo, il valore non sarà valido. Se, ad esempio, updateString viene chiamato su una colonna int che contiene "53", l'aggiornamento verrà eseguito. Se invece il valore String sottostante è "foo" o "3000000000", verrà generato un errore.  
  
 Quando updateString viene chiamato su un **binario**, **varbinary**, **varbinary (max)**, o **immagine** del tipo di dati di colonna, il valore String verrà gestito come valore di stringa esadecimale.  
  
 Quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati colonna **XML**, il valore di dati deve essere valido **XML**. Quando si chiama updateBytes o updateBinaryStream, updateBlob metodi, il valore di dati deve essere la rappresentazione di stringa esadecimale dei caratteri XML. Esempio:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 Si noti che se i caratteri XML sono espressi in codifiche di caratteri specifiche, è necessario un indicatore dell'ordine dei byte (BOM, Byte-Order Mark).  
  
## <a name="setter-method-conversions"></a>Conversioni dei metodi di impostazione  
 Per i dati passati al set di Java tipizzati\<tipo > metodi () del [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe e il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe, applicano le seguenti conversioni.  
  
 ![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")  
  
 Il server cercherà di eseguire la conversione e restituirà degli errori in caso di esito negativo.  
  
 In caso del **stringa** il tipo di dati, se il valore supera la lunghezza di **VARCHAR**, viene eseguito il mapping **LONGVARCHAR**. Analogamente, **NVARCHAR** esegue il mapping a **LONGNVARCHAR** se il valore supera la lunghezza di **NVARCHAR**. Lo stesso vale per **byte []**. Valori più lunghi di **VARBINARY** diventano **LONGVARBINARY**.  
  
 Sono disponibili due categorie di conversione supportate dai metodi di impostazione del driver JDBC:  
  
-   **Senza perdita di dati (x)**: conversioni nei casi numerici in cui il tipo di impostazione è uguale o inferiore rispetto al tipo di server sottostante. Ad esempio, quando si chiama setBigDecimal su un server sottostante **decimale** colonna, è necessaria alcuna conversione. Per valori numerici per casi di carattere, il linguaggio **numerico** tipo di dati viene convertito in un **stringa**. Ad esempio, la chiamata setDouble con un valore di "53" in una colonna varchar (50) produce un valore character "53" nella colonna di destinazione.  
  
-   **Convertito (y)**: le conversioni da un linguaggio **numerico** tipo a un server sottostante **numerico** tipo inferiore. Questa conversione è regolare e segue [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] le convenzioni di conversione. La precisione è sempre troncata, mai arrotondata, e l'overflow genera un errore di conversione non supportata. Ad esempio, usando updateDecimal con un valore pari a "1,9999"il valore su un risultati di colonna integer sottostante "1" nella colonna di destinazione. Tuttavia, se viene passato "3000000000", il driver genera un errore.  
  
-   **Dipendente dai dati (z)**: le conversioni da un linguaggio **stringa** tipo sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati dipende dalle condizioni seguenti: il driver invia il **stringa** valore [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] esegue conversioni, se necessario. Se la proprietà sendStringParametersAsUnicode è impostata su true e sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati **immagine**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è consentita la conversione **nvarchar** a **immagine** e genera un SQLServerException. Se la proprietà sendStringParametersAsUnicode è impostata su false e sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati **immagine**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] consente la conversione **varchar** a **immagine**e non viene generata un'eccezione.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]esegue le conversioni e restituisce gli errori al driver JDBC quando si verificano problemi.  
  
 Quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati colonna **XML**, il valore di dati deve essere valido **XML**. Quando si chiama updateBytes o updateBinaryStream, updateBlob metodi, il valore di dati deve essere la rappresentazione di stringa esadecimale dei caratteri XML. Esempio:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 Si noti che se i caratteri XML sono espressi in codifiche di caratteri specifiche, è necessario un indicatore dell'ordine dei byte (BOM, Byte-Order Mark).  
  
## <a name="conversions-on-setobject"></a>Conversioni in setObject  
  
> [!NOTE]  
>  Microsoft JDBC driver 4.2 (e versioni successive) per SQL Server supporta JDBC 4.1 e 4.2. Per ulteriori informazioni sulle versioni 4.1 e 4.2: mapping e le conversioni vedere [conformità a JDBC 4.1 per il Driver JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) e [JDBC 4.2 conformità per il Driver JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md), oltre alle informazioni seguenti.  
  
 Per il linguaggio dati tipizzati passati al setObject (\<tipo >) metodi del [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe, applicano le seguenti conversioni.  
  
 ![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")  
  
 Il metodo setObject con alcun tipo di destinazione specificato utilizzerà il mapping predefinito. In caso del **stringa** il tipo di dati, se il valore supera la lunghezza di **VARCHAR**, viene eseguito il mapping **LONGVARCHAR**. Analogamente, **NVARCHAR** esegue il mapping a **LONGNVARCHAR** se il valore supera la lunghezza di **NVARCHAR**. Lo stesso vale per **byte []**. Valori più lunghi di **VARBINARY** diventano **LONGVARBINARY**.  
  
 Sono disponibili tre categorie di conversione supportate dai metodi setObject del driver JDBC:  
  
-   **Senza perdita di dati (x)**: conversioni nei casi numerici in cui il tipo di impostazione è uguale o inferiore rispetto al tipo di server sottostante. Ad esempio, quando si chiama setBigDecimal su un server sottostante **decimale** colonna, è necessaria alcuna conversione. Per valori numerici per casi di carattere, il linguaggio **numerico** tipo di dati viene convertito in un **stringa**. Ad esempio, la chiamata setDouble con un valore di "53" in una colonna varchar (50) produrrà un valore character "53" nella colonna di destinazione.  
  
-   **Convertito (y)**: le conversioni da un linguaggio **numerico** tipo a un server sottostante **numerico** tipo inferiore. Questa conversione è regolare e segue [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] le convenzioni di conversione. La precisione è sempre troncata, mai arrotondata, e l'overflow genera un errore di conversione non supportata. Ad esempio, usando updateDecimal con un valore pari a "1,9999"il valore su un risultati di colonna integer sottostante "1" nella colonna di destinazione. Tuttavia, se viene passato "3000000000", il driver genera un errore.  
  
-   **Dipendente dai dati (z)**: le conversioni da un linguaggio **stringa** tipo sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati dipende dalle condizioni seguenti: il driver invia il **stringa** valore [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] esegue conversioni, se necessario. Se la proprietà di connessione sendStringParametersAsUnicode è impostata su true e sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati **immagine**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è consentita la conversione **nvarchar** a **immagine** e genera un SQLServerException. Se la proprietà sendStringParametersAsUnicode è impostata su false e sottostante [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati **immagine**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] consente la conversione **varchar** a **immagine**e non viene generata un'eccezione.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]esegue la maggior parte delle conversioni set e restituisce gli errori al driver JDBC quando si verificano problemi. Le conversioni sul lato client costituiscono un'eccezione e vengono eseguite solo in caso di **data**, **ora**, **timestamp**, **booleano**e  **Stringa** valori.  
  
 Quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è di tipo di dati colonna **XML**, il valore di dati deve essere valido **XML**. Quando si chiama il metodo setObject(byte[], SQLXML), setObject(inputStream, SQLXML) o setObject(Blob, SQLXML), il valore dei dati deve essere la rappresentazione di stringa esadecimale dei caratteri XML. Esempio:  
  
```  
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E   
```  
  
 Si noti che se i caratteri XML sono espressi in codifiche di caratteri specifiche, è necessario un indicatore dell'ordine dei byte (BOM, Byte-Order Mark).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sui tipi di dati del driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
