---
title: Origini dati | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 479cc73538bf94499f2762cca528d2cec72ff3b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675360"
---
# <a name="data-sources"></a>Origini dati
Oggetto *zdroj dat* è semplicemente l'origine dei dati. Può essere un file, un database specifico in un sistema DBMS o persino un feed di dati in tempo reale. I dati potrebbero trovarsi nello stesso computer del programma, o in un altro computer in una posizione in una rete. Ad esempio, un'origine dati potrebbe essere un DBMS Oracle in esecuzione in un sistema operativo OS/2®, accessibile da Novell Netware®; un DBMS di IBM DB2 si accede tramite un gateway. una raccolta di file Xbase in una directory di server. o un file di database locale di Microsoft® Access.  
  
 Lo scopo di un'origine dati è quello di raccogliere tutte le informazioni tecniche necessarie per accedere ai dati, ovvero il nome del driver, l'indirizzo di rete, il software di rete e così via, in un unico posizionare e lo nasconde da parte dell'utente. L'utente deve essere in grado di esaminare un elenco che include delle retribuzioni, inventario e il personale, scegliere nell'elenco delle retribuzioni e che l'applicazione di connettersi ai dati di payroll, tutto senza sapere dove risiedono i dati di payroll o come l'applicazione è arrivati a esso.  
  
 Il termine *zdroj dat* non deve essere confuso con termini simili. In questo manuale *DBMS* oppure *database* fa riferimento a un programma di database o del motore. Un ulteriore distinguono *database per desktop,* progettato per l'esecuzione in un personal computer e spesso mancano di SQL completa e il supporto delle transazioni, e *database del server,* progettato per essere eseguito in un client / situazione di server e caratterizzate da un motore di database autonoma e SQL avanzate e il supporto delle transazioni. *Database* fa riferimento anche a una determinata raccolta di dati, ad esempio una raccolta di file Xbase in una directory o un database in SQL Server. Equivale a livello generale per il termine *catalogo* usate più avanti in questo manuale o il termine *qualificatore* nelle versioni precedenti di ODBC.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di origini dati](../../odbc/reference/types-of-data-sources.md)  
  
-   [Uso delle origini dati](../../odbc/reference/using-data-sources.md)  
  
-   [Esempio di origine dati](../../odbc/reference/data-source-example.md)
