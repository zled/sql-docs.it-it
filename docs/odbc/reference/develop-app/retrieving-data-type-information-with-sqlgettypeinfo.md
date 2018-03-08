---
title: Il recupero di dati digitare le informazioni con SQLGetTypeInfo | Documenti Microsoft
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
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3ae7606967ce0f77fea638a69a8b44f0e175a48
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Durante il recupero delle informazioni sul tipo di dati con SQLGetTypeInfo
Poiché i mapping dai tipi di dati SQL sottostanti per gli identificatori di tipo ODBC sono approssimativi, ODBC fornisce una funzione (**SQLGetTypeInfo**) tramite un driver possibili completamente descrivere ogni tipo di dati SQL nell'origine dati. Questa funzione restituisce un set di risultati, ogni riga di cui vengono descritte le caratteristiche di un tipo di dati singolo, ad esempio nome, tipo identificatore, precisione, scala e supporto di valori null.  
  
 In genere, queste informazioni vengono utilizzate dalle applicazioni generiche che consentono all'utente di creare e modificare le tabelle. Chiamata di questo tipo applicazioni **SQLGetTypeInfo** per recuperare le informazioni sul tipo di dati e quindi presenta alcuni o tutti i relativi all'utente. Tali applicazioni è necessario essere a conoscenza delle seguenti operazioni:  
  
-   Più di un tipo di dati SQL è possibile eseguire il mapping a un identificatore di tipo singolo, che può rendere difficile determinare il tipo di dati da utilizzare. Per risolvere questo problema, il set di risultati viene ordinato prima dall'identificatore di tipo e la seconda dal livello alla definizione dell'identificatore di tipo. Inoltre, i tipi di dati definito dall'origine dati hanno la precedenza su tipi di dati definito dall'utente. Ad esempio, si supponga che un'origine dati definisce i tipi di dati INTEGER e contatore in base ad eccezione del fatto che i CONTATORI è a incremento automatico. Si supponga inoltre che il tipo definito dall'utente WHOLENUM è un sinonimo dell'intero. Ognuno di questi tipi viene eseguito il mapping a SQL_INTEGER. Nel **SQLGetTypeInfo** set di risultati, numero intero viene visualizzata in primo luogo, seguito da WHOLENUM e quindi del contatore. WHOLENUM viene visualizzato dopo l'intero perché è definito dall'utente, ma prima di contatore perché è più possibile corrispondente la definizione del SQL_INTEGER tipo identificatore.  
  
-   ODBC non definisce i nomi dei tipi di dati per l'utilizzo in **CREATE TABLE** e **ALTER TABLE** istruzioni. Al contrario, l'applicazione deve utilizzare il nome restituito nella colonna TYPE_NAME del set di risultati restituito da **SQLGetTypeInfo**. Il motivo è che sebbene la maggior parte di SQL non variare molto tra DBMS, nomi dei tipi di dati variare notevolmente. Anziché forzare il driver per analizzare le istruzioni SQL e sostituire i nomi dei tipi di dati standard con nomi di tipi di dati specifici del DBMS, ODBC richiede alle applicazioni di utilizzare i nomi specifici del DBMS in primo luogo.  
  
 Si noti che **SQLGetTypeInfo** non necessariamente descritti tutti i tipi di dati può verificarsi un'applicazione. In particolare, i set di risultati potrebbero contenere tipi di dati non direttamente supportati dall'origine dati. Questi tipi di dati potrebbero non essere supportati dall'origine dati, ad esempio, sono definiti i tipi di dati delle colonne nel set di risultati restituiti dalle funzioni di catalogo da ODBC. Per determinare le caratteristiche dei tipi di dati in un set di risultati, un'applicazione chiama **SQLColAttribute**.
