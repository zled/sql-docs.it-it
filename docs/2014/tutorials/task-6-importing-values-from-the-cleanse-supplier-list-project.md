---
title: 'Attività 6: Importazione di valori dal progetto Cleanse Supplier List | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fec0deef-a729-4ff1-b709-72d2b3f407ac
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7a915013d779392d585bd5609384fab7bffd2800
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063951"
---
# <a name="task-6-importing-values-from-the-cleanse-supplier-list-project"></a>Attività 6: Importazione di valori dal progetto Cleanse Supplier List
  In questa attività vengono importate le informazioni sulla qualità dei dati raccolte durante il processo di pulizia. Vedere [importazione di pulizia dei valori di un progetto in un dominio](http://msdn.microsoft.com/library/hh479581.aspx) per altre informazioni. Anche esportata la knowledge base in un file DQS prima di pubblicare aggiornato **Suppliers** della knowledge base.  
  
1.  Nella pagina principale del **Client DQS**, fare clic su **freccia destra** accanto a **Suppliers** sotto **Knowledge Base recenti** e fare clic su **Gestione dominio**.  
  
2.  Fare clic su **Contact Email** nell'elenco di domini e passare per il **i valori di dominio** scheda nel riquadro di destra.  
  
3.  Fare clic su **freccia in giù** accanto al **Importa valori** icona sulla barra degli strumenti fare clic su **Importa valori progetto**.  
  
     ![Progetto importazione valori pulsante della barra degli strumenti](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-01.jpg "pulsante della barra degli strumenti i valori di progetto Importa")  
  
4.  Nel **Importa valori progetto** finestra di dialogo, seleziona il **Cleanse Supplier List** del progetto e fare clic su **OK**.  
  
5.  Si noti che tutti gli indirizzi di posta elettronica vengono importati insieme alle due correzioni apportate durante la pulizia interattiva. Scorrere per visualizzare le due correzioni.  
  
    |valore|Correggi in|  
    |-----------|----------------|  
    |bobby0@adventure-work.com|bobby0@adventure-works.com|  
    |tad0@adventure-work.com|tad0@adventure-works.com|  
  
6.  Ripetere il passaggio precedente per importare i valori di progetto per la **paese** dominio e notare che viene aggiunta una nuova voce per la correzione **United State** al **Italia** (con ' s').  
  
    |valore|Correggi in|  
    |-----------|----------------|  
    |United State|United States|  
  
7.  Per visualizzare i valori di dominio precedenti, deselezionare **Mostra solo nuovi** casella di controllo.  
  
8.  Ripetere il passaggio precedente per importare i valori di progetto per la **Supplier Name** dominio. Per impostazione predefinita, dopo l'importazione, verranno visualizzati solo i nuovi valori. Per visualizzare tutti i valori, deselezionare **Mostra solo nuovi** casella di controllo. È stata arricchita il **Suppliers** knowledge base con le informazioni acquisite dall'attività di pulizia. Maggiore è l'attendibilità della Knowledge Base, migliori sono i risultati della pulizia.  
  
    > [!NOTE]  
    >  Non è possibile importare valori per un dominio composito.  
  
9. Fare clic su **Esporta Knowledge Base** icona sulla barra degli strumenti e quindi fare clic su **Esporta Knowledge Base**.  
  
     ![Menu Esporta Knowledge Base](../../2014/tutorials/media/et-importingvaluesfromthecslistproject-02.jpg "Menu Esporta Knowledge Base")  
  
10. Passare alla cartella dell'esercitazione, digitare **Suppliers. DQS** per il **nome file**, fare clic su **salvare**. È possibile utilizzare questo file DQS per creare una nuova Knowledge Base basandosi su di esso.  
  
11. Fare clic su **OK** per chiudere la **Esporta Knowledge Base-Suppliers** finestra di messaggio.  
  
12. Fare clic su **fine** per completare l'attività.  
  
13. Fare clic su **Pubblica**.  
  
14. Fare clic su **OK** nella finestra di messaggio.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Lezione 3: Corrispondenza dei dati per rimuovere i duplicati dall'elenco fornitori](../../2014/tutorials/lesson-3-matching-data-to-remove-duplicates-from-supplier-list.md)  
  
  