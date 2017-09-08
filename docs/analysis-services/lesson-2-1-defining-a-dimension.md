---
title: Definizione di una dimensione | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6969c73bc6f466eb1a2acfd9d41ff21e80d727c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-1---defining-a-dimension"></a>Lezione 2-1-definizione di una dimensione
Nell'attività seguente si utilizzerà la Creazione guidata dimensione per compilare una dimensione Date.  
  
> [!NOTE]  
> Per questa lezione è necessario aver completato tutte le procedure nella lezione 1.  
  
### <a name="to-define-a-dimension"></a>Per definire una dimensione  
  
1.  In Esplora soluzioni, a destra di Microsoft Visual Studio, fare clic con il pulsante destro del mouse su **Dimensioni**e scegliere **Nuova dimensione**. Verrà visualizzata la Creazione guidata dimensione.  
  
2.  Nella pagina iniziale di **Creazione guidata dimensione** fare clic su **Avanti**.  
  
3.  Nella pagina **Selezione metodo di creazione** verificare che la pagina **Usa una tabella esistente** sia selezionata e fare clic su **Avanti**.  
  
4.  Nella pagina **Impostazione informazioni origine** verificare che sia selezionata la vista origine dati **Adventure Works DW 2012** .  
  
5.  Nell'elenco **Tabella principale** selezionare **Data**.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella pagina **Selezione attributi dimensione** selezionare le caselle di controllo accanto agli attributi seguenti:  
  
    -   **Date Key**  
  
    -   **Full Date Alternate Key**  
  
    -   **English Month Name**  
  
    -   **Calendar Quarter**  
  
    -   **Calendar Year**  
  
    -   **Calendar Semester**  
  
8.  Modificare l'impostazione della colonna **Tipo attributo** per l'attributo **Full Date Alternate Key** da **Regolare** a **Data**. A tale scopo, fare clic su **Regolare** nella colonna **Tipo attributo** . Fare quindi clic sulla freccia per espandere le opzioni. Fare poi clic su **Data** > **Calendario** > **Data**. Scegliere **OK**. Ripetere questi passaggi per modificare il tipo di attributo per gli attributi seguenti:  
  
    -   **English Month Name** in **Mese**  
  
    -   **Calendar Quarter** in **Trimestre**  
  
    -   **Calendar Year** in **Anno**  
  
    -   **Calendar Semester** in **Semestre**  
  
9. Scegliere **Avanti**.  
  
10. Nel riquadro Anteprima della pagina **Completamento procedura guidata** è possibile visualizzare la dimensione **Date** e i relativi attributi.  
  
11. Fare clic su **Fine** per completare la procedura guidata.  
  
    In Esplora soluzioni nel progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial la dimensione Date viene visualizzata nella cartella **Dimensioni** . Al centro dell'ambiente di sviluppo, in Progettazione dimensioni viene visualizzata la dimensione Date.  
  
12. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Definizione di un cubo](../analysis-services/lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a>Vedere anche  
[Dimensioni nei modelli multidimensionali](../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)  
[Creare una dimensione utilizzando una tabella esistente](../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)  
[Creare una dimensione utilizzando la Creazione guidata dimensione](../analysis-services/multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
  

