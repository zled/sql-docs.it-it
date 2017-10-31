---
title: FORMATO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMAT_TSQL
- FORMAT
dev_langs:
- TSQL
helpviewer_keywords:
- FORMAT function
ms.assetid: dad6f24c-b8d9-4dbe-a561-9b167b8f20c8
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 75f944ad28bc56300db7ca9dd7220036faaea711
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="format-transact-sql"></a>FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce un valore formattato con il formato specificato e impostazioni cultura facoltative in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Utilizzare la funzione FORMAT per formattare in base alle impostazioni locali i valori numerici e di data/ora come stringhe. Per le conversioni di tipi di dati generali, utilizzare CAST o CONVERT.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
FORMAT ( value, format [, culture ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Valore*  
 Espressione di un tipo di dati supportato da formattare. Per un elenco di tipi validi, vedere la tabella nella sezione Osservazioni indicata di seguito.  
  
 *formato*  
 **nvarchar** modello di formato.  
  
 Il *formato* argomento deve contenere una stringa di formato .NET Framework valida, come una stringa di formato standard (ad esempio, "C" o "D"), o come una serie di caratteri personalizzati per date e valori numerici (ad esempio "MMMM gg, aaaa (gggg)") . La formattazione composta non è supportata. Per una spiegazione completa di questi schemi di formattazione, consultare la documentazione di .NET Framework nella stringa di formattazione in generale, data personalizzato e formati di ora e formati di numero personalizzati. Un buon punto di partenza è l'argomento "[formattazione dei tipi di](http://go.microsoft.com/fwlink/?LinkId=211776)."  
  
 *impostazioni cultura*  
 Parametro facoltativo **nvarchar** argomento che specifica le impostazioni cultura.  
  
 Se il *delle impostazioni cultura* argomento non viene specificato, viene utilizzata la lingua della sessione corrente. Tale lingua viene impostata in modo implicito o in modo esplicito tramite l'istruzione SET LANGUAGE. *impostazioni cultura* accetta qualsiasi impostazione cultura supportata da .NET Framework come argomento; non è limitato alle lingue supportate in modo esplicito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se il *delle impostazioni cultura* argomento non è valido, FORMAT genera un errore.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar** o null  
  
 La lunghezza del valore restituito è determinata dal *formato*.  
  
## <a name="remarks"></a>Osservazioni  
 FORMAT restituisce NULL per errori diversi da un *delle impostazioni cultura* non *valido*. Ad esempio, viene restituito NULL se il valore specificato *formato* non è valido.  
 
 La funzione FORMAT è non deterministica.   
  
 FORMATO basato sulla presenza di .NET Framework Common Language Runtime (CLR).  
  
 Questa funzione non può essere eseguita in modalità remota poiché dipende la presenza di CLR. Comunicazione remota di una funzione che richiede CLR, potrebbe causare un errore nel server remoto.  
  
 FORMATO si basa su CLR, regole, che indica che deve essere evitato:) e il punto di formattazione. Pertanto, quando lo stringa di formato (secondo parametro) contiene un carattere due punti o periodo, i due punti o periodo devono essere precedute dal carattere barra rovesciata quando un valore di input (il primo parametro) è del **ora** tipo di dati. Vedere [formatoD.con tipi di dati ora](#ExampleD).  
  
 Nella tabella seguente sono elencati i tipi di dati accettabili per la *valore* argomento insieme ai rispettivi tipi equivalenti mapping di .NET Framework.  
  
|Category|Tipo|Tipo .NET|  
|--------------|----------|---------------|  
|Numeric|bigint|Int64|  
|Numeric|int|Int32|  
|Numeric|smallint|Int16|  
|Numeric|tinyint|Byte|  
|Numeric|decimal|SqlDecimal|  
|Numeric|numeric|SqlDecimal|  
|Numeric|float|Double|  
|Numeric|real|Single|  
|Numeric|smallmoney|Decimal|  
|Numeric|money|Decimal|  
|Data e ora|data|DateTime|  
|Data e ora|time|TimeSpan|  
|Data e ora|datetime|DateTime|  
|Data e ora|smalldatetime|DateTime|  
|Data e ora|datetime2|DateTime|  
|Data e ora|datetimeoffset|DateTimeOffset|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-simple-format-example"></a>A. Esempio semplice di FORMAT  
 Nell'esempio seguente viene restituita una data semplice nel formato per impostazioni cultura diverse.  
  
```sql  
DECLARE @d DATETIME = '10/01/2011';  
SELECT FORMAT ( @d, 'd', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'd', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'd', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'd', 'zh-cn' ) AS 'Simplified Chinese (PRC) Result';   
  
SELECT FORMAT ( @d, 'D', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'D', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'D', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'D', 'zh-cn' ) AS 'Chinese (Simplified PRC) Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
US English Result Great Britain English Result  German Result Simplified Chinese (PRC) Result  
----------------  ----------------------------- ------------- -------------------------------------  
10/1/2011         01/10/2011                    01.10.2011    2011/10/1  
  
(1 row(s) affected)  
  
US English Result            Great Britain English Result  German Result                    Chinese (Simplified PRC) Result  
---------------------------- ----------------------------- -----------------------------  ---------------------------------------  
Saturday, October 01, 2011   01 October 2011               Samstag, 1. Oktober 2011        2011年10月1日  
  
(1 row(s) affected)  
```  
  
### <a name="b-format-with-custom-formatting-strings"></a>B. FORMAT con stringhe di formattazione personalizzate  
 Nell'esempio seguente vengono illustrati i valori numerici di formattazione specificando un formato personalizzato. Nell'esempio si presuppone che la data corrente è 27 settembre 2012. Per ulteriori informazioni su questi e altri formati personalizzati, vedere [stringhe di formato numerico personalizzate](http://msdn.microsoft.com/library/0c899ak8.aspx).  
  
```sql  
DECLARE @d DATETIME = GETDATE();  
SELECT FORMAT( @d, 'dd/MM/yyyy', 'en-US' ) AS 'DateTime Result'  
       ,FORMAT(123456789,'###-##-####') AS 'Custom Number Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DateTime Result  Custom Number Result  
--------------   --------------------  
27/09/2012       123-45-6789  
  
(1 row(s) affected)  
```  
  
### <a name="c-format-with-numeric-types"></a>C. FORMAT con tipi numerici  
 L'esempio seguente restituisce 5 righe di **currencyrate** tabella il [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database. La colonna **EndOfDateRate** viene archiviato come tipo **money** nella tabella. In questo esempio, la colonna viene restituita senza formattazione e viene quindi formattata specificando i tipi di formato di numero, valuta e generico di .NET. Per ulteriori informazioni su questi e altri formati numerici, vedere [stringhe di formato numerico Standard](http://msdn.microsoft.com/library/dwhawy9k.aspx).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
            ,FORMAT(EndOfDayRate, 'N', 'en-us') AS 'Number Format'  
            ,FORMAT(EndOfDayRate, 'G', 'en-us') AS 'General Format'  
            ,FORMAT(EndOfDayRate, 'C', 'en-us') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1.00            1.0002          $1.00  
2              1.55          1.55            1.5500          $1.55  
3              1.9419        1.94            1.9419          $1.94  
4              1.4683        1.47            1.4683          $1.47  
5              8.2784        8.28            8.2784          $8.28  
  
(5 row(s) affected)  
  
```  
  
 In questo esempio vengono specificate le impostazioni cultura tedesche (de-de).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
      ,FORMAT(EndOfDayRate, 'N', 'de-de') AS 'Numeric Format'  
      ,FORMAT(EndOfDayRate, 'G', 'de-de') AS 'General Format'  
      ,FORMAT(EndOfDayRate, 'C', 'de-de') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1,00            1,0002          1,00 €  
2              1.55          1,55            1,5500          1,55 €  
3              1.9419        1,94            1,9419          1,94 €  
4              1.4683        1,47            1,4683          1,47 €  
5              8.2784        8,28            8,2784          8,28 €  
  
 (5 row(s) affected)  
```  
  
###  <a name="ExampleD"></a> D. FORMAT con tipi di dati ora  
 FORMAT restituisce NULL in questi casi, perché `.` e `:` non di escape.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh.mm');   --> returns NULL  
SELECT FORMAT(cast('07:35' as time), N'hh:mm');   --> returns NULL  
```  
  
 Format restituisce una stringa formattata in quanto il `.` e `:` vengono sottoposti a escape.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh\.mm');  --> returns 07.35  
SELECT FORMAT(cast('07:35' as time), N'hh\:mm');  --> returns 07:35  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

