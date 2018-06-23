---
title: 'Attività 17: Verifica del progetto DQS Cleansing creato dal pacchetto SSIS | Documenti Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4226fd9a8e8eb8aa2851eed8eb318b8535010c8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166744"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Attività 17: Verifica del progetto DQS Cleansing creato dal pacchetto SSIS
  In questa attività viene aperto il progetto DQS creato dal pacchetto SSIS nel client DQS, vengono esaminati i risultati del processo di pulizia e, facoltativamente, viene effettuata la pulizia interattiva e l'esportazione dei risultati.  
  
1.  Avviare **Client Data Quality**.  
  
2.  Fare clic su **il monitoraggio dell'attività** nel **amministrazione** riquadro.  
  
3.  Ordinare l'elenco in base alle **ora di inizio attività** per visualizzare il record più recente.  
  
4.  Si noti che il nome del progetto nel formato seguente: **cleanseandcurate. CLEANSE Supplier Data. GUID**.  
  
     ![Progetto DQS Cleansing creato dal pacchetto SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "progetto DQS Cleansing creato dal pacchetto SSIS")  
  
5.  Si noti che il valore il **attivo** campo **Active**.  
  
6.  Fare clic su **Profiler** scheda nel riquadro inferiore per visualizzare statistiche del profiler per l'attività di pulizia effettuata dal pacchetto SSIS.  
  
7.  Fare clic su **chiudere** per chiudere la **amministrazione** dello schermo.  
  
8.  Nella pagina principale del **Client DQS**, fare clic su **Apri progetto Data Quality** nel **progetti Data Quality** riquadro.  
  
9. Nell'elenco di progetti selezionare il progetto creato dal componente SSIS DQS Cleansing. Il nome del progetto deve essere nel formato: **cleanseandcurate. CLEANSE Supplier Data. GUID (in rosso)**. Potrebbe essere necessario ordinare l'elenco in base alle **data di creazione** colonna e cercare il record più recente.  
  
10. Scegliere **Avanti**.  
  
11. Il **Gestisci e Visualizza risultati** pagina dovrebbe essere familiare dalla pulizia interattiva effettuata precedentemente durante questa esercitazione.  
  
12. Esaminare i risultati della pulizia. Inoltre, è possibile effettuare la pulizia interattiva ed esportare i risultati in un file di Excel o in un database nella pagina successiva.  
  
13. Scegliere **Avanti**. In questo **esportare** pagina, è possibile esportare i risultati in un file di excel, file CSV, o a un database SQL.  
  
14. Fare clic su **fine** per completare l'attività.  
  
15. Nella pagina principale del **Client DQS**, fare clic su **monitoraggio dell'attività** nel **amministrazione** riquadro.  
  
16. Si noti che il valore di **IsActive** campo per il progetto è **finito** ora.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Conclusione](../../2014/tutorials/conclusion.md)  
  
  