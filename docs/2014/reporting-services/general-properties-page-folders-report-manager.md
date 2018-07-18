---
title: Pagina delle proprietà generale, cartelle (gestione Report) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31d99d9b-2303-4bae-9466-fb67b97cf11a
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 69330b9a1a65ed147d716d47d9a2cc68e34bab6b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065537"
---
# <a name="general-properties-page-folders-report-manager"></a>Pagina delle proprietà Generale, Cartelle (Gestione report)
  La pagina delle proprietà Generale per le cartelle consente di visualizzare e impostare le proprietà per le cartelle create. Nella pagina delle proprietà Generale vengono visualizzati il nome dell'utente che ha creato o modificato la cartella e la data e ora di creazione o modifica.  
  
 Le proprietà delle cartelle includono inoltre le impostazioni di sicurezza. Per ulteriori informazioni sulla sicurezza delle cartelle, vedere [proteggere cartelle](security/secure-folders.md).  
  
 Le cartelle speciali, ad esempio Home, Report personali e Cartelle utenti, non possono essere rinominate o spostate nello spazio dei nomi del server di report. Per queste cartelle non è disponibile la pagina delle proprietà Generale.  
  
## <a name="navigation"></a>Navigazione  
 Utilizzare la procedura riportata di seguito per navigare fino a questo percorso nell'interfaccia utente.  
  
###### <a name="to-open-the-general-properties-page-for-a-folder"></a>Per aprire la pagina delle proprietà Generale per una cartella  
  
1.  Aprire Gestione report, quindi aprire la cartella per la quale si desidera visualizzare o configurare le proprietà.  
  
2.  Nell'intestazione della cartella, nella barra degli strumenti, fare clic su **Impostazioni cartella**.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Digitare un nome per la cartella. Il nome deve includere almeno un carattere alfanumerico. È inoltre possibile utilizzare spazi e alcuni simboli. Non utilizzare i caratteri ; ? : @ & = +, $ * \< > | "o / quando si specifica un nome.  
  
 **Descrizione**  
 Consente di digitare una descrizione del contenuto della cartella. Questa descrizione viene visualizzata nella pagina Contenuto per gli utenti autorizzati ad accedere alla cartella.  
  
 **Nascondi in visualizzazione elenco**  
 Selezionare questa opzione per fare in modo che la cartella non venga visualizzata per gli utenti che utilizzano la modalità di visualizzazione Elenco in Gestione report. La modalità di visualizzazione Elenco è il formato di visualizzazione predefinito utilizzato per l'esplorazione della gerarchia di cartelle del server di report. Nella visualizzazione Elenco i nomi e le descrizioni degli elementi vengono disposti dall'alto in basso nella pagina. Il formato alternativo è costituito dalla visualizzazione Dettagli, in cui non sono incluse le descrizioni ma sono disponibili altre informazioni sugli elementi. Gli elementi possono essere nascosti nella visualizzazione Elenco ma non nella visualizzazione Dettagli. Se si desidera limitare l'accesso a un elemento, è necessario creare un'assegnazione di ruolo.  
  
 **Applica**  
 Fare clic per salvare le modifiche.  
  
 **Elimina**  
 Fare clic per rimuovere la cartella e il relativo contenuto.  
  
 **Sposta**  
 Fare clic per spostare un report o una cartella all'interno dello spazio dei nomi del server di report. Verrà visualizzata la pagina di spostamento degli elementi, che consente di esplorare le cartelle per selezionare un nuovo percorso.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione report &#40;modalità nativa SSRS&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Guida F1 di gestione report](../../2014/reporting-services/report-manager-f1-help.md)  
  
  