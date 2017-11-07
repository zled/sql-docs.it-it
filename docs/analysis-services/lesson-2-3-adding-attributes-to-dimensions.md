---
title: Aggiunta di attributi alle dimensioni | Documenti Microsoft
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
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0642ac7688f86ce5fb23f1af50e9ced776993216
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-3---adding-attributes-to-dimensions"></a>Lezione 2-3-aggiunta di attributi alle dimensioni
Dopo avere definito le dimensioni, è possibile popolarle con gli attributi che rappresentano ogni elemento dati nella dimensione. Gli attributi si basano in genere sui campi di una vista origine dati. Quando si aggiungono gli attributi a una dimensione, è possibile includere campi di qualsiasi tabella nella vista origine dati.  
  
In questa attività verrà utilizzato Progettazione dimensioni per aggiungere attributi alle dimensioni Customer e Product. La dimensione Customer includerà gli attributi basati sui campi delle tabelle Customer e Geography.  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>Aggiunta di attributi alla dimensione Customer  
  
#### <a name="to-add-attributes"></a>Per aggiungere attributi  
  
1.  Aprire Progettazione dimensioni per la dimensione Customer. A tale scopo, fare doppio clic sulla dimensione **Customer** nel nodo **Dimensioni** di Esplora soluzioni.  
  
2.  Nel riquadro **Attributi** si notino gli attributi Customer Key e Geography Key creati con la Creazione guidata cubo.  
  
3.  Sulla barra degli strumenti della scheda **Struttura dimensione** verificare che l'icona Zoom per la visualizzazione delle tabelle nel riquadro **Vista origine dati** sia impostata su 100%.  
  
4.  Trascinare le colonne seguenti dalla tabella **Customer** nel riquadro **Vista origine dati** al riquadro **Attributi** :  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **Gender**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Phone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  Trascinare le colonne seguenti dalla tabella **Geography** nel riquadro **Vista origine dati** al riquadro **Attributi** :  
  
    -   **City**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  Scegliere **Salva tutti**dal menu File.  
  
## <a name="adding-attributes-to-the-product-dimension"></a>Aggiunta di attributi alla dimensione Product  
  
#### <a name="to-add-attributes"></a>Per aggiungere attributi  
  
1.  Aprire Progettazione dimensioni per la dimensione Product. Fare doppio clic sulla dimensione **Product** in Esplora soluzioni.  
  
2.  Nel riquadro **Attributi** si noti l'attributo Product Key creato con la Creazione guidata cubo.  
  
3.  Sulla barra degli strumenti della scheda **Struttura dimensione** verificare che l'icona Zoom per la visualizzazione delle tabelle nel riquadro **Vista origine dati** sia impostata su 100%.  
  
4.  Trascinare le colonne seguenti dalla tabella **Product** nel riquadro **Vista origine dati** al riquadro **Attributi** :  
  
    -   **StandardCost**  
  
    -   **Colore**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **Dimensione**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **Classe**  
  
    -   **Stile**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **Stato**  
  
5.  Scegliere **Salva tutti**dal menu File.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Esame delle proprietà del cubo e delle dimensioni](../analysis-services/lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento alle proprietà degli attributi delle dimensioni](../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
  

