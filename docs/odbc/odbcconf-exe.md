---
title: ODBCCONF. EXE | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f7a6e48f6a7a17c8ea3decd79d765fb176080e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914306"
---
# <a name="odbcconfexe"></a>ODBCCONF. FILE EXE
ODBCCONF.exe è uno strumento da riga di comando che consente di configurare i nomi delle origini dati e i driver ODBC.  
  
> [!NOTE]  
>  ODBCCONF.exe verrà rimossa in una versione futura di Windows Data Access Components. Evitare di utilizzarla e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. È possibile utilizzare i comandi di PowerShell per gestire i driver e origini dati. Per ulteriori informazioni su questi comandi di PowerShell, vedere [i cmdlet di Windows Data Access Components](https://technet.microsoft.com/library/hh771019.aspx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Argomenti  
 *Switch*  
 Zero o più opzioni. Per l'elenco di opzioni disponibili, vedere la sezione Osservazioni, più avanti in questo argomento.  
  
 *action*  
 Un'azione da eseguire. Per l'elenco delle opzioni disponibili, vedere la sezione Osservazioni.  
  
## <a name="remarks"></a>Osservazioni  
 Sono disponibili le opzioni seguenti:  
  
|Opzione|Description|  
|------------|-----------------|  
|/A {*azione*}|Specificare un'azione.<br /><br /> /A è facoltativo se è specificata un'azione.|  
|/?|Visualizzare l'utilizzo per ODBCCONF. FILE EXE.|  
|/C|L'elaborazione continua se un'azione ha esito negativo.|  
|/E|Cancellare il file di risposta specificato con /F al termine dell'elaborazione.|  
|/F|Utilizzare un file di risposta, ad esempio `odbcconf /F my.rsp`.<br /><br /> My.rsp potrebbe essere simile al seguente: `REGSVR c:\my.dll`<br /><br /> /A non viene usato in un file di risposta.|  
|/H|Visualizzare l'utilizzo (Guida). Questa opzione è analoga /?.|  
|/ L [*modalità*] *filename*|Inviare l'output del programma in un file in una delle tre modalità: normale (n), dettagliato (v) e debug (d). Le DLL caricate dal odbcconf.exe i record delle modalità di debug.<br /><br /> Se si specifica /L senza una modalità, il file di log sarà vuoto.<br /><br /> Ad esempio, **>.log.txt /Lv**.|  
|/R|L'azione verrà eseguita dopo un riavvio.|  
|/S|Modalità invisibile all'utente. Non vengono visualizzati messaggi di errore.|  
  
 Sono disponibili le azioni seguenti:  
  
|Azione|Description|  
|------------|-----------------|  
|CONFIGDRIVER *nome_driver * * i parametri di configurazione specifiche del driver*|Carica la DLL di installazione del driver appropriato e chiama il **ConfigDriver** (funzione).<br /><br /> Equivale al [SQLConfigDriver funzione](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Esempio:<br /><br /> /A {CONFIGDRIVER "Nome Driver" "CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER "Nome Driver" "DriverODBCVer = 03.80"}|  
|CONFIGDSN *nome_driver* DSN =*nome* &#124; *gli attributi*|Aggiunge o modifica un'origine dati di sistema.<br /><br /> Equivale al [funzione SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Esempio:<br /><br /> /A {CONFIGDSN "SQL Server" "DSN = nome &#124; Server = srv"}|  
|CONFIGSYSDSN *nome_driver* DSN =*nome* &#124; *gli attributi*|Aggiunge o modifica un'origine dati di sistema.<br /><br /> Equivale al [funzione SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Esempio:<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN = nome &#124; Server = srv"}|  
|INSTALLDRIVER|Equivalente a [SQLInstallDriverEx funzione](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Per informazioni sulla sintassi delle coppie parola chiave / valore passata a INSTALLDRIVER, vedere [sottochiavi specifica del Driver](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Esempio:<br /><br /> /A {INSTALLDRIVER "Driver &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage = 0 &#124; SQLLevel = 1"}|  
|INSTALLTRANSLATOR *configurazione traduttore * * percorso di driver*|Aggiunge informazioni su una funzione di conversione per la **HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. Funzioni di conversione INI\ODBC** chiave del Registro di sistema.<br /><br /> Equivalente a [SQLInstallTranslatorEx funzione](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Per informazioni sulla sintassi delle coppie parola chiave / valore passata a INSTALLDRIVER, vedere [traduttore specifica sottochiavi](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Esempio:<br /><br /> /A {INSTALLTRANSLATOR "la funzione di conversione &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll"}|  
|REGSVR *dll*|Registra una DLL.<br /><br /> Equivale a regsvr32.exe.<br /><br /> Esempio:<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|Quando HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC DSN\DefaultDSNDir di File non esiste, l'azione SETFILEDSNDIR la creerà e assegnarvi il valore in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, aggiunto con \ODBC\Data origini.<br /><br /> Il valore HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC File DSN\DefaultDSNDir specifica il percorso predefinito utilizzato dall'amministratore origine dati ODBC per la creazione di un'origine dati basata su file.<br /><br /> Esempio:<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
