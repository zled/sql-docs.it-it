---
title: Le conversioni eseguite dal Server al Client | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], server to client
ms.assetid: 676fdf24-fb72-4ea0-a8d2-2b197da3c83f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1ec005ab299a8be40e977ccf6a3a8f318591b86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167199"
---
# <a name="conversions-performed-from-server-to-client"></a>Conversioni eseguite da server a client
  In questo argomento vengono illustrate le conversioni di data/ora eseguite tra [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) e un'applicazione client scritta con OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="conversions"></a>Conversioni  
 Nella tabella seguente vengono descritte le conversioni tra il tipo restituito al client e il tipo presente nell'associazione. Per i parametri di output, se è stato chiamato ICommandWithParameters:: SetParameterInfo e il tipo specificato in *pwszDataSourceType* non corrisponde il tipo effettivo del server, una conversione implicita verrà eseguito dal server , e il tipo restituito al client corrisponderà al tipo specificato tramite ICommandWithParameters:: SetParameterInfo. Se le regole di conversione del server sono diverse da quelle descritte in questo argomento, la conversione potrebbe dare risultati imprevisti. Quando ad esempio è necessario specificare una data predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza 1900-1-1 anziché 1899-12-30.  
  
|A -><br /><br /> From|DATE|DBDATE|DBTIME|DBTIME2|DBTIMESTAMP|DBTIMESTAMPOFFSET|FILETIME|BYTES|VARIANT|SSVARIANT|BSTR|STR|WSTR|  
|----------------------|----------|------------|------------|-------------|-----------------|-----------------------|--------------|-----------|-------------|---------------|----------|---------|----------|  
|date|1,7|OK|-|-|1|1,3|1,7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Time|5,6,7|-|9|OK|6|3,6|5,6|-|OK (VT_BSTR)|OK|OK|4|4|  
|Smalldatetime|7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|DATETIME|5,7|8|9,10|10|OK|3|7|-|7 (VT_DATE)|OK|OK|4|4|  
|Datetime2|5,7|8|9,10|10|7|3|5,7|-|OK (VT_BSTR)|OK|OK|4|4|  
|Datetimeoffset|5,7,11|8,11|9,10,11|10,11|7,11|OK|5,7,11|-|OK (VT_BSTR)|OK|OK|4|4|  
|Char, Varchar,<br /><br /> Nchar, Nvarchar|7, 13|12|12,9|12|12|12|7,13|N/D|N/D|N/D|N/D|N/D|N/D|  
|Sql_variant<br /><br /> (datetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (smalldatetime)|7|8|9,10|10|OK|3|7|-|7(VT_DATE)|OK|OK|4|4|  
|Sql_variant<br /><br /> (date)|1,7|OK|2|2|1|1,3|1,7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (time)|5,6,7|2|6|OK|6|3,6|5,6|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetime2)|5,7|8|9,10|10|OK|3|5,7|-|OK(VT_BSTR)|OK|OK|4|4|  
|Sql_variant<br /><br /> (datetimeoffset)|5,7,11|8,11|9,10,11|10,11|7,11|OK|5,7,11|-|OK(VT_BSTR)|OK|OK|4|4|  
  
## <a name="key-to-symbols"></a>Descrizione dei simboli  
  
|Simbolo|Significato|  
|------------|-------------|  
|OK|Nessuna conversione necessaria.|  
|-|Non viene supportata alcuna conversione. Se l'associazione viene convalidato quando viene chiamato IAccessor:: CreateAccessor, viene restituito DBBINDSTATUS_UPSUPPORTEDCONVERSION in *rgStatus*. Quando la convalida della funzione di accesso viene rinviata, viene impostato DBSTATUS_E_BADACCESSOR.|  
|1|I campi relativi all'ora vengono impostati su zero.|  
|2|Viene impostato DBSTATUS_E_CANTCONVERTVALUE.|  
|3|Il fuso orario viene impostato su zero.|  
|4|Se le dimensioni del buffer client non sono sufficienti, viene impostato DBSTATUS_S_TRUNCATED. Quando il tipo di server include secondi frazionari, il numero di cifre nella stringa del risultato corrisponde esattamente alla scala del tipo di server.|  
|5|Il troncamento dei secondi o dei secondi frazionari viene ignorato.|  
|6|La data viene impostata sul valore corrente, a meno che l'origine non sia una stringa con valore letterale ora e la destinazione non sia DBTYPE_DATE. In questo caso viene utilizzato il valore 1899-12-30.|  
|7|Se il valore comporta un overflow, viene impostato DBSTATUS_E_DATAOVERFLOW.|  
|8|I campi relativi all'ora vengono ignorati.|  
|9|I campi relativi ai secondi frazionari vengono ignorati.|  
|10|Il componente relativo alla data viene ignorato.|  
|11|Viene effettuata la conversione dell'ora nel fuso orario del client. Se si verifica un errore durante questa conversione, viene impostato DBSTATUS_E_DATAOVERFLOW.|  
|12|La stringa viene analizzata come valore letterale ISO e convertita nel tipo di destinazione. Se l'operazione non riesce, la stringa viene analizzata come valore letterale data OLE (che presenta anche componenti di ora) e convertita da data OLE (DBTYPE_DATE) nel tipo di destinazione. La stringa deve essere conforme alla sintassi per i valori letterali del tipo di destinazione consentiti per la riuscita dell'analisi del formato ISO. Perché l'analisi OLE riesca, è necessario che la stringa sia conforme alla sintassi riconosciuta da OLE. Se non è possibile analizzare la stringa, viene impostato DBSTATUS_E_CANTCONVERTVALUE. Se sono presenti valori di componente esterni all'intervallo, viene impostato DBSTATUS_E_DATAOVERFLOW.|  
|13|La stringa viene analizzata come valore letterale ISO e convertita nel tipo di destinazione. Se l'operazione non riesce, la stringa viene analizzata come valore letterale data OLE (che presenta anche componenti di ora) e convertita da data OLE (DBTYPE_DATE) nel tipo di destinazione. La stringa deve essere conforme alla sintassi per i valori letterali di data e ora, a meno che la destinazione non sia DBTYPE_DATE o DBTYPE_DBTIMESTAMP. In questo caso, per la riuscita dell'analisi del formato ISO è consentito un valore letterale data e ora oppure ora. Perché l'analisi OLE riesca, è necessario che la stringa sia conforme alla sintassi riconosciuta da OLE. Se non è possibile analizzare la stringa, viene impostato DBSTATUS_E_CANTCONVERTVALUE. Se sono presenti valori di componente esterni all'intervallo, viene impostato DBSTATUS_E_DATAOVERFLOW.|  
  
## <a name="see-also"></a>Vedere anche  
 [Associazioni e conversioni &#40;OLE DB&#41;](conversions-ole-db.md)  
  
  
