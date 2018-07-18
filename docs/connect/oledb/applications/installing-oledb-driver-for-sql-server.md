---
title: Installazione del Driver OLE DB per SQL Server | Documenti Microsoft
description: Installazione e disinstallazione di Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0cbe9e82dac58e3ba4d15f4a608d914c73987af1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installazione del Driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Per installare il Driver OLE DB per SQL Server è necessario msoledbsql.msi installer.
Eseguire il programma di installazione e verificare le selezioni preferite. Il Driver OLE DB per SQL Server può essere installato side-by-side con versioni precedenti di provider Microsoft OLE DB.

Il Driver OLE DB per i file di SQL Server (msoledbsql.dll, msoledbsqlr.rll) vengono installati nella `%SYSTEMROOT%\system32\` . Inoltre, x64 msoledbsql.msi installa i file binari a 32 bit in `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Tutte le impostazioni del Registro di sistema appropriati per il Driver OLE DB per SQL Server vengono eseguite come parte del processo di installazione.  

Il Driver OLE DB per SQL Server libreria file di intestazione e (msoledbsql.h e msoledbsql.lib) vengono installati nella `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`. Inoltre, x64 msoledbsql.msi installa i file stesso in `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`.  

È possibile distribuire il Driver OLE DB per SQL Server tramite msoledbsql.msi. Potrebbe essere necessario installare il Driver OLE DB per SQL Server quando si distribuisce un'applicazione. Un modo per installare più pacchetti in un'installazione che all'utente può sembrare singola consiste nell'usare la tecnologia del chainer e del programma di avvio automatico. Per ulteriori informazioni, vedere [Authoring a Custom Bootstrapper Package for Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) e [aggiunta di prerequisiti personalizzati](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
X64 msoledbsql.msi installa anche la versione a 32 bit del Driver OLE DB per SQL Server. Se l'applicazione è destinata a una piattaforma diversa da quella che in cui è stata sviluppata, è possibile scaricare le versioni di msoledbsql.msi per x64 e x86.

Quando si richiama msoledbsql.msi, solo i componenti client vengono installati per impostazione predefinita. Il client sono i componenti sono file che supportano l'esecuzione di un'applicazione sviluppata tramite il Driver OLE DB per SQL Server. Per installare i componenti SDK, specificare `ADDLOCAL=All` sulla riga di comando. Esempio:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installazione invisibile all'utente  
 Se si utilizza il /passive, /qn, /qb o l'opzione /qr con msiexec, è necessario specificare anche IACCEPTMSOLEDBSQLLICENSETERMS = Sì, per indicare in modo esplicito si accettano le condizioni di licenza per l'utente finale. È necessario specificare questa opzione in lettere maiuscole.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installazione del Driver OLE DB per SQL Server come una dipendenza  
È importante non disinstallare il Driver OLE DB per SQL Server fino a quando non tutte le applicazioni dipendenti vengono disinstallate. Per fornire agli utenti con un avviso che l'applicazione dipende dal Driver OLE DB per SQL Server, utilizzare l'opzione di installazione APPGUID in MSI, come segue:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Il valore passato a APPGUID è il codice prodotto specifico. Quando si utilizza Microsoft Installer per aggregare il programma di installazione dell'applicazione, è necessario creare un codice prodotto.
L'opzione APPGUID richiede che esegue il programma di installazione da un prompt dei comandi con privilegi elevati.

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
