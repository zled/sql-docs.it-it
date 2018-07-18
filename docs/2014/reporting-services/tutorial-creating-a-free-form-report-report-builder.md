---
title: 'Esercitazione: Creazione di un report in formato libero (Generatore report) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
caps.latest.revision: 15
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: fe42fc3dd5e1398cc0e66ad2c37cd14a3fedd67a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202811"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a>Esercitazione: Creazione di un report in formato libero (Generatore report)
  In questa esercitazione viene illustrato come creare un report in formato libero di SSRS che sia simile a una lettera tipo. È possibile disporre gli elementi dei report in modo da creare un form, con caselle di testo, immagini e altre aree dati.  
  
 Il report creato in questa esercitazione si basa su dati di vendita di esempio inclusi nell'esercitazione. Nel report le informazioni vengono raggruppate per territorio e vengono visualizzati il nome del responsabile vendite del territorio e informazioni dettagliate e riepilogative relative alle vendite. Come base per il report in formato libero si utilizzerà l'area dati elenco e si aggiungerà quindi un pannello decorativo con un'immagine, testo statico contenente dati, una tabella per la visualizzazione di informazioni dettagliate e facoltativamente grafici a torta e istogrammi per la visualizzazione di informazioni di riepilogo.  
  
##  <a name="BackToTop"></a> Lezioni dell'esercitazione  
 In questa esercitazione verranno illustrate le operazioni seguenti:  
  
-   [Creare un Report vuoto, l'origine dati e set di dati](#BlankReport)  
  
-   [Aggiungere e configurare un elenco](#List)  
  
-   [Aggiungere elementi grafici](#Graphics)  
  
-   [Aggiungere testo in formato libero](#Text)  
  
-   [Aggiungere una tabella per visualizzare i dettagli](#Table)  
  
-   [Formattare i dati](#Format)  
  
-   [Salvare il Report](#Save)  
  
### <a name="other-optional-steps"></a>Altri passaggi facoltativi  
  
-   [Aggiungere una linea per separare le aree del Report](#Line)  
  
-   [Aggiungere una visualizzazione dei dati di riepilogo](#Visualization)  
  
 Il tempo stimato per il completare l'esercitazione è di 20 minuti.  
  
## <a name="requirements"></a>Requisiti  
 Per altre informazioni sui requisiti, vedere [Prerequisiti per le esercitazioni &#40;Generatore report&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="BlankReport"></a> 1. Creare un report vuoto, un'origine dati e un set di dati  
  
> [!NOTE]  
>  Per evitare che nel report sia necessaria un'origine dati esterna, nella query di questa esercitazione sono inclusi i valori dei dati. L'uso di questo tipo di dati interni è molto utile ai fini dell'apprendimento, ma tale approccio rende la query piuttosto lunga. ,  
  
#### <a name="to-create-a-blank-report"></a>Per creare un report vuoto  
  
1.  Fare clic sul menu **Start**, scegliere **Programmi**, **Generatore report per Microsoft SQL Server 2012**e quindi fare clic su **Generatore report**.  
  
    > [!NOTE]  
    >  Verrà visualizzata la finestra di dialogo **Riquadro attività iniziale** . In caso contrario, fare clic sul pulsante Generatore report, quindi su **Nuovo**.  
  
2.  Nel riquadro sinistro della finestra di dialogo **Riquadro attività iniziale** verificare che l'opzione **Nuovo report** sia selezionata.  
  
3.  Nel riquadro destro fare clic su **Report vuoto**.  
  
#### <a name="to-create-a-new-data-source"></a>Per creare una nuova origine dati  
  
1.  Nel riquadro dei dati del report fare clic su **Nuova**, quindi su **Origine dati**.  
  
2.  Nel `Name` , digitare: **ListDataSource**  
  
3.  Fare clic su **Usa una connessione incorporata nel report**.  
  
4.  Verificare che il tipo di connessione sia Microsoft SQL Server, quindi nella casella **Stringa di connessione** digitare **Origine dati = \<nomeserver>**  
  
     \<NomeServer >, ad esempio Report001, specifica un computer in cui è installata un'istanza del motore di Database SQL Server. Poiché i dati del report non vengono estratti da un database di SQL Server, non è necessario includere il nome di un database. Per analizzare la query viene utilizzato il database predefinito nel server specificato.  
  
5.  Fare clic su **Credenziali**, quindi immettere le credenziali necessarie per la connessione all'istanza del motore di database di SQL Server.  
  
6.  Fare clic su **OK**.  
  
#### <a name="to-create-a-new-dataset"></a>Per creare un nuovo set di dati  
  
1.  Nel riquadro dei dati del report fare clic su **Nuovo**, quindi su **Set di dati**.  
  
2.  Nel `Name` , digitare: **ListDataset.**  
  
3.  Fare clic su **Utilizzare un set di dati incorporato nel report**, quindi verificare che l'origine dati sia **ListDataSource**.  
  
4.  Verificare che il tipo di query **Testo** sia selezionato, quindi fare clic su **Progettazione query**.  
  
5.  Fare clic su **Modifica come testo**.  
  
6.  Copiare e incollare la query seguente nel relativo riquadro:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
7.  Fare clic su Esegui per eseguire la query.  
  
     I risultati della query corrispondono ai dati disponibili per la visualizzazione nel report.  
  
     ![Progettazione query](../../2014/tutorials/media/tutorial-querydesigner.png "Progettazione query")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="List"></a> 2. Aggiungere e configurare un elenco  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fornisce tre modelli di area dati, ovvero tabella, matrice ed elenco. Questi modelli sono tutti basati su un area dati Tablix.  
  
 In questa esercitazione si userà un elenco per visualizzare le informazioni sulle vendite per i territori di vendita in un report simile a un notiziario. Le informazioni vengono raggruppate per territorio. Si aggiungerà un nuovo gruppo di righe per il raggruppamento dei dati per territorio e si eliminerà quindi il gruppo di righe Dettagli incorporato. Il modello di elenco è ideale per la creazione di report in formato libero. Per altre informazioni, vedere [sono elencati &#40;Generatore Report e SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Questo report utilizza il formato carta Letter (21,7 X 27,9 cm) e margini di 2,54 cm. Una pagina del report più alta di 9 pollici (23 centimetri) o più larga di 6 1/2 (16,5) centimetri potrebbe determinare la generazione di pagine vuote.  
  
#### <a name="to-add-a-list"></a>Per aggiungere un elenco  
  
1.  Nell'area **Aree dati** della scheda **Inserisci** della barra multifunzione fare clic su **Elenco** , quindi trascinare l'elenco nel corpo del report. Assegnare all'elenco un'altezza di 7 pollici (18 centimetri) e una larghezza di 6,25 pollici (16 centimetri).  
  
2.  Fare clic nell'elenco, fare clic con il pulsante destro del mouse sulla parte superiore dell'elenco, quindi scegliere **Proprietà Tablix**.  
  
     ![Aggiunta dell'elenco](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "aggiunta dell'elenco")  
  
3.  Nell'elenco a discesa **Nome set di dati** selezionare **ListDataset**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  Fare clic con il pulsante destro del mouse nell'elenco, quindi scegliere **Proprietà rettangolo**.  
  
     ![Comando Proprietà rettangolo](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "comando Proprietà rettangolo")  
  
6.  Nella scheda **Generale** selezionare la casella di controllo **Aggiungi un'interruzione di pagina dopo** .  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a>Per aggiungere un nuovo gruppo di righe ed eliminare il gruppo Dettagli  
  
1.  Nel riquadro Gruppi di righe fare clic con il pulsante destro del mouse sul gruppo Dettagli, scegliere **Aggiungi gruppo**, quindi fare clic su **Gruppo padre**.  
  
     ![Comando gruppo padre](../../2014/tutorials/media/tutorial-parentgroupcommand.png "comando gruppo padre")  
  
2.  Nell'elenco a discesa selezionare `[Territory].`  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     All'elenco verrà aggiunta una colonna. La colonna contiene la cella `[Territory].`  
  
4.  Fare clic con il pulsante destro del mouse sulla colonna Territory, quindi scegliere **Elimina colonne**.  
  
     ![Elimina colonne](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Elimina colonne")  
  
5.  Fare clic su **Elimina solo colonne**.  
  
     ![Dialogo Elimina colonne](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "nella finestra di dialogo Elimina colonne")  
  
6.  Nel riquadro Gruppi di righe fare clic con il pulsante destro del mouse sul gruppo **Dettagli** , quindi scegliere **Elimina gruppo**.  
  
     ![Elimina gruppo di dettagli](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Elimina gruppo dettagli")  
  
7.  Fare clic su **Elimina solo gruppo**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Graphics"></a> 3. Aggiungere elementi grafici  
 Uno dei vantaggi offerti da un'area dati elenco consiste nella possibilità di aggiungere elementi del report, quali rettangoli e caselle di testo, in qualsiasi posizione, anziché essere limitati a un layout tabulare. L'aggiunta di un elemento grafico, ad esempio un rettangolo colorato, conferirà al report un aspetto più gradevole.  
  
#### <a name="to-add-graphic-elements-to-the-report"></a>Per aggiungere elementi grafici al report  
  
1.  Nel **inserire** della scheda della barra multifunzione, fare clic su **rettangolo**, quindi trascinare un rettangolo nell'angolo in alto a sinistra dell'elenco. Assegnare al rettangolo un'altezza di 7 pollici (18 centimetri) e una larghezza di 1 pollice (2,5 centimetri).  
  
2.  Fare clic con il pulsante destro del mouse sul rettangolo, quindi scegliere **Proprietà rettangolo**.  
  
3.  Fare clic sulla scheda **Riempimento** .  
  
4.  Nell'elenco a discesa **Colore riempimento** fare clic su **Altri colori**, quindi selezionare il colore **GrigioScuro** .  
  
     ![Selezionare il colore di riempimento](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "colore di riempimento selezione")  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Nella parte sinistra del report è ora presente un elemento grafico verticale costituito da un rettangolo di colore grigio scuro.  
  
##  <a name="Text"></a> 4. Aggiungere testo in formato libero  
 Una casella di testo contiene testo statico ripetuto in ogni pagina del report, nonché campi dati.  
  
#### <a name="to-add-text-to-the-report"></a>Per aggiungere testo al report  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nella scheda **Inserisci** della barra multifunzione fare clic su **Casella di testo**, quindi trascinare una casella di testo nell'angolo superiore sinistro dell'elenco all'interno del rettangolo aggiunto in precedenza. Assegnare alla casella di testo un'altezza di 3 pollici (8 centimetri) e una larghezza di 5 pollici (13 centimetri).  
  
3.  Posizionare il cursore nella parte superiore della casella di testo, quindi digitare: **Notiziario per** .  
  
     ![Aggiungere il testo dell'intestazione newsletter](../../2014/tutorials/media/tutorial-newsletterfor.png "Aggiungere il testo dell'intestazione newsletter")  
  
    > [!NOTE]  
    >  Assicurarsi di includere lo spazio aggiuntivo dopo la parola "per". Lo spazio consente di separare il testo dal campo che si aggiungerà nel passaggio successivo.  
  
4.  Trascinare il campo Territory nella casella di testo e posizionarlo dopo il testo digitato nel passaggio 3.  
  
     ![Aggiungi campo Territorial](../../2014/tutorials/media/tutorial-addterritorialfield.png "campo Territorial aggiungere")  
  
5.  Selezionare tutto il testo, fare clic con il pulsante destro del mouse su di esso, quindi scegliere **Proprietà testo**.  
  
6.  Fare clic sulla scheda **Tipo di carattere** .  
  
7.  Nell'elenco **Tipo di carattere** selezionare **Times New Roman**, in **Dimensioni** selezionare **20 pt**e in **Colore** selezionare **Rosso**.  
  
     ![Proprietà testo](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "proprietà testo")  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. Posizionare il cursore sotto il testo digitato nel passaggio 3 e digitare: **Salve** .  
  
    > [!NOTE]  
    >  Assicurarsi di includere lo spazio aggiuntivo dopo la parola "Salve". Lo spazio consente di separare il testo dal campo che si aggiungerà nel passaggio successivo.  
  
10. Trascinare il campo FullName nella casella di testo e posizionarlo dopo il testo digitato nel passaggio 9, quindi digitare una virgola (,).  
  
     ![Aggiungi campo nome completo](../../2014/tutorials/media/tutorial-addfullnamefield.png "aggiungere lo stesso nome")  
  
11. Selezionare il testo aggiunto nei passaggi 9 e 10, fare clic con il pulsante destro del mouse su di esso, quindi scegliere **Proprietà testo**.  
  
12. Fare clic sulla scheda **Tipo di carattere** .  
  
13. Nell'elenco **Tipo di carattere** selezionare **Times New Roman**, in **Dimensioni** selezionare **16 pt**e in **Colore** selezionare **Nero** .  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. Posizionare il cursore sotto il testo aggiunto nei passaggi da 9 a 13, quindi copiare e incollare il testo fittizio seguente:  
  
    ```  
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque.   
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel.   
    ```  
  
16. Selezionare il testo aggiunto nel passaggio 15, fare clic con il pulsante destro del mouse su di esso, quindi scegliere **Proprietà testo**.  
  
17. Fare clic sulla scheda **Tipo di carattere** .  
  
18. Nell'elenco **Tipo di carattere** selezionare **Arial**, in **Dimensioni** selezionare **10 pt**e in **Colore** selezionare **Nero**.  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Aggiungi testo newsletter](../../2014/tutorials/media/tutorial-newslettertext.png "Aggiungi testo newsletter")  
  
20. Posizionare il cursore sotto il testo incollato nel passaggio 15, quindi digitare: **Congratulazioni per le vendite totali di** .  
  
    > [!NOTE]  
    >  Assicurarsi di includere lo spazio aggiuntivo dopo la parola "di". Lo spazio consente di separare il testo dal campo che si aggiungerà nel passaggio successivo.  
  
21. Trascinare il campo Sales nella casella di testo, posizionarlo dopo il testo digitato nel passaggio 20, quindi digitare un punto esclamativo (!).  
  
22. Evidenziare il campo Sales, fare clic sul campo e quindi fare clic su **espressione**.  
  
23. Nella casella dell'espressione modificare l'espressione per includere la funzione Sum nel modo seguente:  
  
    ```  
    =Sum(Fields!Sales.value)  
    ```  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     ![Aggiungere un'espressione al campo sales](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "aggiungere un'espressione al campo sales")  
  
25. Selezionare il testo aggiunto nei passaggi da 20 a 23, fare clic con il pulsante destro del mouse su di esso, quindi scegliere **Proprietà testo**.  
  
26. Fare clic sulla scheda **Tipo di carattere** .  
  
27. Nell'elenco **Tipo di carattere** selezionare **Times New Roman**, in **Dimensioni** selezionare **16 pt**e in **Colore** selezionare **Rosso**.  
  
28. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
29. Selezionare `[Sum(Sales)]` e nel gruppo **Numero** della scheda **Home** fare clic sul pulsante **Valuta** .  
  
     ![Aggiungi simbolo di valuta](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Aggiungi simbolo di valuta")  
  
30. Fare clic con il pulsante destro del mouse sulla casella di testo contenente il testo "Fare clic per aggiungere il titolo", quindi scegliere **Elimina**.  
  
31. Selezionare la casella di riepilogo e spostarla nella parte superiore della pagina utilizzando i tasti di direzione.  
  
32. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Nel report viene visualizzato il testo statico e in ogni pagina del report sono inclusi i dati relativi a un territorio. Le vendite vengono formattate come valuta.  
  
 ![Anteprima della Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "anteprima della Newsletter")  
  
##  <a name="Table"></a> 5. Aggiungere una tabella per la visualizzazione dei dettagli delle vendite  
 Utilizzare la procedura guidata Nuova tabella o matrice per aggiungere una tabella al report in formato libero. Dopo avere completato la procedura guidata, si aggiungerà manualmente una riga per i totali.  
  
#### <a name="to-add-a-table"></a>Per aggiungere una tabella  
  
1.  Nell'area **Aree dati** della scheda **Inserisci** della barra multifunzione fare clic su **Tabella**, quindi su **Creazione guidata tabella**.  
  
2.  Nella pagina Scegliere un set di dati fare clic su **ListDataset**.  
  
3.  Scegliere **Avanti**.  
  
4.  Nella pagina **Disponi campi** trascinare il campo Product da **Campi disponibili** a **Valori**.  
  
5.  Ripetere il passaggio 4 per SalesDate, Quantity e Sales. Posizionare SalesDate sotto Product, Quantity sotto SalesDate e Sales sotto SalesDate.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella pagina **Scegliere il layout** visualizzare il layout della tabella.  
  
     La tabella è molto semplice. È costituita da cinque colonne e non presenta gruppi di righe o colonne. Poiché non dispone di gruppi, le opzioni di layout correlate ai gruppi non sono disponibili. Più avanti nell'esercitazione si aggiornerà manualmente la tabella per includere un totale.  
  
8.  Scegliere **Avanti**.  
  
9. Nel riquadro **Stili** della pagina **Scegliere uno stile** selezionare **Ardesia**.  
  
10. Scegliere **Fine**.  
  
11. Trascinare la tabella sotto la casella di testo aggiunta nella lezione 4.  
  
    > [!NOTE]  
    >  Verificare che la tabella sia posizionata all'interno dell'elenco.  
  
12. Dopo avere confermato che la tabella è selezionata, nel riquadro Gruppo di righe fare clic con il pulsante destro del mouse su Dettagli, scegliere **Aggiungi totale**, quindi fare clic su **Dopo**.  
  
     ![Aggiungi totale report](../../2014/tutorials/media/tutorial-addtotal.png "Aggiungi totale report")  
  
13. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Nel report verrà visualizzata una tabella con i dettagli e i totali delle vendite.  
  
 ![Totali vendite nel report](../../2014/tutorials/media/tutorial-reportsalestotals.png "totali vendite nel report")  
  
##  <a name="Format"></a> 6. Formattare i dati  
 Formattare solo i dati numerici come valuta e le date come giorno e ora.  
  
#### <a name="to-format-fields-table"></a>Per formattare la tabella dei campi  
  
1.  Fare clic su **Progettazione** per passare alla visualizzazione Struttura.  
  
2.  Fare clic sulle celle della tabella contenenti `[Sum(SalesSales)]` e nel gruppo **Numero** della scheda **Home** fare clic sul pulsante **Valuta** .  
  
     ![Aggiungi simbolo di valuta a vendite totali](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Aggiungi simbolo di valuta a vendite totali")  
  
3.  Fare clic sulle celle contenenti `[SalesDate]` e nell'elenco a discesa del gruppo **Numero** selezionare **Data**.  
  
4.  Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Nel report verranno visualizzati i dati formattati che rendono più facile la lettura.  
  
 ![Formatta totali vendite nel report](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "formatta totali vendite nel report")  
  
##  <a name="Save"></a> 7. Salvare il report  
 È possibile salvare i report in un server di report, in una raccolta di SharePoint o nel computer locale. È anche possibile esportare il report in diversi formati, ad esempio Word e PDF, eseguendo il report e scegliendo il formato dal menu **Esporta** .  
  
 In questa esercitazione il report verrà salvato in un server di report. Se non si dispone dell'accesso a un server di report, sarà possibile salvare il report nel computer locale.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Per salvare il report in un server di report  
  
1.  Fare clic sul pulsante **Generatore report** , quindi su **Salva con nome**.  
  
2.  Fare clic su **Siti e server recenti**.  
  
3.  Selezionare o digitare il nome del server di report per il quale si dispone delle autorizzazioni di salvataggio dei report.  
  
     Verrà visualizzato il messaggio "Connessione al server di report". Al termine della connessione, verrà visualizzato il contenuto della cartella di report specificata dall'amministratore del server di report come posizione predefinita per i report.  
  
4.  Nelle `Name`, sostituire il nome predefinito con **Informazionivenditeperterritorio**.  
  
5.  Fare clic su **Salva**.  
  
 Il report verrà salvato sul server di report. Il nome del server di report al quale si è connessi verrà visualizzato sulla barra di stato nella parte inferiore della finestra.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Per salvare il report nel computer  
  
1.  Fare clic sul pulsante **Generatore report** , quindi su **Salva con nome**.  
  
2.  Fare clic su **Desktop**, **Documenti**o **Risorse del computer**, quindi selezionare la cartella in cui si desidera salvare il report.  
  
3.  Nelle `Name`, sostituire il nome predefinito con **Informazionivenditeperterritorio**.  
  
4.  Fare clic su **Salva**.  
  
##  <a name="Line"></a> 8. (Facoltativo) Aggiungere una linea per separare le aree del report  
 Aggiungere una linea per separare l'area editoriale da quella dei dettagli del report.  
  
#### <a name="to-add-a-line"></a>Per aggiungere una linea  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nell'area **Elementi del report** della scheda **Inserisci** della barra multifunzione fare clic su **Linea**.  
  
3.  Disegnare una linea sotto la casella di testo in formato libero aggiunta nella lezione 4.  
  
4.  Fare clic sulla linea.  
  
5.  Fare clic sulla scheda **Home** .  
  
6.  Nell'area **Bordo** selezionare **4 1/2** pt per la larghezza e **Rosso**per il colore.  
  
     ![Aggiungi riga al report](../../2014/tutorials/media/tutorial-reportwithline.png "Aggiungi riga al report")  
  
##  <a name="Visualization"></a> 9. (Facoltativo) Aggiungere una visualizzazione dei dati di riepilogo  
 I rettangoli consentono di controllare la modalità di rendering del report. Posizionare un grafico a torta e un istogramma all'interno di un rettangolo per essere certi che il rendering del report venga eseguito nel modo desiderato.  
  
#### <a name="to-add-a-rectangle"></a>Per aggiungere un rettangolo  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nell'area **Elementi del report** della scheda **Inserisci** della barra multifunzione fare clic su **Rettangolo**, quindi trascinare il rettangolo nell'elenco, a destra della tabella. Assegnare al rettangolo una larghezza di 2 pollici (5 centimetri) e un'altezza di 4 pollici (10 centimetri).  
  
3.  Allineare le parti superiori del rettangolo e della tabella.  
  
#### <a name="to-add-a-pie-chart"></a>Per aggiungere un grafico a torta  
  
1.  In **Visualizzazioni dati** nella scheda **Inserisci** della barra multifunzione fare clic su **Grafico** , quindi su **Creazione guidata grafico**.  
  
2.  Nella pagina Scegliere un set di dati fare clic su **ListDataset**, quindi su **Avanti**.  
  
3.  Fare clic su **Torta**, quindi su **Avanti**.  
  
4.  Nella pagina Disponi campi del grafico trascinare Product in **Categorie**.  
  
5.  Trascinare Quantity in **i valori**, quindi fare clic su **successivo**.  
  
6.  Nel riquadro **Stili** della pagina **Scegliere uno stile** selezionare **Ardesia**.  
  
7.  Scegliere **Fine**.  
  
8.  Ridimensionare il grafico visualizzato nell'angolo superiore sinistro del report in modo che abbia un'altezza di 1 1/2 pollici (4 centimetri) e una larghezza di 2 pollici (5 centimetri).  
  
9. Trascinare il grafico all'interno del rettangolo.  
  
     ![Aggiungi grafico a torta](../../2014/tutorials/media/tutorial-addpiechart.png "Aggiungi grafico a torta")  
  
10. Fare clic con il pulsante destro del mouse sul titolo del grafico, quindi scegliere **Proprietà titolo**.  
  
11. In Testo del titolo nella finestra di dialogo **Proprietà titolo grafico** digitare: **le Quantità di prodotto vendute**.  
  
12. Fare clic sulla scheda **Tipo di carattere** , quindi nell'elenco **Dimensioni** fare clic su **10pt**.  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-add-a-column-chart"></a>Per aggiungere un istogramma  
  
1.  In **Visualizzazioni dati** nella scheda **Inserisci** della barra multifunzione fare clic su **Grafico** , quindi su **Creazione guidata grafico**.  
  
2.  Nella pagina **Scegliere un set di dati** fare clic su **ListDataset**, quindi su **Avanti**.  
  
3.  Fare clic su **Colonna**, quindi su **Avanti**.  
  
4.  Nella pagina Disponi campi del grafico, trascinare il campo Product **categorie**.  
  
5.  Trascinare Sales in **Valori** , quindi fare clic su **Avanti**.  
  
     I valori vengono visualizzati sull'asse verticale.  
  
6.  Nel riquadro **Stili** della pagina **Scegliere uno stile** selezionare **Ardesia**.  
  
7.  Scegliere **Fine**.  
  
     Un istogramma verrà aggiunto all'angolo superiore sinistro del report.  
  
8.  Ridimensionare il grafico in modo che abbia una larghezza e un'altezza di 2 pollici (5 centimetri).  
  
9. Trascinare il grafico all'interno del rettangolo sotto il grafico a torta.  
  
     ![Aggiungi istogramma](../../2014/tutorials/media/tutorial-addcolumnchart.png "Aggiungi istogramma")  
  
10. Fare clic con il pulsante destro del mouse sul titolo del grafico, quindi scegliere **Proprietà titolo**.  
  
11. In Testo del titolo nella finestra di dialogo **Proprietà titolo grafico** digitare: **le Vendite prodotto**.  
  
12. Fare clic sulla scheda **Tipo di carattere** , quindi nell'elenco **Dimensioni** fare clic suk **10pt**e infine fare clic su **OK**.  
  
13. Nell'istogramma fare clic con il pulsante destro del mouse sull'asse verticale, quindi deselezionare **Mostra titolo asse**.  
  
14. Ripetere il passaggio 13 per l'asse orizzontale.  
  
15. Fare clic con il pulsante destro del mouse sulla legenda, quindi scegliere **Elimina legenda**.  
  
    > [!NOTE]  
    >  La rimozione dei titoli degli assi e della legenda rende il grafico più leggibile quando è di piccole dimensioni.  
  
 ![Modifica titoli del grafico e Rimuovi titolo dell'asse](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "modifica titoli del grafico e Rimuovi titolo dell'asse")  
  
#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a>Per verificare che i grafici siano all'interno del rettangolo  
  
1.  Fare clic sul rettangolo aggiunto in precedenza nel corso della lezione.  
  
     Nel riquadro proprietà, il `Name` proprietà Visualizza il nome del rettangolo.  
  
     ![Nome del rettangolo](../../2014/tutorials/media/tutorial-rectanglename.png "nome del rettangolo")  
  
2.  Fare clic sul grafico a torta.  
  
3.  Nel **delle proprietà** riquadro, verificare che il `Parent` proprietà contiene il nome del rettangolo.  
  
     ![Proprietà per il grafico a torta padre](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "padre proprietà per il grafico a torta")  
  
4.  Fare clic sull'istogramma e ripetere i passaggi 2 e 3.  
  
    > [!NOTE]  
    >  Se non si trovano all'interno del rettangolo, i grafici non verranno visualizzati insieme nel report visualizzabile.  
  
#### <a name="to-make-the-charts-the-same-size"></a>Per assegnare ai grafici le stesse dimensioni  
  
1.  Fare clic sul grafico a torta, premere CTRL, quindi fare clic sull'istogramma.  
  
2.  Con entrambi i grafici selezionati, fare clic con il pulsante destro del mouse, scegliere **Layout**, quindi fare clic su **Assegna stessa larghezza**.  
  
     ![Rendere la larghezza delle grafico lo stesso](../../2014/tutorials/media/tutorial-makechartssamewidth.png "rendere lo stesso larghezze grafico")  
  
    > [!NOTE]  
    >  Il primo elemento selezionato determina la larghezza di tutti gli elementi selezionati.  
  
3.  Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Nel report verranno visualizzati i dati di vendita riepilogativi in diagrammi a torta e istogrammi.  
  
 ![Report in formato libero dell'esercitazione, SSRS](../../2014/tutorials/media/tutorial-reportfinal.png "report in formato libero dell'esercitazione, SSRS")  
  
## <a name="more-information"></a>Ulteriori informazioni  
 Per altre informazioni sugli elenchi, vedere [tabelle, matrici ed elenchi &#40;Generatore Report e SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [Elenca &#40;Generatore Report e SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [dati Tablix Aree dell'area &#40;Report e SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), e [celle di regione dati Tablix, le righe e colonne &#40;Generatore Report&#41; e SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 Per altre informazioni sulla progettazione delle query, vedere [Finestre di progettazione query &#40;Generatore report&#41;](../../2014/reporting-services/query-designers-report-builder.md) e [Interfaccia utente di Progettazione query basata su testo &#40;Generatore report&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazioni su &#40;Generatore Report&#41;](report-builder-tutorials.md)   
 [Generatore report in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  