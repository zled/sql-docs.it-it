---
title: Spostare o eliminare un elemento (Gestione report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
caps.latest.revision: 44
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: b3b4ede3a29c43cf2c77b61e2fe8fb6fb3b9e6ff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168011"
---
# <a name="move-or-delete-an-item-report-manager"></a>Spostare o eliminare un elemento (Gestione report)
  I report e gli altri elementi relativi ai report pubblicati in un server di report vengono archiviati in cartelle. È possibile spostare gli elementi in una cartella diversa e i riferimenti a tali elementi vengono mantenuti automaticamente dal server di report. Prima di eliminare un elemento, verificare se sono presenti altri elementi che dipendono da esso.  
  
## <a name="move-an-item"></a>Spostare un elemento  
 È possibile spostare gli elementi del server di report in percorsi di cartelle diversi nella gerarchia di cartelle del server di report. Quando si sposta un elemento, tutte le proprietà, incluse le impostazioni di sicurezza, vengono spostate con l'elemento nel nuovo percorso. Quando si sposta una cartella, vengono spostati tutti gli elementi contenuti nella cartella.  
  
 In Gestione report gli elementi che è possibile spostare vengono indicati nella gerarchia di cartelle. Nella tabella seguente sono illustrate le icone di ogni elemento che è possibile spostare.  
  
|Icona|Elemento spostabile|  
|----------|-------------------|  
|![Icona di report](../media/hlp-16doc.gif "Icona di report")|Report|  
|![Icona di report collegato](../media/hlp-16linked.gif "Icona di report collegato")|Report collegato|  
|![Icona di cartella](../media/hlp-16folder.gif "Icona di cartella")|Cartella|  
|![Icona di risorsa generica](../media/hlp-16file.gif "Icona di risorsa generica")|Risorsa generica|  
|![Icona di origine dati condivisa](../media/hlp-16datasource.png "Icona di origine dati condivisa")|Origine dati condivisa|  
||Set di dati condiviso|  
  
 Non tutti gli elementi possono essere spostati. Non è possibile spostare elementi associati a un report, ad esempio le sottoscrizioni o la cronologia del report. Tali elementi si spostano insieme ai report a essi associati. Analogamente, non è possibile spostare elementi disponibili all'esterno della gerarchia di cartelle, ad esempio le pianificazioni condivise. Non è possibile spostare gli elementi se non si dispone delle autorizzazioni appropriate. L'autorizzazione per lo spostamento di un elemento viene concessa a un utente selezionando le attività seguenti nell'assegnazione di ruolo dell'utente per l'elemento specifico: "Gestione di report", "Gestione modelli", "Gestione di cartelle" e "Gestione di origini dei dati".  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a>Per spostare un elemento dalla pagina Contenuto  
  
1.  Avviare [gestione Report &#40;modalità nativa SSRS&#41;]... / report-manager-ssrs-nativo-mode.md).  
  
2.  In Gestione report passare alla pagina **Contenuto** e individuare l'elemento da spostare.  
  
3.  Posizionare il puntatore del mouse sull'elemento, quindi fare clic sulla freccia a discesa.  
  
4.  Nel menu a discesa fare clic su **Sposta**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  In **Percorso**specificare la cartella in cui si vuole spostare l'elemento. È possibile digitare il nome completo della cartella oppure utilizzare il controllo dell'albero per passare alla cartella desiderata.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 In alternativa, è possibile passare all'oggetto da spostare, fare clic su **Proprietà**e quindi su **Sposta** nella parte superiore della pagina.  
  
## <a name="delete-an-item"></a>Eliminare un elemento  
 Prima di eliminare un elemento, determinare se è utilizzato da altri elementi. Se ad esempio si elimina un'origine dati condivisa, i report e i modelli che la utilizzano non verranno più eseguiti. Quando si elimina un report, vengono eliminate anche la cronologia del report e le sottoscrizioni associate. Per trovare elementi dipendenti per un elemento, vedere [pagina elementi dipendenti &#40;gestione Report&#41;]... / dipendente-elementi-pagina-report-manager.md).  
  
#### <a name="to-delete-a-report-or-item"></a>Per eliminare un report o un elemento  
  
1.  Avviare [gestione Report &#40;modalità nativa SSRS&#41;]... / report-manager-ssrs-nativo-mode.md).  
  
2.  In Gestione report passare alla pagina **Contenuto** e quindi individuare l'elemento da eliminare.  
  
3.  Posizionare il puntatore del mouse sull'elemento, quindi fare clic sulla freccia a discesa.  
  
4.  Scegliere **Elimina**dal menu a discesa.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Pagina di contenuto &#40;gestione Report&#41;]... / contenuto-pagina-report-manager.md)   
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report e SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  