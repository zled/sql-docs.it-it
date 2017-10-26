---
title: Mapping di parametri di Query a variabili in un componente del flusso di dati | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da9367a56cefbb37244d4a47543b93586e7e8870
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Mapping dei parametri di query a variabili in un componente del flusso di dati
  Quando viene configurata l'origine OLE DB per utilizzare query con parametri, è possibile eseguire il mapping dei parametri alle variabili.  
  
 L'origine OLE DB utilizza query con parametri per filtrare i dati quando l'origine si collega a un'origine dati.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Per eseguire il mapping di un parametro di query a una variabile  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi dalla **Casella degli strumenti**trascinare l'origine OLE DB sull'area di progettazione.  
  
4.  Fare clic con il pulsante destro del mouse sull'origine OLE DB e quindi scegliere **Modifica**.  
  
5.  In **Editor origine OLE DB**, selezionare la gestione connessione OLE DB da usare per la connessione all'origine dei dati oppure fare clic su **Nuova** per creare una nuova gestione connessione OLE DB.  
  
6.  Selezionare l'opzione **Comando SQL** per la modalità di accesso ai dati e quindi immettere una query con parametri nella casella **Testo comando SQL** .  
  
7.  Fare clic su **Parametri**.  
  
8.  Nel **imposta parametri Query** finestra di dialogo casella, eseguire il mapping di ogni parametro nel **parametri** elenco a una variabile nel **variabili** elenco o creare una nuova variabile facendo  **\<nuova variabile >**. Scegliere **OK**.  
  
    > [!NOTE]  
    >  Sono disponibili per il mapping solo le variabili di sistema e le variabili definite dall'utente nell'ambito del pacchetto, di un contenitore padre quale Ciclo Foreach o dell'attività Flusso di dati che contiene il componente del flusso di dati. La variabile deve avere un tipo di dati compatibile con la colonna nella clausola WHERE a cui è assegnato il parametro.  
  
9. Facendo clic su **Anteprima** è possibile visualizzare fino a 200 righe di dati restituiti dalla query.  
  
10. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Origine OLE DB](../../integration-services/data-flow/ole-db-source.md)   
 [Trasformazione ricerca](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  

