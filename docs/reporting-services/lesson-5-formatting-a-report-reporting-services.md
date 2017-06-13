---
title: 'Lezione 5: Formattazione di un Report (Reporting Services) | Documenti Microsoft'
ms.custom: 
ms.date: 05/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
caps.latest.revision: 20
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e168601f761a966d494168cd79d3724fc4342b63
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Lesson 5: Formatting a Report (Reporting Services)
Dopo avere aggiunto un'area dati e alcuni campi al report Sales Orders, è possibile formattare i campi relativi a data e valuta e le intestazioni di colonna.  
  
## <a name="bkmk_format_date"></a>Formattare la data  
Nel campo Date vengono visualizzate la data e l'ora per impostazione predefinita. È possibile formattare tale campo in modo da visualizzare solo la data.  
  
#### <a name="to-format-a-date-field"></a>Per formattare un campo di tipo data  
  
1.  Fare clic sulla scheda **Progettazione** .  
  
2.  Fare clic con il pulsante destro del mouse nella cella contenente l'espressione per il campo `[Date]` e scegliere **Proprietà casella di testo**.  
  
3.  Fare clic su **Numero**, quindi selezionare **Data** nel campo **Categoria**.  
  
4.  Nella casella **Tipo** selezionare **31 Gennaio 2000**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Visualizzare un'anteprima del report per vedere la modifica al campo `[Date]` , quindi tornare alla visualizzazione della struttura.  
  
## <a name="bkmk_format_currency"></a>Formattare la valuta  
Nel campo **LineTotal** viene visualizzato un numero generico. È possibile formattare tale numero come valuta.  
  
#### <a name="to-format-a-currency-field"></a>Per formattare un campo di tipo valuta  
  
1.  Fare clic con il pulsante destro del mouse nella cella contenente l'espressione per il campo `[LineTotal]` e scegliere **Proprietà casella di testo**.  
  
2.  Fare clic su **Numero**, quindi scegliere **Valuta** nel campo **Categoria**.  
  
3.  Se la lingua delle impostazioni locali è l'italiano, le impostazioni predefinite devono essere le seguenti:  
  
    -   **Cifre decimali: 2**  
  
    -   **Numeri negativi: (€12345,00)**  
  
    -   **Simbolo: € italiano**  
  
4.  Selezionare **Usa separatore delle migliaia (,)**.  
  
    Se il testo di esempio è:**$ 12.345,00**, le impostazioni sono corrette.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Visualizzare un'anteprima del report per vedere la modifica al campo `[LineTotal]` , quindi tornare alla visualizzazione della struttura.  
  
## <a name="bkmk_change_textstyle"></a>Modifica dello stile del testo e della larghezza delle colonne  
È possibile modificare anche la formattazione della riga dell'intestazione per differenziarla dalle righe di dati nel report. Come ultima operazione, si potrà regolare la larghezza delle colonne.  
  
#### <a name="to-format-header-rows-and-table-columns"></a>Per formattare le righe di intestazione e le colonne di tabella  
  
1.  Fare clic nella tabella in modo che vengano visualizzati gli handle di colonna e riga sopra e accanto alla tabella. Le barre grigie lungo la parte superiore e laterale della tabella sono gli handle di riga e di colonna.  
       
  
2.  Posizionare il puntatore del mouse sulla riga tra gli handle di colonna in modo che il cursore assuma la forma di una doppia freccia. Trascinare le colonne fino a ottenere le dimensioni desiderate.
 ![rs_BasicTableDetailsDesign](../reporting-services/media/rs-basictabledetailsdesign.png)   
  
3.  Selezionare la riga che contiene le etichette dell'intestazione di colonna e scegliere **Carattere** dal menu **Formato** , quindi fare clic su **Grassetto**.  
  
4.  Per visualizzare un'anteprima del report fare clic sulla scheda **Anteprima** . L'aspetto dell'anteprima dovrebbe essere simile al seguente:  
  
    ![Anteprima della tabella con intestazioni di colonna in grassetto](../reporting-services/media/rs-basictabledetailsformattedpreview.png "anteprima della tabella con intestazioni di colonna in grassetto")  
  
5.  Per salvare il report, scegliere **Salva tutti** nel menu **File** .  
  
## <a name="next-steps"></a>Passaggi successivi  
Sono stati formattati le intestazioni di colonna e i valori di data e valuta. È possibile aggiungere gruppi e totali al report. Vedere [Lezione 6: Aggiunta di gruppi e totali &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
[Formattazione di numeri e date &#40;Generatore report e SSRS&#41;](../reporting-services/report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)  
[Tipi di rendering &#40;Generatore report e SSRS&#41;](../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
  


