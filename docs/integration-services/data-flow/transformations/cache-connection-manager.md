---
title: "Gestione connessione della cache | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestione connessione della cache"
ms.assetid: bdc92038-3720-4795-8a5c-79b963f2c952
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Gestione connessione della cache
  La gestione connessione della cache consente di leggere i dati dalla trasformazione cache o da un file di cache (con estensione caw) e di salvarli in un file di cache. Se si configura la gestione connessione della cache in modo da utilizzare un file di cache, i dati sono archiviati sempre in memoria.  
  
 La trasformazione Trasformazione cache consente di scrivere i dati da un'origine dati connessa nel flusso di dati a una gestione connessione della cache. La trasformazione Ricerca in un pacchetto consente di effettuare ricerche nei dati.  
  
> [!NOTE]  
>  I tipi di dati BLOB (oggetto binario di grandi dimensioni), ovvero DT_TEXT, DT_NTEXT e DT_IMAGE, non sono supportati nella Gestione connessione cache. Se il set di dati di riferimento contiene un tipo di dati BLOB, il componente avrà esito negativo quando viene eseguito il pacchetto. È possibile utilizzare **Editor gestione connessione cache** per modificare i tipi di dati di colonna. Per altre informazioni, vedere [Editor gestione connessione cache](../../../integration-services/data-flow/transformations/cache-connection-manager-editor.md).  
  
> [!NOTE]  
>  Il livello di protezione del pacchetto non si applica al file di cache. Se il file di cache contiene informazioni riservate, utilizzare un elenco di controllo di accesso (ACL) per limitare l'accesso al percorso o alla cartella nella quale verrà archiviato il file. È consigliabile consentire l'accesso solo a determinati account. Per altre informazioni, vedere [Accesso ai file utilizzati dai pacchetti](../../../integration-services/security/access-to-files-used-by-packages.md).  
  
## Configurazione della gestione connessione cache  
 Per configurare la gestione connessione cache, procedere nel modo seguente:  
  
-   Indicare se utilizzare un file di cache.  
  
     Se la gestione connessione della cache viene configurata in modo da utilizzare un file di cache, la gestione connessione eseguirà una delle seguenti azioni:  
  
    -   Salvare i dati in un file quando la trasformazione Cache viene configurata in modo da scrivere i dati da un'origine dati nel flusso di dati alla gestione connessione della cache.  
  
    -   Leggere i dati dal file di cache.  
  
     Per ulteriori informazioni, vedere [Cache Transform](../../../integration-services/data-flow/transformations/cache-transform.md).  
  
-   Modificare i metadati per le colonne archiviate nella cache.  
  
-   Aggiornare il nome del file di cache in fase di esecuzione usando un'espressione per impostare la proprietà ConnectionString. Per altre informazioni, vedere [Utilizzo delle espressioni di proprietà nei pacchetti](../../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], vedere [Editor gestione connessione cache](../../../integration-services/data-flow/transformations/cache-connection-manager-editor.md).  
  
 Per informazioni su come configurare una gestione connessione a livello di programmazione, vedere <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Aggiunta di connessioni a livello di programmazione](../../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Attività correlate  
 [Implementazione di una trasformazione Ricerca in modalità Full Cache utilizzando la gestione connessione della cache](../../../integration-services/data-flow/transformations/lookup transformation full cache mode - cache connection manager.md)  
  
  