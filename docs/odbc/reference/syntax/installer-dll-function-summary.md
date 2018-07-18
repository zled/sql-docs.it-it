---
title: Riepilogo delle funzioni DLL Installer | Documenti Microsoft
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
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 685a0533aae91d790b48b788498aebbcb171fa93
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917387"
---
# <a name="installer-dll-function-summary"></a>Riepilogo delle funzioni DLL programma di installazione
Nella tabella seguente vengono descritte le funzioni nel programma di installazione DLL. Per ulteriori informazioni sulla sintassi e semantica per ogni funzione, vedere [Installer DLL API Reference](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Attività|Nome funzione|Scopo|  
|----------|-------------------|-------------|  
|Installazione di ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Carica la DLL di installazione specifici del driver.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Restituisce un elenco di driver installati.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Aggiunge un driver per le informazioni di sistema.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Restituisce la directory di destinazione per la gestione del Driver.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Restituisce le informazioni di stato o di errore per le funzioni del programma di installazione.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Aggiunge una funzione di conversione per le informazioni di sistema.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Consente a una libreria di programma di installazione driver o funzione di conversione per segnalare gli errori.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Rimuove le informazioni di sistema di un driver.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Rimuove le informazioni di sistema di componenti di base di ODBC.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Rimuove la funzione di conversione dalle informazioni di sistema.|  
|Configurazione delle origini dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Chiama la DLL di installazione specifici del driver.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Visualizza una finestra di dialogo per aggiungere un'origine dati.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Recupera la modalità di configurazione che indica la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Scrive un valore per le informazioni di sistema.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Visualizza una finestra di dialogo per selezionare una funzione di conversione.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Visualizza una finestra di dialogo per configurare i driver e origini dati.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Legge le informazioni di DSN su file.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Rimuove l'origine dati predefinita.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Rimuove un'origine dati.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Imposta la modalità di configurazione che indica la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Controlla la lunghezza e la validità del nome dell'origine dati.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Aggiunge un'origine dati.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Scrive le informazioni di DSN su file.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Ottiene un valore dalle informazioni di sistema.|
