---
title: Le voci del Registro di sistema (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83c2d0752cc8b786a9de84d1a5005a8bc0c5b5f5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Voci del Registro di sistema (Driver ODBC di Visual FoxPro)
Quando si installa il Driver ODBC di Visual FoxPro, il programma di installazione aggiorna il Registro di sistema nella chiave del Registro di sistema HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, per aggiungere una nuova chiave denominata driver per Microsoft Visual FoxPro. In tale chiave, vengono aggiunti i valori descritti nella tabella seguente.  
  
|Nome del valore|Tipo valore|Valore|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ.|"1"|  
|ConnectFunctions|REG_SZ.|"YYN"|  
|Driver|REG_SZ.|Percorso di sistema per il file vfpodbc|  
|DriverODBCVer|REG_SZ.|"02.50"|  
|FileExtns|REG_SZ.|"*. dbf,\*cdx,\*.fpt"|  
|FileUsage|REG_SZ.|"1"|  
|Installazione|REG_SZ.|Percorso di sistema per il file vfpodbc|  
|SQLLevel|REG_SZ.|"0"|  
  
 Il programma di installazione aggiunge anche la chiave "Visual FoxPro Files", che rappresenta il driver di Visual FoxPro predefinito, alla chiave HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini del sistema. In questa chiave, il programma di installazione aggiunge i valori descritti nella tabella seguente.  
  
|Nome del valore|Tipo valore|Valore|  
|----------------|----------------|-----------|  
|Driver|REG_SZ.|Percorso di sistema per il file vfpodbc|  
  
 Ogni volta che si aggiunge un'origine dati ODBC Visual FoxPro alla configurazione di ODBC, viene aggiunta una nuova chiave per tale nome origine dati. I valori per l'origine dati corrispondono ai valori impostati il **installazione ODBC Visual FoxPro** la finestra di dialogo, come indicato nella tabella seguente.  
  
|Nome del valore (parola chiave)|Tipo valore|Valore|  
|----------------------------|----------------|-----------|  
|Fascicola|REG_SQ|Sequenza di confronto supportate|  
|Description|REG_SZ.|Descrizione dell'origine dati utente|  
|Driver||Percorso di sistema per il file vfpodbc|  
|Exclusive||Sì o No|  
|BackgroundFetch||Sì o No|  
|SourceDB|REG_SZ.|Percorso. File DBC|  
|SourceType|REG_SZ.|"DBC" o "DBF"|  
  
 Non è necessario accedere direttamente; queste informazioni qualsiasi amministrazione del Registro di sistema viene gestita dall'amministratore ODBC quando si aggiungere, modificare o eliminare un'origine dati.  
  
 È possibile utilizzare alcune di queste parole chiave e i valori come parametri in di [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) funzione API ODBC.
