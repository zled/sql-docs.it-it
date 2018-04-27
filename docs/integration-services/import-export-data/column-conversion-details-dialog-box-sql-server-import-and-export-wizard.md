---
title: Finestra di dialogo Dettagli conversione colonna (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: import-export-data
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.issuedetails.f1
ms.assetid: e2d00a39-dfbd-4821-a4d8-a5bd1164ed4d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97c1f0b447b26c2afc1836bed0269eba33d1656c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="column-conversion-details-dialog-box-sql-server-import-and-export-wizard"></a>Finestra di dialogo Dettagli conversione colonna (Importazione/Esportazione guidata SQL Server)
  Se si fa doppio clic su una riga per una singola colonna nella pagina **Verifica mapping tra i tipi di dati** , l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza la finestra di dialogo **Dettagli conversione colonna** . In questa pagina è possibile esaminare informazioni dettagliate sulla conversione per una singola colonna. Le informazioni comprendono gli elementi seguenti.
-   Il tipo di dati della colonna all'origine e alla destinazione.
-   La conversione del tipo di dati che verrà eseguita dalla procedura guidata, nel caso in cui sia necessaria una conversione.
-   I file di mapping dei tipi di dati usati dalla procedura guidata per determinare la conversione dei tipi di dati necessaria. 

## <a name="screen-shot-of-the-column-conversion-details-page"></a>Screenshot della pagina Dettagli conversione colonna 
 Lo screenshot seguente mostra la finestra di dialogo **Dettagli conversione colonna** della procedura guidata dopo che l'utente ha fatto doppio clic su una riga nella pagina **Verifica mapping tra i tipi di dati** . Per altre informazioni sulla pagina **Verifica mapping tra i tipi di dati** , vedere [Verifica mapping tra i tipi di dati (Importazione/Esportazione guidata SQL Server)](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).
 
Questo esempio mostra quanto segue:
-   La colonna `PersonID` nella tabella SQL Server di origine è di tipo `int`. La procedura guidata esegue il mapping di questo tipo al tipo di dati `DT_I4` di SQL Server Integration Services (SSIS), che è un intero con segno a quattro byte, tramite riferimento al file di mapping dei tipi di dati MSSQLToSSIS10.xml.
-   Anche la colonna `PersonID` nella tabella SQL Server di destinazione è di tipo `int`. La procedura guidata esegue il mapping di questo tipo allo stesso tipo di dati SSIS.
-   La procedura guidata viene conclusa, *Non è necessario eseguire la conversione per questo tipo di colonna*.
 
  
 ![Pagina Dettagli conversione colonna dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/media/column-conversion.png "Pagina Dettagli conversione colonna dell'Importazione/Esportazione guidata") 
  
## <a name="whats-next"></a>Quali sono le operazioni successive?  
 Dopo aver esaminato i dettagli di conversione della colonna e aver fatto doppio clic su **OK**, dalla finestra di dialogo **Dettagli conversione colonna** si passa nuovamente alla pagina **Verifica mapping tra i tipi di dati** . Per altre informazioni, vedere [Verifica mapping tra i tipi di dati](../../integration-services/import-export-data/review-data-type-mapping-sql-server-import-and-export-wizard.md).  

## <a name="see-also"></a>Vedere anche
[Data Type Mapping in the SQL Server Import and Export Wizard](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
