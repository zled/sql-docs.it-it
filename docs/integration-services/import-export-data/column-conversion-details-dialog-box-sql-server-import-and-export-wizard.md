---
title: La finestra di dialogo (SQL Server importazione / esportazione guidata) dei dettagli conversione colonna | Documenti Microsoft
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
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 985ba8a478999a153b3bb32649b98c3e809fc5e8
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Finestra di dialogo Dettagli conversione colonna (Importazione/Esportazione guidata SQL Server)
  Se si fa doppio clic su una riga per una singola colonna nella pagina **Verifica mapping tra i tipi di dati** , l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza la finestra di dialogo **Dettagli conversione colonna** . In questa pagina è possibile esaminare informazioni dettagliate sulla conversione per una singola colonna. Le informazioni comprendono gli elementi seguenti.
-   Il tipo di dati della colonna nell'origine e destinazione.
-   Il tipo di dati conversione che verrà eseguita la procedura guidata, se non è necessaria una conversione.
-   I file di mapping dei tipi di dati usati dalla procedura guidata per determinare la conversione dei tipi di dati necessaria. 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>Screenshot della pagina Dettagli conversione colonna 
 Lo screenshot seguente mostra la finestra di dialogo **Dettagli conversione colonna** della procedura guidata dopo che l'utente ha fatto doppio clic su una riga nella pagina **Verifica mapping tra i tipi di dati** . Per altre informazioni sulla pagina **Verifica mapping tra i tipi di dati** , vedere [Verifica mapping tra i tipi di dati (Importazione/Esportazione guidata SQL Server)](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).
 
In questo esempio, viene visualizzato quanto segue.
-   Il `PersonID` colonna nella tabella di SQL Server di origine è di tipo `int`. La procedura guidata esegue il mapping di questo tipo di SQL Server Integration Services (SSIS) `DT_I4` tipo di dati, ovvero un intero con segno a 4 byte, facendo riferimento al file di mapping dei tipi di dati MSSQLToSSIS10.xml.
-   Il `PersonID` colonna nella tabella di SQL Server di destinazione è di tipo `int`. La procedura guidata esegue il mapping di questo tipo per il tipo di dati SSIS.
-   Si conclude la procedura guidata, *questa colonna non è necessario che la conversione*.
 
  
 ![Pagina di conversione di colonna dell'importazione / esportazione guidata](../../integration-services/import-export-data/media/column-conversion.png "pagina conversione colonna dell'importazione / esportazione guidata") 
  
## <a name="whats-next"></a>Operazioni successive  
 Dopo aver esaminato i dettagli di conversione della colonna e aver fatto doppio clic su **OK**, dalla finestra di dialogo **Dettagli conversione colonna** si passa nuovamente alla pagina **Verifica mapping tra i tipi di dati** . Per altre informazioni, vedere [Verifica mapping tra i tipi di dati](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Vedere anche
[Data Type Mapping in the SQL Server Import and Export Wizard](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)

