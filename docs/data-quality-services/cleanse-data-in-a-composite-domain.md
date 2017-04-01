---
title: "Pulire i dati in un dominio composito | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d1076e0-7710-469a-9107-e293e4bd80ac
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# Pulire i dati in un dominio composito
  In questo argomento vengono fornite informazioni sulla pulizia dei domini compositi in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Un dominio composito è costituito da due o più singoli domini di cui viene eseguito il mapping a un campo dati costituito da più termini correlati. I singoli domini in un dominio composito devono contenere un'area delle informazioni in comune. Per informazioni dettagliate sui domini compositi, vedere [Managing a Composite Domain](../data-quality-services/managing-a-composite-domain.md).  
  
##  <a name="Mapping"></a> Esecuzione del mapping di un dominio composito ai dati di origine  
 Sono disponibili due modalità per eseguire il mapping dei dati di origine a un dominio composito:  
  
-   Dati di origine costituiti da un singolo campo, ad esempio Nome e cognome, di cui viene eseguito il mapping a un dominio composito.  
  
    -   Se il mapping del dominio composito viene eseguito a un servizio dati di riferimento, i dati di origine verranno inviati così come sono al servizio dati di riferimento per la correzione e l'analisi.  
  
    -   Se il mapping del dominio composito non viene eseguito a un servizio dati di riferimento, i dati di origine verranno analizzati in base al metodo di analisi definito per il dominio composito. Per ulteriori informazioni sulla specifica di un metodo di analisi per i domini compositi, vedere [Create a Composite Domain](../data-quality-services/create-a-composite-domain.md).  
  
-   Dati di origine costituiti da più campi, ad esempio Nome, Secondo nome e Cognome, di cui viene eseguito il mapping ai singoli domini all'interno di un dominio composito.  
  
 Per un esempio di come eseguire il mapping di domini compositi ai dati di origine, vedere [collegare dominio o dominio composito ai dati di riferimento](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md).  
  
##  <a name="CDCorrection"></a> Correzione dei dati mediante le regole definitive tra domini  
 Le regole tra domini in un dominio composito consentono di creare regole che indicano la relazione tra i singoli domini in un dominio composito. Le regole tra domini vengono prese in considerazione quando si esegue l'attività di pulizia sui dati di origine relativi ai domini compositi. Oltre a indicare si conosce la validità di una regola tra domini, definitivo *quindi* regola tra domini, **valore è uguale a**, corregge anche i dati durante l'attività di pulizia dei dati.  
  
 Considerare l'esempio seguente. Si supponga di avere un dominio composito, Product, con tre singoli domini: ProductName, CompanyName e ProductVersion. Creare la regola definitiva tra domini seguente:  
  
 Se il valore ‘CompanyName’ del dominio contiene *Microsoft* e il valore ‘ProductName’ del dominio è uguale a *Office* e il valore ‘ProductVersion’ è uguale a *2010* THEN il valore ‘ProductName’ del dominio è uguale a *Microsoft Office 2010*.  
  
 Quando questa regola tra domini viene eseguita, i dati di origine (ProductName) verranno corretti come segue dopo l'attività di pulizia:  
  
 **Origine dati**  
  
|ProductName|CompanyName|ProductVersion|  
|-----------------|-----------------|--------------------|  
|Office|Microsoft Inc.|2010|  
  
 **Dati di output**  
  
|ProductName|CompanyName|ProductVersion|  
|-----------------|-----------------|--------------------|  
|Microsoft Office 2010|Microsoft Inc.|2010|  
  
 Quando si testa il definitivo *quindi* regola tra domini, **valore è uguale a**,  **Test regola dominio composito** la finestra di dialogo contiene una nuova colonna, **Correggi in**, che consente di visualizzare i dati corretti. In un progetto DQS, questa regola definitiva tra domini modifica i dati con 100% e **motivo** colonna Visualizza il messaggio seguente: corretto dalla regola '*\< nome della regola tra domini >*'. Per ulteriori informazioni sulle regole tra domini, vedere [creare una regola tra domini](../data-quality-services/create-a-cross-domain-rule.md).  
  
> [!NOTE]  
>  La regola definitiva tra domini non funziona per i domini compositi associati al servizio dati di riferimento.  
  
##  <a name="DataProfiling"></a> Profiling dei dati per i domini compositi  
 Profiling DQS fornisce due dimensioni della qualità dei dati: *completezza* (l'entità a cui sono presenti dati) e *accuratezza* (l'entità cui dati possono essere utilizzati per gli scopi previsti) durante l'attività di pulizia. È possibile che il profiling non fornisca statistiche di completezza affidabili per i domini compositi. Se sono necessarie statistiche di completezza, utilizzare domini singoli anziché domini compositi. Se si desidera utilizzare domini compositi, è consigliabile creare una Knowledge Base con domini singoli di cui eseguire il profiling per determinare la completezza, quindi creare un altro dominio con un dominio composito per l'attività di pulizia. Ad esempio, il profiling potrebbe mostrare una completezza del 95% per record relativi a indirizzi, utilizzando un dominio composito, ma potrebbe esservi un livello di incompletezza molto più alto per una delle colonne, ad esempio una colonna relativa al codice postale (CAP). In questo esempio, è necessario misurare la completezza della colonna del CAP con un solo dominio.  
  
 Il profiling fornirà probabilmente statistiche di accuratezza affidabili per i domini compositi perché è possibile misurare l'accuratezza di più colonne allo stesso tempo. Il valore di questi dati sta nell'aggregazione composta, pertanto è consigliabile misurarne l'accuratezza con un dominio composito.  
  
 Per informazioni dettagliate sui dati di profilatura durante l'attività di pulizia, vedere [statistiche del Profiler](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md#Profiler) in [pulire i dati tramite DQS & #40; interno & #41; Knowledge Base](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md).  
  
  