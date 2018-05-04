---
title: Quali sono i metadati utilizzati? | Microsoft Docs
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
- result sets [ODBC], metadata
- metadata [ODBC]
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c4779c5e60b97a389ebf686678c9a989fb933cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="how-is-metadata-used"></a>Quali sono i metadati utilizzati?
Le applicazioni richiedono metadati per la maggior parte delle operazioni sui set di risultati. L'applicazione, ad esempio, utilizza il tipo di dati di una colonna per determinare il tipo di variabile da associare alla colonna. Usa la lunghezza in byte di una colonna di tipo carattere per determinare la quantità di spazio che è necessario visualizzare dati di tale colonna. Il modo in cui un'applicazione determina i metadati per una colonna dipende dal tipo dell'applicazione.  
  
 Le applicazioni verticali utilizzano tabelle predefinite ed eseguono operazioni predefinite in tali tabelle. Poiché i metadati del set di risultati per tali applicazioni sono definito prima che l'applicazione viene scritto anche ed è controllato dallo sviluppatore dell'applicazione, può essere hardcoded nell'applicazione. Se, ad esempio, una colonna di ID ordine viene definita come valore integer a 4 byte nell'origine dati, l'applicazione può sempre associare un valore integer a 4 byte alla colonna. Quando i metadati vengono specificati a livello di codice nell'applicazione, una modifica apportata alle tabelle utilizzate dall'applicazione comporta in genere una modifica al codice dell'applicazione. Ciò costituisce raramente un problema, poiché tali modifiche vengono apportate in genere come parte di una nuova versione dell'applicazione.  
  
 Come le applicazioni verticali, applicazioni personalizzate in genere con le tabelle predefinite ed eseguono operazioni predefinite in tali tabelle. Ad esempio, potrà scrivere un'applicazione per trasferire dati tra tre origini dati diverse. i dati da trasferire sono noto in genere quando l'applicazione viene scritta. Di conseguenza, applicazioni personalizzate anche tendono a livello di codice dei metadati.  
  
 Applicazioni generiche, in particolare quelli che supportano query ad hoc, non conoscere quasi mai i metadati del set di risultati creati. Pertanto, individuano i metadati in fase di esecuzione tramite le funzioni di **SQLNumResultCols**, **SQLDescribeCol**, e **SQLColAttribute**, che sono descritte nel la sezione successiva, [SQLDescribeCol e SQLColAttribute](../../../odbc/reference/develop-app/sqldescribecol-and-sqlcolattribute.md).  
  
 Tutte le applicazioni, indipendentemente dal loro tipo, è possibile codificare i metadati per il set di risultati restituiti dalle funzioni di catalogo. Questi set di risultati sono definiti nella sezione di riferimento di questo manuale.
