---
title: Requisiti di sistema, installazione e i file dei Driver | Documenti Microsoft
ms.custom: ''
ms.date: 02/14/2018
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
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1837964d0c0c7736890dd8e73d4e04ced90cda8a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="system-requirements-installation-and-driver-files"></a>Requisiti di sistema, installazione e file del driver
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] supporta connessioni a SQL Server 2014, SQL Server 2012 R2, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro_md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]e [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)].  
  
In Windows è possibile installare ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in un computer che dispone anche di una o più versioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  
  
ODBC Driver 13 e 13.1 per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], oltre a quanto sopra, supporta SQL Server 2016. 

Il 17 del Driver ODBC per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] supporta tutte quelle precedenti, nonché 2017 di SQL Server.
  
Il nome del driver specificato nella stringa di connessione è `ODBC Driver 11 for SQL Server` o `ODBC Driver 13 for SQL Server` (per 13 e 13.1) o `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Sistemi operativi supportati

È possibile eseguire applicazioni con il driver nei sistemi operativi Windows seguenti:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(solo per ODBC Driver 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installazione di Microsoft ODBC Driver for SQL Server

Il driver viene installato quando si esegue `msodbcsql.msi` da uno dei seguenti collegamenti:

- [Scaricare Microsoft ODBC Driver 17 per SQL Server in Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Scaricare Microsoft ODBC Driver 13.1 for SQL Server in Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Scaricare Microsoft ODBC Driver 13 for SQL Server in Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Scaricare Microsoft ODBC Driver 11 for SQL Server in Windows](https://www.microsoft.com/download/details.aspx?id=36434). 

Può essere installato side-by-side con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client.  

Quando si richiama `msodbcsql.msi`, solo i componenti client vengono installati per impostazione predefinita. I componenti client sono file che supportano l'esecuzione di un'applicazione sviluppata tramite il driver. Per installare i componenti SDK, specificare `ADDLOCAL=ALL` nella riga di comando. Esempio:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Specificare `IACCEPTMSODBCSQLLICENSETERMS=YES` per accettare le condizioni della licenza dell'utente finale se si utilizza il `/passive`, `/qn`, `/qb`, o `/qr` opzione di installazione. È necessario specificare questa opzione in lettere maiuscole. Esempio:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Per eseguire una disinstallazione invisibile all'utente:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Quando un'applicazione utilizza il driver, l'applicazione deve indicare che dipende dal driver tramite l'opzione di installazione `APPGUID`. In questo modo consente l'installazione di driver per segnalare le applicazioni dipendenti prima della disinstallazione. Per specificare una dipendenza sul driver, impostare il `APPGUID` parametro della riga di comando per il codice di prodotto durante l'installazione invisibile all'utente il driver. Quando si usa Microsoft Installer per aggregare il programma di installazione dell'applicazione, è necessario creare un codice prodotto. Esempio:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Gli strumenti da riga di comando: sqlcmd.exe e bcp.exe

Il `bcp.exe` e `sqlcmd.exe` degli strumenti per l'utilizzo con il driver può essere scaricato da [Microsoft Command Line Utilities 11 for SQL Server](http://www.microsoft.com/download/details.aspx?id=36433), [13 utilità della riga di comando di Microsoft per SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), o [Microsoft Command Line Utilities 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Il driver è un prerequisito per l'installazione `sqlcmd.exe` e `bcp.exe`.
  
`bcp.exe` e `sqlcmd.exe` vengono installati nel `110\Tools` sottocartella di `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` per la versione 11 e `130\Tools` per 13 e 13.1.

Un'applicazione che Usa funzioni BCP deve specificare il driver della stessa versione fornita con il file di intestazione e la libreria usati per compilare l'applicazione.  

Ad esempio, quando si compila un'applicazione ODBC con `msodbcsql11.lib` e `msodbcsql.h`, usare "DRIVER = {ODBC Driver 11 for SQL Server}" nella stringa di connessione.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Componenti di Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] in Windows 
 Il driver ODBC in Windows contiene i componenti seguenti:
 
|Componente|Description|  
|---------------|-----------------|  
|msodbcsql17.dll o <br> msodbcsql13.dll or <br> msodbcsql11.dll|File della DLL (Dynamic-Link Library, libreria di collegamento dinamico) che contiene tutte le funzionalità del driver. Questo file viene installato in % SYSTEMROOT%\System32.|  
|msodbcdiag17.dll o <br> msodbcdiag13.dll o <br> msodbcdiag11.dll|Il file di libreria a collegamento dinamico (DLL) che contiene l'interfaccia di diagnostica (analisi) del driver. Questo file viene installato in % SYSTEMROOT%\System32.|
|msodbcsqlr17.RLL o <br> msodbcsqlr13.rll or <br> msodbcsqlr11.rll|File di risorse associato per la libreria del driver. Questo file viene installato in % SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm o <br> s11ch_msodbcsql.chm |Il file della Guida Creazione guidata origine dati che illustra come creare un'origine dati per il driver. Questo file viene installato in %SYSTEMROOT%\System32\1033 <br /> <br /> **Nota:** è presente alcun file chm per 17 Driver ODBC. |  
|msodbcsql.h|Il file di intestazione che contiene tutte le nuove definizioni necessarie per l'utilizzo del driver.<br /><br /> **Nota:**  non è possibile fare riferimento a msodbcsql.h e odbcss.h nello stesso programma.<br /><br /> msodbcsql. h per ODBC Driver 17 o 13 viene installato in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql. h per ODBC Driver 11 viene installato in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib or <br> msodbcsql13.lib or <br> msodbcsql11.lib|Il file di libreria necessario per chiamare il **bcp** funzioni di utilità che fanno parte del driver.<br /><br /> **Nota:** se si fa riferimento questo file di libreria nel programma, assicurarsi che sia nel percorso di sistema e nel percorso di sistema di quelli che usano l'applicazione.<br /><br /> msodbcsql17.lib o msodbcsql13.lib viene installato in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib viene installato in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a>Vedere anche  
 [Microsoft ODBC Driver for SQL Server in Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
