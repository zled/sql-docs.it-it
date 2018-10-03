---
title: 'Attività 2: Mapping delle colonne di Excel ai domini DQS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4af26cb52b8d30dbfad5fc5ab40dc732f8ce4dc2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135521"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Attività 2: Mapping delle colonne di Excel ai domini DQS
    
1.  Nella pagina **Mappa** selezionare **File di Excel** per **Origine dati**.  
  
2.  Fare clic su **esplorare**, selezionare **Suppliers. xlsx**, fare clic su **Open**.  
  
3.  Selezionare **IncomingSuppliers$** per il **foglio di lavoro**.  
  
4.  Eseguire il mapping delle colonne come illustrato nella tabella e schermata seguenti. Durante la creazione di mapping per il **lo stato** dominio, fare clic su **Aggiungi un mapping colonne** pulsante sulla barra degli strumenti posizionata proprio sopra l'elenco.  
  
    > [!TIP]  
    >  Non si usa **Supplier ID** colonna/il dominio per la pulizia. Si userà il **Supplier ID** dominio in un secondo momento nell'attività di corrispondenza.  
  
    |Colonna di Excel|Dominio DQS|  
    |------------------|----------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Riga indirizzo|Riga indirizzo|  
    |Città|Città|  
    |State|State|  
    |Paese (fare clic su **+ (Aggiungi un mapping colonne)** sulla barra degli strumenti per aggiungere una riga)|Country|  
    |Zip Code|CAP|  
  
     ![I mapping delle colonne di Excel ai domini](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "i mapping delle colonne di Excel ai domini")  
  
5.  Come è stato eseguito il mapping di tutti i singoli domini all'interno di **Address Validation** dominio composito, il dominio composito partecipa automaticamente anche il processo di pulizia. Fare clic su **Visualizza/seleziona domini compositi** pulsante per verificare che il **Address Validation** dominio composito viene selezionata automaticamente e quindi fare clic su **OK**.  
  
     ![Finestra di dialogo Visualizza/seleziona domini compositi](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "finestra di dialogo Visualizza/seleziona domini compositi")  
  
6.  Fare clic su **successivo** per passare alle **Pulisci** pagina.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 3: Pulizia dei dati fornitore rispetto alla Knowledge Base Suppliers](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
