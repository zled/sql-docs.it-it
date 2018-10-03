---
title: Cursori scorrevoli e isolamento delle transazioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5510eb58315f70195eb40390edec1766c350fb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662349"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Cursori scorrevoli e isolamento delle transazioni
Nella tabella seguente elenca i fattori che controllano la visibilità delle modifiche.  
  
|Modifiche apportate da:|Visibilità dipende da:|  
|----------------------|----------------------------|  
|Cursore|Tipo di cursore, implementazione dei cursori|  
|Altre istruzioni nella stessa transazione|Tipo di cursore|  
|Istruzioni in altre transazioni|Tipo di cursore, a livello di isolamento delle transazioni|  
  
 Questi fattori vengono visualizzati nella figura seguente.  
  
 ![Fattori che controllano la visibilità delle modifiche](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 La tabella seguente riepiloga la capacità di ogni tipo di cursore di rilevare le modifiche apportate da solo da altre operazioni nella propria transazione e da altre transazioni. La visibilità delle modifiche quest'ultime varia a seconda del tipo di cursore e il livello di isolamento della transazione contenente il cursore.  
  
|Cursore type\action|self|Il proprietario<br /><br /> TXN|Assumere<br /><br /> TXN<br /><br /> (RU[a])|Assumere<br /><br /> TXN<br /><br /> (RC[a])|Assumere<br /><br /> TXN<br /><br /> (RR[a])|Assumere<br /><br /> TXN<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statico|||||||  
|Insert|Forse [b]|no|no|no|no|no|  
|Update|Forse [b]|no|no|no|no|no|  
|DELETE|Forse [b]|no|no|no|no|no|  
|Gestito da keyset|||||||  
|Insert|Forse [b]|no|no|no|no|no|  
|Update|Sì|Sì|Sì|Sì|no|no|  
|DELETE|Forse [b]|Sì|Sì|Sì|no|no|  
|Dynamic|||||||  
|Insert|Sì|Sì|Sì|Sì|Sì|no|  
|Update|Sì|Sì|Sì|Sì|no|no|  
|DELETE|Sì|Sì|Sì|Sì|no|no|  
  
 [a] le lettere tra parentesi indicano il livello di isolamento della transazione contenente il cursore. il livello di isolamento della transazione (in cui è stata effettuata la modifica) non è rilevante.  
  
 RU: Read uncommitted  
  
 RC: Read commit  
  
 RR: Lettura ripetibile  
  
 S: serializzabile  
  
 [b] dipende dal modo in cui il cursore viene implementato. Indica se il cursore è possibile rilevare tali modifiche viene segnalato tramite l'opzione SQL_STATIC_SENSITIVITY **SQLGetInfo**.
