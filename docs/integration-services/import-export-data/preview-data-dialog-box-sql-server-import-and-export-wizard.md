---
title: Visualizzare in anteprima la finestra di dialogo di dati (SQL Server importazione / esportazione guidata) | Documenti Microsoft
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.previewdata.f1
ms.assetid: 423ac26a-ba02-4fdf-88b4-07995fe4a97e
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bfa75d2c1d2d50d1f0205fed22811ddbb3b96747
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="preview-data-dialog-box-sql-server-import-and-export-wizard"></a>Finestra di dialogo Anteprima dati (Importazione/Esportazione guidata SQL Server)
  Dopo aver specificato i dati che si desidera copiare, è possibile scegliere facoltativamente **Anteprima** per aprire la finestra di dialogo **Anteprima dati** . In questa pagina è possibile visualizzare in anteprima fino a 200 righe di dati di esempio dall'origine dati. Questo permette di verificare che la procedura guidata sta per copiare i dati desiderati.
  
## <a name="screen-shot-of-the-preview-data-page"></a>Screenshot della pagina Anteprima dati 
 L'immagine riportata di seguito illustra la finestra di dialogo **Anteprima dati** della procedura guidata.  
 
![Pagina di dati di anteprima dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/preview-data.png "pagina di dati di anteprima dell'importazione / esportazione guidata")  
  
## <a name="preview-sample-data"></a>Visualizzare in anteprima i dati di esempio  
 **Origine**  
Visualizza la query usata dalla procedura guidata per caricare i dati dall'origine dati.

Se è stata selezionata una tabella da copiare, il **origine** campo viene visualizzato un `SELECT * FROM <table>` query anziché il nome della tabella. 
  
 **Griglia Dati di esempio**  
 Visualizza fino a 200 righe di dati di esempio dell'origine dati restituite dalla query.  


## <a name="thats-not-right-i-want-to-change-something"></a>Non è corretto, che è necessario modificare un elemento
Dopo aver visualizzato i dati in anteprima, potrebbe essere necessario modificare le opzioni selezionate nelle pagine precedenti della procedura guidata. Per apportare queste modifiche, fare clic su **OK** per tornare al **Selezione origine tabelle e viste** pagina e quindi fare clic su **nuovamente** per tornare alle pagine precedenti in cui è possibile modificare il selezioni.

## <a name="whats-next"></a>Operazioni successive  
 Dopo aver visualizzato in anteprima i dati che si stanno per copiare e aver fatto clic su **OK**, la finestra di dialogo **Anteprima dati** consente di tornare alla pagina **Seleziona tabelle e viste di origine** o **Configurare la destinazione del file flat** . Per altre informazioni, vedere [Seleziona tabelle e viste di origine](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md) o [Configurare la destinazione del file flat](../../integration-services/import-export-data/configure-flat-file-destination-sql-server-import-and-export-wizard.md).  
 
 ## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

