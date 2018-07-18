---
title: Report di valutazione (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
caps.latest.revision: 14
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d5d2d79c47dd1a819e602e55aad36844445e6c79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="assessment-report-accesstosql"></a>Report di valutazione (AccessToSQL)
Nella finestra di Report di valutazione vengono visualizzati i risultati della conversione di oggetti di database per [!INCLUDE[tsql](../../includes/tsql_md.md)] , sintassi e possibile stimare la complessità e costi dei progetti di migrazione.  
  
Per creare un report di valutazione, selezionare gli oggetti da convertire in Visualizzatore metadati di origine, fare doppio clic su **database**, quindi selezionare **crea Report**. È inoltre possibile visualizzare questo report automaticamente dopo la conversione degli schemi. Tuttavia, il nome del report sarà Report di conversione. Per ulteriori informazioni, vedere [progetto. le impostazioni (GUI) (SSMA comune)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Opzioni  
**Riquadro di esplorazione**  
Contiene una gerarchia di oggetti nel report di valutazione. Espandere le cartelle per visualizzare i componenti secondari e i singoli oggetti. Quando si fa clic su una categoria o un oggetto, le statistiche di conversione per tale categoria o un oggetto vengono visualizzati nel riquadro dei dettagli.  
  
**Riquadro dei dettagli**  
Mostra la conversione di messaggi di avviso o di statistiche e di errore per l'oggetto selezionato. Ad esempio, se si seleziona la cartella di tabelle, nel riquadro di dettagli vengono visualizzati i numeri di chiavi esterne, indici, chiavi primarie e le tabelle che sono state convertite.  
  
**Riquadro messaggi**  
Viene illustrato l'errori, avvisi e messaggi informativi che sono stati generati quando il report di valutazione è stato creato. I messaggi vengono raggruppati per numero.  
  
Per visualizzare i dettagli del messaggio, fare clic su **errori**, **avvisi**, o **messaggi**, quindi espandere un messaggio. SSMA verrà visualizzato l'elenco di oggetti che dispongono di questo errore. Fare clic su un oggetto per visualizzare tutte le informazioni dettagliate sulla conversione per l'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
[Reference(Access) dell'interfaccia utente](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  
