---
title: Istruzione CREATE INDEX | Documenti Microsoft
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
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61d1532e457748b432e5aa14a55e9e68b4486c9c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-index-statement"></a>Istruzione CREATE INDEX
La sintassi dell'istruzione CREATE INDEX è:  
  
 CREATE INDEX [UNIQUE] *-nome dell'indice* via *-nome della tabella* (*colonna identificatore* [ASC] [DESC] [, *colonna identificatore* [ASC][DESC]...]) CON \< *elenco di opzioni di indice*>  
  
 in cui \< *elenco di opzioni di indice*> può essere: primaria &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Solo il driver Microsoft Access utilizza le opzioni di indice DISALLOW NULL e IGNORARE NULL. I driver Paradox e i file dBASE accetta la sintassi, ma ignora la presenza di entrambe le opzioni.  
  
 Quando viene utilizzato il driver Paradox, l'istruzione CREATE INDEX crea file di chiave primari Paradox e file secondari.  
  
 Questa istruzione non è supportata dai driver Microsoft Excel o testo.
