---
title: Driver specifica sottochiavi | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], driver specification subkeys
- driver specification subkeys [ODBC]
- registry entries for components [ODBC], driver specification subkeys
- drivers subkey [ODBC]
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f45130c81f9fc4f669cf95d4bde72155f519c1aa
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-specification-subkeys"></a>Sottochiavi di specifica di driver
Ogni driver elencate nella sottochiave del driver ODBC ha una sottochiave propri. Questa sottochiave ha lo stesso nome come valore corrispondente nella sottochiave del driver ODBC. I valori in questa sottochiave elencare i percorsi completi dei driver e di installazione del driver DLL, i valori delle parole chiave driver restituite da **SQLDrivers**e il conteggio di utilizzo. I formati dei valori vengono visualizzati nella tabella seguente.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|APILevel|REG_SZ.|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ.|{**Y**&#124;** N**} {**Y**&#124;** N**} {**Y**&#124;** N**}|  
|CreateDSN|REG_SZ.|*Descrizione del driver*|  
|Driver|REG_SZ.|*percorso DLL di driver*|  
|DriverODBCVer|REG_SZ.|*nn.nn*|  
|FileExtns|REG_SZ.|**\*.** *file extension1*[**,\*.** *file extension2*]...|  
|FileUsage|REG_SZ.|**0** &#124; **1** &#124; **2**|  
|Installazione|REG_SZ.|*il programma di installazione-DLL-path.*|  
|SQLLevel|REG_SZ.|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD|*count*|  
  
 L'utilizzo di ogni parola chiave viene visualizzato nella tabella seguente.  
  
|Parola chiave|Utilizzo|  
|-------------|-----------|  
|**APILevel**|Un numero che indica ODBC interfaccia a livello di conformità supportata dal driver:<br /><br /> 0 = Nessuno<br /><br /> 1 = 1 livello supportato<br /><br /> 2 = livello 2 è supportato<br /><br /> Deve essere uguale al valore restituito per l'opzione SQL_ODBC_INTERFACE_CONFORMANCE in **SQLGetInfo**.|  
|**CreateDSN**|Il nome di uno o più origini dati da creare quando viene installato il driver. Le informazioni di sistema devono includere una sezione specifica di origine dati per ogni origine dati elencati con il **CreateDSN** (parola chiave). Queste sezioni non devono includere il **Driver** (parola chiave), perché questo è specificato nella sezione specifica di driver, ma deve includere le informazioni necessarie per il **ConfigDSN** nel driver (funzione) DLL per creare una specifica origine dati senza visualizzare finestre di dialogo del programma di installazione. Per il formato di una sezione specifica di origine dati, vedere [sottochiavi specifica di origine dati](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Una stringa di tre caratteri che indica se il driver supporta **SQLConnect**, **SQLDriverConnect**, e **SQLBrowseConnect**. Se il driver supporta **SQLConnect**, il primo carattere è "Y" in caso contrario, è "N". Se il driver supporta **SQLDriverConnect**, il secondo carattere è "Y" in caso contrario, è "N". Se il driver supporta **SQLBrowseConnect**, il terzo carattere è "Y" in caso contrario, è "N". Ad esempio, se un driver supporta **SQLConnect** e **SQLDriverConnect** ma non **SQLBrowseConnect**, la stringa di tre caratteri è "YYN".|  
|**DriverODBCVer**|Una stringa di caratteri con la versione di ODBC supportate dal driver. La versione è nel formato *nn.nn*, dove le prime due cifre indicano la versione principale e le due cifre successive sono la versione secondaria. Per la versione di ODBC descritto in questo documento, il driver deve restituire "03.00".<br /><br /> Deve essere uguale al valore restituito per l'opzione SQL_DRIVER_ODBC_VER in **SQLGetInfo**.|  
|**FileExtns**|Per i driver basati su file, un elenco delimitato da virgole delle estensioni dei file il driver può utilizzare. Ad esempio, è necessario specificare un driver dBASE \*con estensione dbf e un driver di file di testo formattato può specificare \*. txt,\*CSV. Per un esempio di come un'applicazione può utilizzare queste informazioni, vedere il **FileUsage** (parola chiave).|  
|**FileUsage**|Numero che indica il modo in cui un driver basati su file considera direttamente i file in un'origine dati.<br /><br /> 0 = il driver non è un driver basati su file. Ad esempio, un driver ORACLE è un driver basati su DBMS.<br /><br /> 1 = un file di driver basati su file considera in un'origine dati come tabelle. Ad esempio, un driver Xbase considera ogni file Xbase come una tabella.<br /><br /> 2 = i file considera un driver basati su file in un'origine dati come un catalogo. Ad esempio, un driver Microsoft® Access considera ogni file di Microsoft Access come un database completo.<br /><br /> Un'applicazione può utilizzare per determinare come gli utenti la selezione dei dati. Ad esempio, gli utenti Xbase e Paradox considerare spesso i dati archiviati in file, mentre gli utenti ORACLE e Microsoft Access in genere considerate dei dati archiviati nelle tabelle.<br /><br /> Quando un utente seleziona **Apri File di dati** dal **File** menu, un'applicazione può visualizzare il **Windows File Open** la finestra di dialogo comune. Utilizza le estensioni di file specificate con l'elenco dei tipi di file di **FileExtns** (parola chiave) per i driver che specificano un **FileUsage** valore 1 e "Y", come il secondo carattere del valore del ** ConnectFunctions** (parola chiave). Dopo che l'utente seleziona un file, l'applicazione chiama **SQLDriverConnect** con il **DRIVER** (parola chiave) e quindi eseguire una **selezionare \* FROM *-nome della tabella * ** istruzione.<br /><br /> Quando l'utente seleziona **l'importazione dei dati** dal **File** menu, un'applicazione potrebbe visualizzare un elenco di descrizioni per i driver che specificano un **FileUsage** valore pari a 0 o 2 e "Y" come il carattere del valore del secondo il **ConnectFunctions** (parola chiave). Dopo che l'utente seleziona un driver, l'applicazione chiama **SQLDriverConnect** con il **DRIVER** (parola chiave) e quindi visualizzare un oggetto personalizzato **Seleziona tabella** la finestra di dialogo.|  
|**SQLLevel**|Numero che indica la grammatica SQL-92 supportata dal driver:<br /><br /> 0 = voce SQL-92<br /><br /> 1 = transizione FIPS127-2<br /><br /> 2 = intermedio di SQL-92<br /><br /> 3 = Full SQL-92<br /><br /> Deve essere uguale al valore restituito per l'opzione SQL_SQL_CONFORMANCE in **SQLGetInfo**.|  
  
 Per informazioni su conteggi dell'utilizzo, vedere [il conteggio di utilizzo](../../../odbc/reference/install/usage-counting.md) più indietro in questa sezione.  
  
 Applicazioni non devono impostare il conteggio di utilizzo. ODBC manterrà il conteggio.  
  
 Ad esempio, si supponga che un driver per i file di testo formattato è un DLL denominata Text.dll driver, un programma di installazione di driver separato DLL denominato Txtsetup.dll e installato tre volte. Se il driver supporta il livello di conformità di API di livello 1, supporta il livello di conformità di grammatica SQL minima, i file vengono considerati tabelle e può utilizzare un file con estensione txt e CSV, i valori nella sottochiave del testo potrebbero essere come segue:  
  
```  
APILevel : REG_SZ : 1  
ConnectFunctions : REG_SZ : YYN  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\TEXT.DLL  
DriverODBCVer : REG_SZ : 03.00.00  
FileExtns : REG_SZ : *.txt,*.csv  
FileUsage : REG_SZ : 1  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\TXTSETUP.DLL  
SQLLevel : REG_SZ : 0  
UsageCount : REG_DWORD : 0x3  
```

