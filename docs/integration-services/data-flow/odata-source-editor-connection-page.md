---
title: "Editor origine OData (pagina Connessione) | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.odatasource.connection.f1"
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Editor origine OData (pagina Connessione)
  Usare la pagina **Connessione** della finestra di dialogo **Editor origine OData** per selezionare la gestione connessione OData per l'origine OData. In questa pagina è inoltre possibile specificare una raccolta o un percorso della risorsa, nonché tutte le opzioni query per scegliere i dati che devono essere recuperati dall'origine OData. Per altre informazioni sull'origine OData, vedere [Origine OData](../../integration-services/data-flow/odata-source.md).  
  
## Opzioni statiche  
 **Gestione connessione OData**  
 Selezionare una gestione connessione esistente nell'elenco o crearne una nuova facendo clic su **Nuova**.  
  
 Dopo aver selezionato o creato una gestione connessione, la finestra di dialogo mostra la versione del protocollo OData che la gestione connessione sta usando.  
  
 **Nuova**  
 Creare una nuova gestione connessione usando la finestra di dialogo **Editor gestione connessione OData**.  
  
 **Usa percorso risorsa o raccolta**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Opzione|Description|  
|------------|-----------------|  
|Collection|Recuperare i dati dall'origine OData utilizzando il nome di una raccolta.|  
|Percorso risorsa|Recuperare i dati dall'origine OData utilizzando un percorso della risorsa.|  
  
 **Opzioni query**  
 Specificare le opzioni per la query.  Ad esempio: $top=5  
  
 **URL feed**  
 Viene visualizzato l'URL del feed di dati di sola lettura in base alle opzioni selezionate nella finestra di dialogo.  
  
 **Anteprima**  
 Vengono visualizzati in anteprima i risultati tramite la finestra di dialogo **Anteprima**. L'**anteprima** supporta la visualizzazione di un massimo di 20 righe.  
  
## Opzioni dinamiche  
  
### Usa percorso risorsa o raccolta = Raccolta  
 **Collection**  
 Selezionare una raccolta dall'elenco a discesa.  
  
### Usa percorso risorsa o raccolta = Percorso risorsa  
 **Percorso risorsa**  
 Digitare un percorso della risorsa. Ad esempio: Dipendenti  
  
## Vedere anche  
 [Editor origine OData &#40;pagina Colonne&#41;](../../integration-services/data-flow/odata-source-editor-columns-page.md)   
 [Editor origine OData &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/odata-source-editor-error-output-page.md)   
 [Gestione connessione OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  