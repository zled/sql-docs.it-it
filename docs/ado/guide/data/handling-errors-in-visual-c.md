---
title: Gestione degli errori in Visual C++ | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68ce5fb8cc94b130de5171a45b65743e86eec3da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271690"
---
# <a name="handling-errors-in-visual-c"></a>Gestione degli errori in Visual C++
In COM, la maggior parte delle operazioni restituisce un codice restituito HRESULT che indica se una funzione è stata completata correttamente. La direttiva #import genera codice wrapper per ogni proprietà o il metodo "non elaborato" e verifica il valore HRESULT restituito. Se il valore HRESULT indica un errore, il codice wrapper genera un errore COM come argomento dal chiamante com_issue_errorex () con il codice restituito HRESULT. Oggetti di errore COM possono essere intercettati in un **try-catch** blocco. (Per i migliori risultati ottenere, intercettare un riferimento a un oggetto com_error).  
  
 Tenere presente che questi sono errori ADO: sono il risultato di errore in un'operazione di ADO. Gli errori restituiti dal provider sottostante vengono visualizzati come **errore** gli oggetti di **connessione** dell'oggetto **errori** insieme.  
  
 La direttiva #import crea solo la routine di gestione degli errori per i metodi e le proprietà dichiarate nella DLL di ADO. Tuttavia, è possibile sfruttare lo stesso meccanismo di gestione degli errori scrivendo una funzione di macro o inline errori. Vedere l'argomento le estensioni di Visual C++® per alcuni esempi.
