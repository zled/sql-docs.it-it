---
title: 'Attività 4: Gestione e visualizzazione dei risultati | Documenti Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0e045d9722d380af19147746944c842f97ac9843
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170482"
---
# <a name="task-4-manaing-and-viewing-results"></a>Attività 4: Gestione e visualizzazione dei risultati
  In questa attività si controllano i risultati della pulizia computerizzata; inoltre, si effettua la pulizia interattiva dei dati del fornitore. Vedere [fase di pulizia interattiva](http://msdn.microsoft.com/library/hh213061.aspx#Interactive) per altri dettagli.  
  
1.  Selezionare **Contact Email** dominio dall'elenco di domini.  
  
2.  Passare il **valido** scheda nel riquadro di destra. Si noti che alla fine dei due indirizzi di posta elettronica manca la lettera "s". Questi due messaggi di posta elettronica sono stati trovati non validi dalla regola di dominio che richiede tutti gli indirizzi di posta elettronica al termine **@adventure-works.com** (con del '). In DQS viene applicata la regola di dominio durante la pulizia per stabilire la validità di un indirizzo di posta elettronica. In questa scheda vengono visualizzati i valori del dominio contrassegnati come non validi nella Knowledge Base o che non hanno superato una regola di dominio. In questo caso, i valori in questione non hanno superato la regola di dominio (Email Validation).  
  
3.  Nel **Correggi in** colonna, digitare l'indirizzo e-mail corretto indirizzo che terminano con **@adventure-works.com** (con del ').  
  
     ![Le correzioni di regola di convalida posta elettronica](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "correzioni dalla regola di convalida posta elettronica")  
  
4.  Fare clic su **Approva** per entrambi i record approvare entrambe le modifiche. Quando si approva, i record vengono spostati per il **con correzione** scheda. Anziché approvare separatamente ogni elemento, è possibile approvare tutte le modifiche contemporaneamente utilizzando il **approvare tutti i termini** pulsante della barra degli strumenti.  
  
5.  Passare il **New** scheda nel riquadro di destra. I valori in questa scheda sono quelli per i quali DQS non dispone ancora di informazioni sufficienti nella Knowledge Base per stabilire se sono corretti. Pertanto, non è possibile apportare o suggerire modifiche ai valori di dominio.  
  
6.  Esaminare i valori per verificare che tutti i messaggi di posta elettronica termina con **@adventure-works.com** e fare clic su **approvare tutti i termini** sulla barra degli strumenti. Spostano i valori approvati da questa scheda per il **correggere** scheda.  
  
7.  Selezionare il **paese** dominio dall'elenco di domini.  
  
8.  Passare il **con correzione** scheda nel riquadro destro e notare che **United State** valore viene corretto automaticamente per il **Stati Uniti** con del ' alla fine. Questa regola non rappresenta una regola definita per il **paese** dominio, tuttavia, in DQS viene **83%** certi che il valore corretto sarà **Italia**. Il **Approva** pulsante è selezionato automaticamente per tutti i **con correzione** elementi. È possibile eseguire l'override di questo comportamento e rifiutare una modifica.  
  
9. Si noti che **USA** è stato corretto in **Italia** perché sono sinonimi e **Italia** è il valore iniziale (preferito).  
  
     ![Correzioni basate su sinonimi](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "correzioni basate su sinonimi")  
  
10. Si noti che il **Approva** pulsante è già selezionato per questi valori con correzione. Si tratta del comportamento predefinito per i valori con correzione. È possibile rifiutare le modifiche e quando si esegue questa operazione, il valore viene spostato il **valido** scheda.  
  
11. Selezionare **Supplier Name** dall'elenco di domini.  
  
12. Passare il **con correzione** scheda nel riquadro di destra.  
  
     ![Nomi fornitori con correzione](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "nomi fornitori con correzione")  
  
    1.  Si noti che **r. Datum corp** è stato corretto in **A. Datum Corporation** e il **motivo** è impostato su **relazione basata su termini. A. datum Corporation** è un valore di dominio noto in DQS perché è stato individuato durante il processo di individuazione delle informazioni. È pertanto DQS **100% certi** di questa correzione.  
  
    2.  Si noti che che **Lazy Country Storex** è stato corretto in **Lazy Country Store**, **livello di confidenza** è impostata su **100%** e il  **Motivo** è impostata su **valore di dominio**. Durante il processo di individuazione delle informazioni, si imposta **Lazy Country Storex** come un errore con **Lazy Country Store** come il **correzione**, quindi DQS è **100% certi** questa correzione.  
  
    3.  DQS non ha familiarità con gli altri valori nell'elenco, ma vengono individuate le correzioni per questi valori usando la **correttore ortografico** e vengono proposte le opportune correzioni. DQS è **non 100%** certi queste correzioni, ma il livello di confidenza è superiore all'80%, ovvero il livello di soglia per correzioni automatiche in modo da DQS vengono proposte le correzioni.  
  
13. Si noti che il **Approva** viene abilitata automaticamente per tutti i valori. È possibile sostituire il valore con correzione o rifiutare la modifica in base alle esigenze. Per impostazione predefinita il **Approva** pulsante è selezionato per tutti i valori nel **con correzione** scheda.  
  
14. Passare il **New** scheda.  
  
15. Si noti che **corp** è stato corretto in **Corporation**, **co** è stato corretto in **aziendale**, e **Inc.** è stato corretto in **Incorporated**. Ad esempio **Consolidate Inc.** è stato corretto in **Consolidate Incorporated** e **Consolidated CO.** è stato corretto in **Consolidated Company**, e **Frabrikam corp** è stato corretto in **Fabrikam Corporation**.  È possibile vedere che **relazione basata su termini** indicate come il motivo. Queste modifiche vengono proposte tramite le relazioni basate su termini definite durante l'attività di gestione del dominio. È possibile modificare il **Correggi in** valori manualmente qui.  
  
16. Scorrere l'elenco per visualizzare **Hunxgry Coyote Store** con una riga rossa ondulata. Fare clic su di esso e fare clic su **Hungry Coyote Store** (con senza "x"). Il **Correggi in** colonna viene popolata automaticamente con **Hungry Coyote Store**. Inoltre, è possibile digitare manualmente un valore nella colonna Correggi in.  
  
17. Fare clic su **approvare tutti i termini** dalla barra degli strumenti. I valori di dominio con il **Correggi in** spostare valore specificato per il **con correzione** scheda e i nuovi valori con non è associato alcun **Correggi in** valori spostano il  **Corretto** scheda.  
  
18. Selezionare il **Address Validation** dominio composito dall'elenco di domini.  
  
19. Nel riquadro di destra, passare il **correggere** scheda. Dovrebbe essere indirizzi che devono essere corretti dal **Melissa Data – controllo indirizzo** DQS servizio sul **Azure Marketplace**.  
  
20. Passare il **con correzione** scheda.  
  
21. Si noti che **stato** per il record con **Città** come **Los Angeles** è impostata su **autorità di certificazione** ora. Si noti che nel **motivo** campo è di che **corretti dalla regola 'City-state Rule'**.  
  
     ![Correzione regola City-state](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "correzione regola City-state")  
  
22. Si noti che il **Approva** pulsante di opzione è già selezionato per questo elemento nell'elenco. Si tratta del comportamento predefinito per gli elementi nel **con correzione** scheda.  
  
23. Passare il **suggeriti** scheda. Esaminare le modifiche suggerite per la **Melissa Data – controllo indirizzo** servizio.  
  
24. **Fare clic su Approva tutti i termini** nel pulsante della barra degli strumenti fare clic **OK** sul **conferma** finestra di messaggio.  
  
     ![Approvare tutti i pulsante della barra degli strumenti di termini](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "approvare tutti i termini della barra degli strumenti pulsante")  
  
25. Fare clic su **successivo** per attivare il **esportare** pagina.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 5: Esportazione di pulizia dei risultati in un File di Excel](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  