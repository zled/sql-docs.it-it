---
title: Origini dati | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 84c415fd10a757cebfc365759d7fb038f9630ec4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="data-sources"></a>Origini dati
Oggetto *origine dati* è semplicemente l'origine dei dati. Può trattarsi di un file, un database specifico in un DBMS o anche un feed di dati in tempo reale. I dati potrebbero trovarsi nello stesso computer del programma, o in un altro computer in un punto qualsiasi in una rete. Ad esempio, un'origine dati potrebbe essere un DBMS Oracle in esecuzione in un sistema operativo OS/2®, accede Novell® Netware. un DBMS di IBM DB2 tramite un gateway. una raccolta di file Xbase in una directory di server. o un file di database locale di Microsoft® Access.  
  
 Lo scopo di un'origine dati è quello di raccogliere tutte le informazioni tecniche necessarie per accedere ai dati, ovvero il nome del driver, indirizzo di rete, il software di rete e così via, in un unico inserire e fare in modo da parte dell'utente. L'utente deve essere in grado di esaminare un elenco che include retribuzioni, inventario e personale, scegliere retribuzioni dall'elenco e avere l'applicazione di connettersi ai dati degli stipendi, tutto senza dover sapere dove risiedono i dati del libro paga o come l'applicazione è giunto a esso.  
  
 Il termine *origine dati* non deve essere confuso con condizioni analoghe. In questo manuale, *DBMS* o *database* fa riferimento a un programma di database o di un motore. Un ulteriore distinguono *database desktop,* progettato per l'esecuzione in un personal computer e spesso mancano SQL completo e il supporto delle transazioni, e *database del server,* progettato per l'esecuzione in un client / situazione di server e caratterizzati da un motore di database autonoma e SQL completo e il supporto delle transazioni. *Database* fa riferimento anche a un insieme specifico di dati, ad esempio una raccolta di file Xbase in una directory o un database in SQL Server. È in genere equivalente al termine *catalogo,* utilizzato altrove in questo manuale o il termine *qualificatore* nelle versioni precedenti di ODBC.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di origini dati](../../odbc/reference/types-of-data-sources.md)  
  
-   [Uso delle origini dati](../../odbc/reference/using-data-sources.md)  
  
-   [Esempio di origine dati](../../odbc/reference/data-source-example.md)
