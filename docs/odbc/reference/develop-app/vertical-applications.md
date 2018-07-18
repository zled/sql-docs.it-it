---
title: Le applicazioni verticali | Documenti Microsoft
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
- interoperability [ODBC], vertical applications
- vertical applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f71f960043a843c2aad5f7e3a7eb5cc997b0a6ed
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="vertical-applications"></a>Applicazioni verticali
Le applicazioni verticali in genere un'attività ben definito in un singolo DBMS. Ad esempio, un'applicazione di immissione ordini tiene traccia gli ordini di una società. Ciò che questi tipi di applicazioni hanno in comune è che lo schema del database è in genere progettato dallo sviluppatore dell'applicazione e, se l'applicazione potrebbe funzionare con un numero di diversi DBMS, funziona con un singolo DBMS per un singolo cliente.  
  
 Poiché le applicazioni verticali in genere richiedono determinate funzionalità, ad esempio i cursori scorrevoli o le transazioni, raramente supportano tutti i DBMS. In alternativa, tendono a essere estremamente interoperativi tra un set limitato di DBMS. In genere, gli sviluppatori di applicazioni verticali scelgono di supportare tali DBMS che rappresentano una frazione di grandi dimensioni di mercato e ignorare il resto. Possono anche scegliere di supporto specifici driver per tali DBMS per ridurre i test e i costi di supporto del prodotto.  
  
 Poiché le applicazioni verticali possono supportare un set noto di DBMS, talvolta contengono codice specifico del driver o specifici del DBMS. Tale codice, tuttavia, è preferibile mantenere al minimo, perché richiede più tempo per gestire.
