---
title: Generare Set di metadati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f5de9f9b5b2a6da81fa175f24cd5bdf1b14e6e8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="result-set-metadata"></a>Metadati dei Set di risultati
*Metadati* sono dati che descrivono altri dati. Ad esempio, i metadati dei set di risultati descrive il set di risultati, ad esempio il numero di colonne nel set di risultati, i tipi di dati di tali colonne, i relativi nomi, precisione, ammissione di valori null e così via.  
  
 Applicazioni interoperative devono controllare sempre i metadati delle colonne del set di risultati. I metadati per una colonna in un set di risultati potrebbero essere diversi dai metadati per la colonna, come restituito da una funzione di catalogo. Ad esempio, si supponga che una colonna aggiornabile è incluso in un set di risultati creato unendo in join due tabelle. Mentre **SQLColumnPrivileges** potrebbe indicare che un utente può aggiornare la colonna, i metadati di set di risultati potrebbero non se la colonna è sul lato "molti" del join; molte origini dati possono aggiornare le colonne sul lato "uno" di un join, ma non sul " lato "molti" di ". Non è possibile presupporre anche i tipi di dati siano gli stessi, poiché l'origine dati promuove il tipo di dati durante la creazione di set di risultati.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Quali sono i metadati utilizzati?](../../../odbc/reference/develop-app/how-is-metadata-used.md)  
  
-   [SQLDescribeCol e SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md)

