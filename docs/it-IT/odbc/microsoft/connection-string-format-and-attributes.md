---
title: Formato stringa di connessione e gli attributi | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b11b36cf379d13dd3f8ea2d2913e64998da5083c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connection-string-format-and-attributes"></a>Gli attributi e formato di stringa di connessione
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Anziché utilizzare una finestra di dialogo, alcune applicazioni potrebbero richiedere una stringa di connessione che specifica le informazioni di connessione origine dati. La stringa di connessione è costituita da un numero di attributi che specificano la modalità di connessione di un driver a un'origine dati. Un attributo identifica un'informazione specifica che il driver deve conoscere per poter effettuare la connessione all'origine dati appropriata. Ogni driver potrebbe essere un set di attributi diversi, ma il formato di stringa di connessione è sempre lo stesso. Una stringa di connessione ha il formato seguente:  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Il Driver ODBC di Microsoft per Oracle supporta il formato della stringa di connessione della prima versione del driver, utilizzato `CONNECTSTRING`= anziché `SERVER=`.  
  
 Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare `Trusted_Connection=yes` anziché informazioni utente ID e password nella stringa di connessione.  
  
 È necessario specificare l'origine dati se non si specifica l'UID, PWD, SERVER (o CONNECTSTRING), assegnare un nome e attributi del DRIVER. Tuttavia, tutti gli altri attributi sono facoltativi. Se non si specifica un attributo, tale attributo predefinito a quello specificato nella relativa scheda DSN del **Amministrazione origine dati ODBC** la finestra di dialogo. Il valore dell'attributo potrebbe essere tra maiuscole e minuscole.  
  
 Gli attributi per la stringa di connessione sono i seguenti:  
  
|Attribute|Description|Valore predefinito|  
|---------------|-----------------|-------------------|  
|DSN|Nome dell'origine dati è elencato nella scheda dei driver del **Amministrazione origine dati ODBC** la finestra di dialogo.|""|  
|PWD|La password per il Server Oracle che si desidera accedere. Il driver supporta le limitazioni che Oracle inserisce alle password.|""|  
|SERVER|La stringa di connessione per il Server Oracle che si desidera accedere.|""|  
|UID|Il nome utente Server Oracle. A seconda del sistema, questo attributo potrebbe non essere facoltativo, ovvero alcune tabelle e il database potrebbero richiedere questo attributo per motivi di sicurezza.<br /><br /> Utilizzare "/" per l'utilizzo di Oracle operativo dell'autenticazione del sistema.|""|  
|BUFFERSIZE|Le dimensioni del buffer ottimale utilizzata durante il recupero di colonne.<br /><br /> Il driver ottimizza il recupero in modo che un recupero dal Server Oracle restituisce un numero di righe sufficiente per riempire un buffer di queste dimensioni. Valori più grandi tendono a migliorare le prestazioni se si recupera una grande quantità di dati.|65535|  
|SYNONYMCOLUMNS|Quando questo valore è true (1), una chiamata () API SQLColumn restituisce informazioni sulle colonne. In caso contrario, SQLColumn (() restituisce solo le colonne per le tabelle e viste. Quando questo valore non è impostato, il Driver ODBC per Oracle fornisce un accesso più rapido.|1|  
|REMARKS|Quando questo valore è true (1), il driver restituisce colonne note per il [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) set di risultati. Quando questo valore non è impostato, il Driver ODBC per Oracle fornisce un accesso più rapido.|0|  
|StdDayOfWeek|Applica lo standard ODBC per la funzione scalare DAYOFWEEK. Per impostazione predefinita questa è attiva, ma gli utenti che richiedono la versione localizzata è possono modificare il comportamento per l'utilizzo di qualsiasi risultato restituito Oracle.|1|  
|GuessTheColDef|Specifica se il driver deve restituire un valore diverso da zero per il *cbColDef* argomento di **SQLDescribeCol**. Si applica solo alle colonne in cui non sono presente alcuna scala definita Oracle, ad esempio calcolata numeriche colonne e le colonne definite come numero senza una precisione o scala. Oggetto **SQLDescribeCol** chiamata restituisce 130 per la precisione quando Oracle non vengono fornite le informazioni.|0|  
  
 Ad esempio, una stringa di connessione che si connette all'origine dati MyDataSource utilizzando il MyOracleServerOracle Server e il MyUserID utente Oracle sarà:  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 È una stringa di connessione che si connette all'origine dati MyOtherDataSource utilizzando l'autenticazione del sistema operativo e il MyOtherOracleServerOracle Server:  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```
