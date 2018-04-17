---
title: Le voci del Registro di sistema per le origini dati | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fe69d4c897491166a632bbc38f466aadfb9a1e63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registry-entries-for-data-sources"></a>Voci del Registro di sistema per le origini dati
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo in modo esplicito, è necessario installare ODBC nelle versioni precedenti di Windows.  
  
 Il programma di installazione DLL mantiene le informazioni nel Registro di sistema su ogni origine dati. In Microsoft Windows NT o Windows 2000 e Microsoft Windows 95/98, queste informazioni vengono archiviate nelle sottochiavi in uno dei seguenti due chiavi del Registro di sistema:  
  
 HKEY_LOCAL_MACHINE  
  
 SOFTWARE  
  
 ODBC  
  
 ODBC  
  
 HKEY_CURRENT_USER  
  
 SOFTWARE  
  
 ODBC  
  
 ODBC  
  
 La chiave utilizzata varia a seconda che l'origine dati un *origine dati di sistema,* disponibile a tutti gli utenti o un *origine dati utente,* che è disponibile solo per l'utente corrente. Origini dati di sistema vengono archiviate nella struttura HKEY_LOCAL_MACHINE e origini dati utente vengono archiviate nella struttura HKEY_CURRENT_USER. Tutti gli altri aspetti, origini dati di sistema e le origini dati utente sono identiche.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Sottochiave ODBC Data Sources](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Sottochiavi di specifica dell'origine dati](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Sottochiave Default](../../../odbc/reference/install/default-subkey.md)  
  
-   [Sottochiave ODBC](../../../odbc/reference/install/odbc-subkey.md)
