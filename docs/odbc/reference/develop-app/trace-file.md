---
title: File di traccia | Documenti Microsoft
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
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5c6c58e297e862d0e2241fe216dc7eb82bd4238
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="trace-file"></a>File di traccia
Un'applicazione specifica il file di traccia impostando il **TraceFile** parola chiave nella voce del Registro di sistema ODBC o chiamando **SQLSetConnectAttr** con l'attributo di connessione SQL_ATTR_TRACEFILE. Se il file non esiste quando la traccia è abilitata, gestione Driver verrà creato il file. Ogni applicazione deve avere un proprio file di traccia dedicato per evitare conflitti. Un'applicazione può utilizzare più di un file di traccia. il programma di installazione di un'applicazione può fornire all'utente una scelta di file di traccia. Se è attivata in modo dinamico, un'applicazione può anche visualizzare i risultati della traccia, anziché la registrazione nel file di traccia.  
  
 Il file di traccia fornisce i valori di tutti gli argomenti e un log di ogni chiamata di funzione ODBC con i tipi di dati. Registra le funzioni di tutti gli input ed esegue tutte le funzioni restituite con i codici restituiti e gli stati di errore.  
  
 In ODBC 3*x*, parametri delle funzioni di connessione non disponibili per la DLL di traccia.
