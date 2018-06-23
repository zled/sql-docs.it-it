---
title: Estrarre i file | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d8b36e03ff939cb7ddbc15bdec1d41532a87d9b7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065201"
---
# <a name="check-out-files"></a>Estrazione di file
  Se l'ambiente [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] non è stato configurato per consentire la modifica dei file archiviati, è necessario eseguire l'estrazione di un file prima di poterlo modificare. Quando si estrae un file, una copia della sua versione viene salvata sul disco locale e l'attributo di sola lettura del file viene rimosso.  
  
 È possibile estrarre i file in modalità esclusiva o condivisa. Quando si estrae un file in modalità esclusiva, il file non può essere estratto da altri utenti finché non viene archiviato. Se un file viene estratto in modalità condivisa, può essere estratto e modificato da altri utenti. Al momento dell'archiviazione potrebbe essere quindi necessario unire le versioni create dai diversi utenti.  
  
 Usare la **Estrai** comando per estrarre i file e progetti di controllo del codice sorgente. Quando si utilizza questo comando, vengono estratti anche tutti i file inclusi nella soluzione o nel progetto. L'estrazione di un singolo file di codice sorgente tuttavia non comporta l'estrazione anche del progetto o della soluzione ai quali il file appartiene.  
  
> [!NOTE]  
>  Se il [!INCLUDE[msCoName](../includes/msconame-md.md)] database di Visual SourceSafe per il progetto è configurato per consentire più estrazioni e si desidera estrarre un file in modo esclusivo, è necessario cancellare il **Consenti più estrazioni** opzione il  **Controllare le opzioni avanzate** finestra di dialogo prima dell'estrazione del file. Per rendere effettiva questa impostazione è necessario riavviare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
### <a name="to-check-out-a-file"></a>Per estrarre un file  
  
1.  In Esplora soluzioni selezionare il progetto o il file desiderato.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **Estrai per la modifica**.  
  
3.  Se il **Estrai per la modifica** viene visualizzata la finestra di dialogo, selezionare gli elementi desiderati e scegliere **Estrai**. Se è stata configurata la [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ambiente non venga visualizzata la **Estrai** finestra di dialogo, gli elementi selezionati in Esplora soluzioni e gli elementi figlio potrebbero avere verranno estratti immediatamente.  
  
     **Check-Out**  
     Consente di estrarre tutti gli elementi selezionati.  
  
     **Colonne**  
     Consente di specificare le colonne da visualizzare e il relativo ordine.  
  
     **Commenti**  
     Consente di digitare un commento da associare all'operazione di estrazione.  
  
     **Non visualizzare la finestra Estrai durante l'estrazione di elementi**  
     Consente di impedire la visualizzazione della finestra di dialogo durante le operazioni di estrazione.  
  
     **Visualizzazione semplice**  
     Consente di visualizzare gli elementi che si stanno estraendo in elenchi semplici con la rispettiva connessione del controllo del codice sorgente.  
  
     **Modifica**  
     Consente di modificare un elemento senza estrarlo. Il **modificare** pulsante viene visualizzato solo se hai [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configurato per supportare la modifica dei file archiviati.  
  
     **Nome**  
     Visualizza i nomi degli elementi che è possibile estrarre. Accanto a ogni elemento selezionato è disponibile una casella di controllo. Deselezionare tale casella se non si desidera estrarre l'elemento corrispondente.  
  
     **Opzioni**  
     Consente di visualizzare le opzioni di estrazione specifiche del plug-in del controllo del codice sorgente quando si fa clic sulla freccia a destra del pulsante.  
  
     **Sort**  
     Consente di scegliere l'ordine delle colonne visualizzate.  
  
     **Visualizzazione struttura ad albero**  
     Consente di visualizzare la gerarchia di file e cartelle relativa all'elemento che si desidera estrarre.  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare i file archiviati](../../2014/database-engine/edit-checked-in-files.md)   
 [Estrarre automaticamente i file al momento della modifica](../../2014/database-engine/automatically-check-out-files-upon-edit.md)   
 [Annullamento di estrazioni](../../2014/database-engine/undo-checkouts.md)   
 [Gestione delle estrazioni](../../2014/database-engine/manage-checkouts.md)  
  
  