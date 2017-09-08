---
title: Aggiornamento dal database (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 59a6db8f-2db6-4071-9005-928a7231de92
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0e4a2afc29ff32b51a38e9df117426585e84e177
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="refresh-from-database-mysqltosql"></a>Aggiornamento dal database (MySQLToSQL)
Il **aggiornamento dal Database** la finestra di dialogo consente di selezionare gli oggetti da aggiornare dal database di MySQL. Le righe nella finestra di dialogo sono codificate con colori in base allo stato dei metadati:  
  
-   Se i metadati dell'oggetto sono stato modificato in locale e nel database di MySQL, la riga blu.  
  
-   Se i metadati dell'oggetto sono stato modificato nel database di MySQL, ma non in SSMA, la riga è gialla.  
  
-   Se i metadati dell'oggetto sono stato modificato in locale, ma non nel database di MySQL, la riga è verde.  
  
-   Se l'oggetto è nuovo nel database di MySQL, la riga è rosa.  
  
È possibile specificare le impostazioni di aggiornamento oggetto predefinite nel **impostazioni progetto** la finestra di dialogo. Per ulteriori informazioni, vedere [impostazioni progetto &#40; Sincronizzazione &#41; &#40; MySQLToSQL &#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md)  
  
Per l'accesso di **aggiornamento dal Database** nella finestra di dialogo scelta di un oggetto in Visualizzatore metadati MySQL e fare clic su **aggiornamento dal Database**.  
  
## <a name="options"></a>Opzioni  
  
|||  
|-|-|  
|**Nome**|**Definizione**|  
|**Compressione (-)**|Comprimere tutti i gruppi di oggetti per nascondere singoli oggetti.|  
|**Espansione (+)**|Espandere tutti i gruppi di oggetti per visualizzare i singoli oggetti.|  
|**Mostra/Nascondi oggetti uguali**|Nasconde gli oggetti nell'elenco se l'oggetto di metadati sono lo stesso del database MySQL in SSMA.|  
|**Aggiornamento dal Database (freccia)**|Utilizzare il pulsante freccia per specificare che i metadati per gli oggetti selezionati devono essere aggiornati in SSMA.|  
|**Eseguire non aggiornato dal Database (pulsante) X**|Utilizzare il pulsante X per specificare che i metadati per gli oggetti selezionati non devono essere aggiornati in SSMA.|  
|**Legenda**|Consente di visualizzare un **legenda** la finestra di dialogo. La legenda contiene il mapping tra i colori di riga e gli stati di metadati.<br /><br />Per mantenere il **legenda** la finestra di dialogo in cima il **aggiornamento dal Database** la finestra di dialogo, seleziona il **visualizzare in primo piano** casella di controllo.|  
  

