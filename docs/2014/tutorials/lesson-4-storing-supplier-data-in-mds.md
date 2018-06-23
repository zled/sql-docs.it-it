---
title: 'Lezione 4: Archiviazione dei dati fornitore in MDS | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 40f09aa6544bc38378e547c5b6e94dd26956a549
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158803"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>Lezione 4: Archiviazione dei dati fornitore in MDS
  Master Data Services (MDS) è una soluzione SQL Server per la gestione dei dati master. Nella gestione dei dati master vengono descritti gli sforzi fatti da un'organizzazione per individuare e definire elenchi non transazionali di dati.  
  
 I modelli rappresentano il livello più elevato di organizzazione in Master Data Services e consentono di organizzare la struttura dei dati master. Per l'implementazione di MDS si può disporre di uno o più modelli in ognuno dei quali vengono raggruppati dati simili. I dati master rientrano in genere in una delle quattro categorie seguenti: persone, luoghi, cose o concetti. È ad esempio possibile creare un modello Product per contenere dati relativi al prodotto oppure un modello Customer per contenere dati relativi al cliente. Vedere [modelli (Master Data Services)](http://msdn.microsoft.com/library/ee633746.aspx) per altri dettagli.  
  
 In un modello possono essere incluse una o più entità. Ogni entità dispone di attributi (colonne) e membri (righe). In ogni riga sono contenuti i dati master. In questa lezione viene creato un modello Suppliers con due entità denominate Supplier e State. L'entità Supplier avrà i seguenti attributi: Code, Name, Contact First Name, Contact Last Name, Contact Email Address, Address Line, City, State, Zip e Country. Vedere [attributi (Master Data Services)](http://msdn.microsoft.com/library/ee633745.aspx) per ulteriori informazioni sugli attributi in generale. Gli attributi Name e Code corrispondono alle colonne SupplierID e Supplier Name nel file di Excel relativo ai fornitori con dati puliti e corrispondenti.  
  
 Un attributo basato su dominio è un attributo i cui valori sono popolati da membri di un'altra entità. Gli attributi basati su dominio non consentono l'immissione di valori di attributo non validi da parte di utenti. È possibile selezionare un valore di attributo solo nell'elenco a discesa popolato da un'altra entità. In questa esercitazione, l'attributo State dell'entità Supplier è un attributo basato su dominio con valori dell'entità State. Il valore dell'attributo State dell'entità Supplier può essere impostato solo su uno dei valori nell'entità State. Vedere [attributi basati su dominio](http://msdn.microsoft.com/library/ff487058.aspx) per altri dettagli.  
  
 Una gerarchia derivata in MDS deriva dalla relazione tra attributi basati su dominio nel modello. In questa esercitazione viene creata una gerarchia derivata tra l'entità Supplier e l'entità State. Dopo aver creato la gerarchia derivata, verrà visualizzato un elenco di stati nel visualizzatore di Gestione dati master. Quando si fa clic su uno stato nell'elenco, vengono visualizzati i fornitori nello stato in questione nel riquadro destro. Successivamente, verrà creata una gerarchia derivata basata su questa relazione. Vedere [gerarchie derivate](http://msdn.microsoft.com/library/ee633747.aspx) per altri dettagli.  
  
 È stata compilata una Knowledge Base in DQS che è stata utilizzata per la pulizia e la corrispondenza dei dati fornitore e i risultati sono stati archiviati nel file Cleansed and Matched Supplier Data.xls. In questa lezione i dati puliti e corrispondenti vengono caricati in MDS. In DQS sono contenute solo le informazioni sui dati (metadati), mentre i dati stessi (set master) vengono archiviati da MDS. Ad esempio, è possibile che in DQS siano disponibili informazioni su diversi fornitori, ma in MDS vengono gestiti solo i fornitori utilizzati da una società.  
  
 In questa lezione vengono effettuate le attività seguenti:  
  
1.  Creare il **Suppliers** modello nella **MDS** tramite il **applicazione Web gestione dati Master**.  
  
2.  Aprire **Cleansed and Matched Supplier Data. xls** in Excel e usare i **il componente aggiuntivo MDS per Excel** per creare un'entità denominata **fornitore** e caricare i dati in MDS.  
  
3.  Verificare che i dati vengono creati in MDS utilizzando il **gestione dati Master**.  
  
4.  Creare un'entità denominata **stato** e aggiornare il **stato** attributo del **fornitore** entità che deve essere un attributo basato su dominio in base il **stato** entità. Eseguire queste operazioni, utilizzare il **il componente aggiuntivo MDS per Excel**.  
  
5.  Verificare che l'attributo basato su dominio viene creato usando **gestione dati Master** e aggiornare i valori per il **nome** attributo del **stato** entità.  
  
6.  Visualizzare gli aggiornamenti eseguiti tramite **gestione dati Master** in **Excel**.  
  
7.  Caricare i valori dal **stato** entità in **Excel** e aggiungere un valore e verificare l'aggiunta mediante **gestione dati Master**.  
  
8.  Creare e utilizzare una gerarchia derivata utilizzando la relazione tra attributi basati su dominio tra il **fornitore** entità e il **stato** entità (l'attributo State dell'entità Supplier è di tipo entità State ) usando **gestione dati Master**.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 1: Creazione del modello Supplier tramite Gestione dati Master](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  