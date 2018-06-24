---
title: 'Attività 5: Esportazione di pulizia dei risultati in un File di Excel | Documenti Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f8a716d3b6c0007ceb89f36f23584bb4adb4f706
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055822"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Attività 5: Esportazione dei risultati della pulizia in un file di Excel
  In questa attività vengono esportati i risultati dell'attività di pulizia in un file di Excel. Vedere [fase di esportazione](http://msdn.microsoft.com/library/hh213061.aspx#Export) per altre informazioni.  
  
1.  Nel riquadro destro, selezionare **Excel** per il **tipo di destinazione**.  
  
2.  Fare clic su **esplorare**, specificare il nome del file di output come **Cleansed Supplier List. xls**, quindi fare clic su **aperta**.  
  
3.  Selezionare **Data Only** per il **Output** formato per esportare solo i dati puliti. La seconda opzione, **dati e informazioni pulizia**, consente di esportare i dettagli dell'attività pulizia insieme ai dati puliti. Il **standardizzare formato** opzione consente di applicare i formati di output definiti in un dominio per i valori del dominio. Non è stato definito un formato di output in un dominio nell'esercitazione.  
  
     ![Pagina dei risultati di esportazione pulizia](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "esportazione pulizia pagina risultati")  
  
4.  Fare clic su **esportare** per esportare i dati. Non fare clic **fine** ancora.  
  
5.  Fare clic su **Close** sul **esportazione** finestra di dialogo.  
  
6.  Fare clic su **fine** per completare l'attività. Se si dimentica di esportare i risultati prima di fare clic **fine**, fare clic su **Apri progetto Data Quality** nella pagina principale del **Client DQS**, selezionare **Cleanse Supplier Elenco** dall'elenco dei progetti, fare clic su **successivo** nella parte inferiore della schermata per ottenere il **Esporta** fase del processo di pulizia. È inoltre possibile passare alla **Gestisci e Visualizza risultati** scheda, fare clic su **nuovamente** pulsante.  
  
7.  Aprire la **Cleansed Supplier List. xls** eseguire le operazioni seguenti:  
  
    1.  Assicurarsi che non vi siano indirizzi di posta elettronica che terminino con adventure-work.com (senza la lettera "s ") cercando adventure-work.com nel foglio di lavoro.  
  
    2.  Vedere che è presente alcun **USA** valore il **paese** colonna.  
  
    3.  Cercare **Los Angeles** e verificare che il **stato** è impostato su **CA**.  
  
    4.  Verificare che vi sia alcun termine **co**, **corp**, e **Inc.**.  
  
    5.  Eliminare il **Address Validation** colonna dal foglio di calcolo e salvare il file di excel. Questa colonna aggiuntiva corrisponde al dominio composito Address Validation.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 6: Importazione di valori dal progetto Cleanse Supplier List](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  