---
title: 'Attività 9: Creazione di una gerarchia derivata mediante gestione dati Master | Documenti Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 35584d33afac7a2a8f74abd013288a974cade512
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170913"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a>Attività 9: Creazione di una gerarchia derivata mediante Gestione dati master
  In questa attività viene creata una gerarchia derivata mediante Gestione dati master. Questa gerarchia derivata viene ricavata dalle relazioni tra attributi basati su dominio tra il **fornitore** e **stato** entità.  
  
1.  Passare alla pagina principale del **gestione dati Master** facendo clic su **SQL Server 2012 Master Data Services** nella parte superiore della pagina.  
  
2.  Fare clic su **Amministrazione sistema** nel **le attività amministrative** sezione.  
  
3.  Posizionare il mouse sopra **Manage** sulla barra dei menu, scegliere **gerarchie derivate**.  
  
     ![Menu Gestisci - gerarchie derivate selezionate](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Menu Gestisci - gerarchie derivate selezionate")  
  
4.  Fare clic su **Aggiungi gerarchia derivata (+)** pulsante sulla barra degli strumenti.  
  
     ![Pulsante Aggiungi gerarchia derivata](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "pulsante Aggiungi gerarchia derivata")  
  
5.  Tipo di **SuppliersInState** per il **nome gerarchia derivata**.  
  
6.  Fare clic su **salvare** pulsante sulla barra degli strumenti.  
  
     ![Salva derivato pulsante gerarchia](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Salva derivato pulsante gerarchia")  
  
7.  Trascinare **fornitore** da **livelli disponibili: SuppliersInState** al **livelli correnti: SuppliersInState**.  
  
     ![Entità e gerarchie al livello corrente disponibili](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "entità e gerarchie al livello corrente disponibili")  
  
8.  Trascinare **stato** da **livelli disponibili: SuppliersInState** al **livelli correnti: SuppliersInState**. Nella schermata deve essere **livelli correnti** come illustrato nell'immagine seguente.  
  
     ![Livelli correnti e anteprima della gerarchia derivata](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "livelli correnti e anteprima della gerarchia derivata")  
  
9. Nel **anteprima** finestra, espandere **NY {New York}** dovrebbe essere possibile visualizzare un fornitore di quello stato come illustrato nella figura precedente.  
  
10. Passare alla pagina principale del **gestione dati Master** facendo clic su **SQL Server 2012 Master Data Services** nella parte superiore della pagina.  
  
11. Fare clic su **Esplora**.  
  
12. Posizionare il mouse sopra **gerarchie** e fare clic su **Derived: SuppliersInState**.  
  
     ![Gerarchie - derivate: Menu SuppliersInState](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "- gerarchie derivate: SuppliersInState Menu")  
  
13. Fare clic su un **stato** nodo il **visualizzazione ad albero** dovrebbe essere possibile visualizzare i fornitori dello stato nel riquadro di destra.  
  
     ![In Esplora gerarchia derivata](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "in Esplora gerarchia derivata")  
  
## <a name="next-step"></a>Passaggio successivo  
 [Lezione 5: Automatizzazione della pulizia e corrispondenza tramite SSIS](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  