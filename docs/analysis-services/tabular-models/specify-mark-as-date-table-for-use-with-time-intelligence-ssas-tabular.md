---
title: Specificare contrassegna come tabella data | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6a4ad929c866658ce241f33ddd2a5326dc78e19
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039785"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>Specificare contrassegna come tabella data per l'utilizzo con Business intelligence
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Per utilizzare le funzioni di business intelligence nelle formule DAX, è necessario specificare una tabella di data e una colonna identificatore univoco (datetime) del tipo di dati Data. Una volta specificata una colonna nella tabella relativa alla data come identificatore univoco, è possibile creare le relazioni tra le colonne nella tabella in questione e tutte le tabelle dei fatti.  
  
 Quando si utilizzano funzioni di business intelligence, si applicano le regole seguenti:  
  
-   Quando si utilizzano funzioni di business intelligence DAX, non specificare mai una colonna datetime da una tabella dei fatti. Creare sempre una tabella relativa alla data separata nel modello con almeno un colonna di tipo datetime con tipo di dati Date e con valori univoci.  
  
-   Verificare che la tabella relativa alla data disponga di un intervallo di date continuo.  
  
-   È consigliabile che la granularità della colonna di tipo datetime nella tabella relativa alla data sia a livello di giorno, senza frazioni di un giorno.  
  
-   È necessario specificare una tabella relativa alla data e una colonna dell'identificatore univoco utilizzando la finestra di dialogo **Contrassegna come tabella data** .  
  
-   Creare le relazioni tra le tabelle dei fatti e le colonne di tipo di dati Date nella tabella relativa alla data.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>Per specificare una tabella relativa alla data e un identificatore univoco  
  
1.  In Progettazione modelli fare clic sulla tabella relativa alla data.  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare una colonna da utilizzare come identificatore univoco. In questa colonna devono essere inclusi valori univoci e il tipo di dati utilizzato deve essere Date. Esempio:  
  
    |Data|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  Se necessario, creare tutte le relazioni tra le tabelle dei fatti e la tabella relativa alla data.  
  
## <a name="see-also"></a>Vedere anche  
 [Calcoli](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Funzioni di business intelligence (DAX)](http://msdn.microsoft.com/en-us/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
