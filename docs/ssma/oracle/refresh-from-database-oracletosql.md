---
title: Aggiornamento dal Database (OracleToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 84492f44-c368-4c75-954d-7307a2d2bbc0
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 213fe8ba8569c043ca19c6737be8992da79a17de
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777887"
---
# <a name="refresh-from-database-oracletosql"></a>Aggiornamento dal Database (OracleToSQL)
Il **aggiornamento dal Database** la finestra di dialogo consente di selezionare gli oggetti da aggiornare dal database Oracle. Le righe nella finestra di dialogo sono codificate con colori in base allo stato dei metadati:  
  
-   Se i metadati dell'oggetto sono stato modificato in locale e nel database Oracle, la riga è blu.  
  
-   Se i metadati dell'oggetto sono stato modificato nel database Oracle, ma non in SSMA, la riga è gialla.  
  
-   Se i metadati dell'oggetto sono stato modificato in locale, ma non nel database Oracle, la riga è verde.  
  
-   Se l'oggetto è nuovo nel database Oracle, la riga è rosa.  
  
È possibile specificare le impostazioni di aggiornamento oggetto predefinite nel **impostazioni progetto** la finestra di dialogo. Per altre informazioni, vedere [impostazioni del progetto di&#40;sincronizzazione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
Per l'accesso di **aggiornamento dal Database** nella finestra di dialogo scelta di un oggetto in Visualizzatore metadati Oracle e fare clic su **aggiornamento dal Database**.  
  
## <a name="options"></a>Opzioni  
**Comprimi (-)**  
Comprimere tutti i gruppi di oggetti per nascondere singoli oggetti.  
  
**Espansione (+)**  
Espandere tutti i gruppi di oggetti per visualizzare i singoli oggetti.  
  
**Mostra/Nascondi oggetti uguali**  
Nasconde gli oggetti nell'elenco se l'oggetto di metadati sono lo stesso nel database Oracle e in SSMA.  
  
**Aggiornamento dal Database (clic sul pulsante freccia)**  
Utilizzare il pulsante freccia per specificare che i metadati per gli oggetti selezionati devono essere aggiornati in SSMA.  
  
**Eseguire l'operazione non aggiornato dal Database (pulsante) X**  
Utilizzare il pulsante X per specificare che i metadati per gli oggetti selezionati non devono essere aggiornati in SSMA.  
  
**Legenda**  
Consente di visualizzare un **legenda** la finestra di dialogo. La legenda contiene il mapping tra i colori di riga e gli stati di metadati.  
  
Per mantenere il **legenda** la finestra di dialogo in cima il **aggiornamento dal Database** la finestra di dialogo, seleziona il **visualizzare in primo piano** casella di controllo.  
  
