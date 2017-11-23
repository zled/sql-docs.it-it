---
title: Utilizzo di sequenze di Escape SQL | Documenti Microsoft
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
ms.assetid: 00f9e25a-088e-4ac6-aa75-43eacace8f03
caps.latest.revision: "25"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: df370e44bf2af1a41d926866ea0c2427cccffe59
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="using-sql-escape-sequences"></a>Utilizzo delle sequenze di escape SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'utilizzo di sequenze di escape SQL, come definito dall'API JDBC. Le sequenze di escape vengono utilizzate all'interno di un'istruzione SQL per indicare al driver che la parte della stringa SQL per cui vengono utilizzati caratteri di escape deve essere gestita in modo diverso. Quando la parte della stringa SQL per cui vengono utilizzati caratteri di escape viene elaborata dal driver JDBC, tale parte viene tradotta in codice SQL compreso da SQL Server.  
  
 L'API JDBC richiede cinque tipi di sequenze di escape, tutti supportati dal driver JDBC:  
  
-   Valori letterali dei caratteri jolly LIKE  
  
-   Gestione delle funzioni  
  
-   Valori letterali data e ora  
  
-   Chiamate di stored procedure  
  
-   Outer join  
  
-   Sintassi di escape per Limit  
  
 La sintassi della sequenza di escape utilizzata dal driver JDBC è la seguente:  
  
 `{keyword ...parameters...}`  
  
> [!NOTE]  
>  L'elaborazione delle sequenze di escape SQL è sempre attivata per il driver JDBC.  
  
 Nelle sezioni seguenti vengono descritti i cinque tipi di sequenze di escape e viene illustrato in che modo sono supportati dal driver JDBC:  
  
## <a name="like-wildcard-literals"></a>Valori letterali dei caratteri jolly LIKE  
 Il driver JDBC supporta il `{escape 'escape character'}` sintassi per usare caratteri jolly della clausola LIKE come valori letterali. Il codice seguente restituisce, ad esempio, i valori per col3 se il valore di col2 inizia letteralmente con un carattere di sottolineatura (e non nel caso di utilizzo del carattere jolly).  
  
```  
ResultSet rst = stmt.executeQuery("SELECT col3 FROM test1 WHERE col2   
LIKE '\\_%' {escape '\\'}");  
```  
  
> [!NOTE]  
>  La sequenza di escape deve essere alla fine dell'istruzione SQL. Se vi sono più istruzioni SQL in una stringa di comando, la sequenza di escape deve essere alla fine di ogni istruzione SQL rilevante.  
  
## <a name="function-handling"></a>Gestione delle funzioni  
 Il driver JDBC supporta le sequenze di escape delle funzioni nelle istruzioni SQL con la sintassi seguente:  
  
```  
{fn functionName}  
```  
  
 dove `functionName` è una funzione supportata dal driver JDBC. Esempio:  
  
```  
SELECT {fn UCASE(Name)} FROM Employee  
```  
  
 Nella tabella seguente sono elencate le varie funzioni supportate dal driver JDBC in caso di utilizzo di una sequenza di escape delle funzioni:  
  
|Funzioni per i valori stringa|Funzioni numeriche|Funzioni data/ora|Funzioni di sistema|  
|----------------------|-----------------------|------------------------|----------------------|  
|ASCII<br /><br /> CHAR<br /><br /> CONCATENA<br /><br /> DIFFERENCE<br /><br /> INSERT<br /><br /> LCASE<br /><br /> LEFT<br /><br /> LENGTH<br /><br /> LOCATE<br /><br /> LTRIM<br /><br /> REPEAT<br /><br /> REPLACE<br /><br /> RIGHT<br /><br /> RTRIM<br /><br /> SOUNDEX<br /><br /> SPACE<br /><br /> SUBSTRING<br /><br /> UCASE|ABS<br /><br /> ACOS<br /><br /> ASIN<br /><br /> ATAN<br /><br /> ATAN2<br /><br /> CEILING<br /><br /> COS<br /><br /> COT<br /><br /> DEGREES<br /><br /> EXP<br /><br /> FLOOR<br /><br /> LOG<br /><br /> LOG10<br /><br /> MOD<br /><br /> PI<br /><br /> POWER<br /><br /> RADIANS<br /><br /> RAND<br /><br /> ROUND<br /><br /> SIGN<br /><br /> SIN<br /><br /> SQRT<br /><br /> TAN<br /><br /> TRUNCATE|CURDATE<br /><br /> CURTIME<br /><br /> DAYNAME<br /><br /> DAYOFMONTH<br /><br /> DAYOFWEEK<br /><br /> GIORNOANNO<br /><br /> EXTRACT<br /><br /> HOUR<br /><br /> MINUTE<br /><br /> MONTH<br /><br /> MONTHNAME<br /><br /> NOW<br /><br /> QUARTER<br /><br /> SECOND<br /><br /> TIMESTAMPADD<br /><br /> TIMESTAMPDIFF<br /><br /> WEEK<br /><br /> YEAR|DATABASE<br /><br /> IFNULL<br /><br /> Utente|  
  
> [!NOTE]  
>  Se si tenta di utilizzare una funzione non supportata dal database, si verifica un errore.  
  
## <a name="date-and-time-literals"></a>Valori letterali data e ora  
 La sintassi di escape per i valori letterali data, ora e timestamp è la seguente:  
  
```  
{literal-type 'value'}  
```  
  
 dove `literal-type` è uno dei seguenti:  
  
|Tipo di valore letterale|Description|Formato del valore|  
|------------------|-----------------|------------------|  
|d|Data|aaaa-mm-gg|  
|t|Time|hh:mm:ss [1]|  
|ts|TimeStamp|aaaa-mm-gg hh:mm:ss[.f...]|  
  
 Esempio:  
  
```  
UPDATE Orders SET OpenDate={d '2005-01-31'}   
WHERE OrderID=1025  
```  
  
## <a name="stored-procedure-calls"></a>Chiamate di stored procedure  
 Il driver JDBC supporta la `{? = call proc_name(?,...)}` e `{call proc_name(?,...)}` sintassi per le chiamate di stored procedure, a seconda se è necessario elaborare un parametro restituito di escape.  
  
 Una stored procedure è un oggetto eseguibile archiviato nel database. In genere, si tratta di una o più istruzioni SQL precompilate. La sintassi della sequenza di escape per la chiamata di un stored procedure è la seguente:  
  
```  
{[?=]call procedure-name[([parameter][,[parameter]]...)]}  
```  
  
 dove `procedure-name` specifica il nome di una stored procedure e `parameter` specifica un parametro della stored procedure.  
  
 Per ulteriori informazioni sull'utilizzo di `call` sequenza con le stored procedure di escape, vedere [istruzioni Using con Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
## <a name="outer-joins"></a>Outer join  
 Il driver JDBC supporta la sintassi left, right e full outer join SQL92. La sequenza di escape per gli outer join è la seguente:  
  
```  
{oj outer-join}  
```  
  
 dove outer-join è:  
  
```  
table-reference {LEFT | RIGHT | FULL} OUTER JOIN    
{table-reference | outer-join} ON search-condition  
```  
  
 dove `table-reference` è un nome di tabella e `search-condition` è la condizione di join che si desidera utilizzare per le tabelle.  
  
 Esempio:  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status   
   FROM {oj Customers LEFT OUTER JOIN   
      Orders ON Customers.CustID=Orders.CustID}   
   WHERE Orders.Status='OPEN'  
```  
  
 Le sequenze di escape dell'outer join seguenti sono supportate dal driver JDBC:  
  
-   Left outer join  
  
-   Right outer join  
  
-   Full outer join  
  
-   Outer join nidificati  
  
## <a name="limit-escape-syntax"></a>Sintassi di escape per Limit  
  
> [!NOTE]  
>  La sintassi di escape limite supportata solo da Microsoft JDBC Driver 4.2 (o versione successiva) per SQL Server quando si utilizza JDBC 4.1 o versione successiva.  
  
 La sintassi di escape per LIMIT è la seguente:  
  
```  
LIMIT <rows> [OFFSET <row offset>]  
```  
  
 La sintassi di escape è costituito da due parti: \< *righe*> è obbligatorio e specifica il numero di righe da restituire. OFFSET e \< *offset di riga*> sono facoltativi e specificare il numero di righe da ignorare prima di iniziare a restituire le righe. Il driver JDBC supporta solo la parte obbligatoria trasformando la query per l'utilizzo di TOP invece di LIMIT. SQL Server non supporta la clausola LIMIT. **Il driver JDBC non supporta l'opzione facoltativa \<offset di riga > e il driver genererà un'eccezione se viene utilizzato**.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
