---
title: "Attività 10: Configurazione del dominio composito per l'utilizzo di servizio dati di riferimento | Documenti Microsoft"
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
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2a5d37578ac8336b67201161ef4de59baf90649c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065264"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Attività 10: Configurazione del dominio composito per utilizzare il servizio dati di riferimento
  In questa attività si configura il **Address Validation** dominio composito per utilizzare il **Melissa Data – controllo indirizzo** servizio. In fase di esecuzione, durante l'attività di pulizia, tramite DQS i valori del dominio Address Validation vengono passati al servizio per la pulizia. Vedere [mappa dominio/dominio composito ai dati di riferimento](http://msdn.microsoft.com/library/hh213030.aspx) per altri dettagli.  
  
1.  Nella pagina principale del **Client DQS**, fare clic su **Suppliers (Domain Management)** sotto **Knowledge Base recenti** per avviare il **Domain Management**pagina.  
  
2.  Selezionare il **Address Validation** dominio composito nel **elenco di domini**.  
  
3.  Nel riquadro di destra, passare il **i dati di riferimento** scheda.  
  
     ![Scheda dati di riferimento](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "scheda dati di riferimento")  
  
4.  Fare clic su **Sfoglia** pulsante sulla barra degli strumenti.  
  
5.  Nel **catalogo di provider di dati di riferimento Online** finestra di dialogo **casella di controllo** accanto a **Melissa Data – controllo indirizzo**.  
  
     ![Selezione di Melissa Data - controllo indirizzo](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "selezionare Melissa Data - controllo indirizzo")  
  
6.  Nel riquadro destro, nelle **Schema** sezione, eseguire il mapping **Address Line** dominio per il **Address Line (M)** elemento dello schema utilizzando l'elenco a discesa.  
  
     ![Eseguire il mapping elemento dello Schema di servizi desktop remoto al dominio](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "mappare l'elemento dello Schema di servizi desktop remoto al dominio")  
  
7.  Fare clic su **Aggiungi voce di Schema (+)** pulsante sulla barra degli strumenti per creare una voce nell'elenco.  
  
     ![Aggiungi pulsante della barra degli strumenti di Schema voce](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Aggiungi pulsante della barra degli strumenti voce di Schema")  
  
8.  Eseguire il mapping dei domini DQS utilizzando gli elenchi a discesa come illustrato nella figura seguente.  
  
     ![Mappare gli elementi dello Schema di servizi desktop remoto a domini](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "mappare gli elementi dello Schema di servizi desktop remoto a domini")  
  
9. Scegliere **OK** per chiudere la finestra di dialogo.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 11: Pubblicazione della Knowledge Base](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  