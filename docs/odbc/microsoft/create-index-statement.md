---
title: Istruzione CREATE INDEX | Documenti Microsoft
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
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f6e7525059640e7ffdadd79ec26a62229eabae9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="create-index-statement"></a>Istruzione CREATE INDEX
La sintassi dell'istruzione CREATE INDEX è:  
  
 CREATE INDEX [UNIQUE] *nome indice* ON *-nome della tabella* (*colonna identificatore* [ASC] [DESC] [, *colonna identificatore* [ASC][DESC]...]) CON \< *elenco di opzioni di indice*>  
  
 dove \< *elenco di opzioni di indice*> può essere: primario &#124; Non consentire NULL &#124; IGNORA NULL  
  
 Solo il driver Microsoft Access utilizza le opzioni di indice DISALLOW NULL e IGNORARE NULL. I driver Paradox e i file dBASE accetta la sintassi, ma ignora la presenza di entrambe le opzioni.  
  
 Quando viene utilizzato il driver Paradox, l'istruzione CREATE INDEX crea file di chiave primari Paradox e file secondari.  
  
 Questa istruzione non è supportata dai driver Microsoft Excel o testo.
