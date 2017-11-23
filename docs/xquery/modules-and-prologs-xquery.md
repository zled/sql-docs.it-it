---
title: Moduli e prologhi (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea78f908b07308be5267522d84ca26003665487a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="modules-and-prologs-xquery"></a>Moduli e prologhi (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [Prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md) è una serie di dichiarazioni dello spazio dei nomi. Se si dichiara lo spazio dei nomi nel prologo, è possibile specificare l'associazione di un prefisso a uno spazio dei nomi e utilizzare il prefisso nel corpo della query.  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Le specifiche di XQuery seguenti non sono supportate in questa implementazione:  
  
-   Dichiarazione del modulo (`version`)  
  
-   Dichiarazione del modulo (`module namespace`)  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   Dichiarazione delle regole di confronto predefinite (`declare default collation`)  
  
-   Dichiarazione dell'URI di base (`declare base-uri`)  
  
-   Dichiarazione della costruzione (`declare construction`)  
  
-   Dichiarazione dell'ordinamento predefinito (`declare ordering`)  
  
-   Importazione di schema (`import schema namespace`)  
  
-   Importazione di modulo (`import module`)  
  
-   Dichiarazione di variabile nel prologo (`declare variable`)  
  
-   Dichiarazione di funzione (`declare function`)  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md)  
 Descrive il prologo di una query XQuery.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
