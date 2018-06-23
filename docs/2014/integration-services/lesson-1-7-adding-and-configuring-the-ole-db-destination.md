---
title: 'Passaggio 7: Aggiunta e configurazione della destinazione OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
caps.latest.revision: 24
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9492f985dda337159257257c675fe37d39f162b5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168342"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a>Passaggio 7: Aggiunta e configurazione della destinazione OLE DB
  Il pacchetto ora consente di estrarre i dati dall'origine file flat e trasformarli in un formato compatibile con la destinazione. L'attività successiva consiste nel caricare i dati trasformati nella destinazione. Per caricare i dati è necessario aggiungere una destinazione OLE DB al flusso di dati. La destinazione OLE DB può utilizzare una tabella di database, una vista o un comando SQL per caricare i dati in diversi database compatibili con OLE DB.  
  
 In questa procedura verrà aggiunta e configurata una destinazione OLE DB in modo da utilizzare la gestione connessione OLE DB creata precedentemente.  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a>Per aggiungere e configurare la destinazione OLE DB di esempio  
  
1.  Nella **Casella degli strumenti SSIS**espandere **Altre destinazioni**e trascinare **Destinazione OLE DB** nell'area di progettazione della scheda **Flusso di dati** . Posizionare la destinazione OLE DB sotto la trasformazione **Lookup Date Key** .  
  
2.  Fare clic sulla trasformazione **Lookup Date Key** e trascinare la freccia verde sulla nuova **Destinazione OLE DB** per collegare i due componenti.  
  
3.  Nella finestra di dialogo **Selezione input e output** , nella casella di riepilogo **Output** fare clic su **Output corrispondenza ricerca**e fare clic su **OK**.  
  
4.  Nell'area di progettazione **Flusso di dati** fare clic su **Destinazione OLE DB** nel componente **Destinazione OLE DB** appena aggiunto e cambiare il nome in **Sample OLE DB Destination**.  
  
5.  Fare doppio clic su **Sample OLE DB Destination**.  
  
6.  Nella finestra di dialogo **Editor destinazione OLE DB** verificare che **localhost.AdventureWorksDW2012** sia selezionato nella casella **Gestione connessione OLE DB** .  
  
7.  Nella casella **Nome tabella o vista** digitare o selezionare **[dbo].[FactCurrencyRate]**.  
  
8.  Fare clic sul pulsante **Nuova** per creare una nuova tabella.  Denominare **NewFactCurrencyRate**la tabella nello script.  Fare clic su **OK**.  
  
9. Dopo aver fatto clic su **OK**la finestra di dialogo si chiuderà e la casella **Nome tabella o vista** verrà impostata automaticamente su **NewFactCurrencyRate**.  
  
10. Fare clic su **Mapping**.  
  
11. Verificare che le colonne di input **AverageRate**, **CurrencyKey**, **EndOfDayRate**e **DateKey** siano assegnate correttamente alle colonne di destinazione. Il mapping è corretto se include colonne con nomi corrispondenti.  
  
12. Fare clic su **OK**.  
  
13. Fare clic con il pulsante destro del mouse sulla destinazione **Sample OLE DB Destination** e scegliere **Proprietà**.  
  
14. Nella finestra Proprietà verificare che il `LocaleID` è impostata su **inglese (Stati Uniti)** e il`DefaultCodePage` è impostata su **1252**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Passaggio 8: Semplificazione del pacchetto della lezione 1 comprensione](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazione OLE DB](data-flow/ole-db-destination.md)  
  
  