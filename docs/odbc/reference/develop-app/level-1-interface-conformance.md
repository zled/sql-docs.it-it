---
title: Livello 1 interfaccia conformità | Documenti Microsoft
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
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: faae1bf56dd28f83fa3fec5c340bcf67c302def3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="level-1-interface-conformance"></a>Conformità di interfaccia di livello 1
Il livello di conformità di livello 1 interfaccia include la funzionalità di livello principale dell'interfaccia conformità funzionalità aggiuntive, ad esempio transazioni, in genere disponibili in un DBMS relazionali OLTP. Un driver conforme allo standard dell'interfaccia di livello 1 consente all'applicazione di eseguire le operazioni seguenti, oltre alle funzionalità del livello di conformità interfaccia Core:  
  
|||  
|-|-|  
|101|Specificare lo schema del database, tabelle e viste (tramite nomi in due parti). (Per ulteriori informazioni, vedere i nomi in tre parti funzionalità 201 in [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Richiamare true esecuzione asincrona delle funzioni ODBC, in cui le funzioni ODBC applicabili sono tutti sincrona o asincrona tutte in una determinata connessione.|  
|103|Utilizzare i cursori scorrevoli e in tal modo ottenere accesso a un set di risultati nei metodi diverso forward-only chiamando **SQLFetchScroll** con il *FetchOrientation* argomento diverso da SQL_FETCH_NEXT. (Il SQL_FETCH_BOOKMARK *FetchOrientation* è in funzione 204 [la conformità a livello 2 interfaccia](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Ottenere le chiavi primarie delle tabelle, chiamando **SQLPrimaryKeys**.|  
|105|Utilizzare le stored procedure, tramite la sequenza di escape ODBC per le chiamate di procedure e il dizionario dei dati sulla stored procedure, eseguire una query chiamando **SQLProcedureColumns** e **SQLProcedures**. (Il processo mediante il quale le procedure vengono create e archiviate nell'origine dati è esterno all'ambito di questo documento).|  
|106|Connettersi a un'origine dati passando in modo interattivo i server disponibili, chiamando **SQLBrowseConnect**.|  
|107|Utilizzare le funzioni ODBC anziché istruzioni SQL per eseguire determinate operazioni di database: **SQLSetPos** con SQL_POSITION e SQL_REFRESH.|  
|108|Accedere al contenuto di più set di risultati generati dal batch e stored procedure, chiamando **SQLMoreResults**.|  
|109|Delimitare transazioni che interessano diverse funzioni ODBC, con l'atomicità true e la possibilità di specificare SQL_ROLLBACK in **SQLEndTran**.|
