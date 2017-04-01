---
title: "Esempi di regole di business (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "01/05/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3974b9be-4b7c-4a37-ab26-1a36ef455744
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 19
---
# Esempi di regole di business (Master Data Services)
In questo articolo vengono illustrati esempi di regole di business per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Questi esempi sono disponibili nei modelli di esempio inclusi nell'installazione di [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].   
  
Per istruzioni su come distribuire i modelli di esempio, vedere [Master Data Services](../sql-server/media/master-data-services.png#deploySample).  
  
  
## Esempi di regole di business  
Modello di esempio |Entità  |Nome della regola di business| Description  
---------|---------|---------|-----------|  
Customer    | Customer   | Person pmt terms| Specifica le condizioni di pagamento predefinite per i clienti.          
Nella regola di business seguente, se il valore dell'attributo CustomerType soddisfa la [condizione della regola](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, viene applicata l'[azione della regola](../master-data-services/business-rule-conditions-master-data-services.md) `defaults to` all'attributo PaymentTerms. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    CustomerType is equal to 2  
Then  
    PaymentTerms defaults to CASH  
Else  
    None      
```  
  
**--------------------------------------------------**  
  
Modello di esempio  |Entità  |Nome della regola di business|Description    
---------|---------|---------|---------------  
Customer     | Customer    | Org pmt terms | Specifica le condizioni di pagamento predefinite per le organizzazioni.         
Nella regola di business seguente, se il valore dell'attributo CustomerType soddisfa la [condizione della regola](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, viene applicata l'[azione della regola](../master-data-services/business-rule-actions-master-data-services.md) `defaults to` all'attributo PaymentTerms. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    CustomerType is equal to 1  
Then  
    PaymentTerms defaults to 210Net30  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business| Description    
---------|---------|---------|-----------  
Product     |  Product       | DaysToManufacture |Specifica l'intervallo di giorni alla produzione per la produzione interna.          
Nella regola di business seguente, se il valore dell'attributo InHouseManufacture soddisfa la [condizione della regola](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, viene applicata l'[azione della regola](../master-data-services/business-rule-actions-master-data-services.md) `must be between` all'attributo DaysToManufacture. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    InHouseManufacture is equal to Y  
Then  
    DaysToManufacture must be between 1 and 10  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Description    
---------|---------|---------|-------------  
Product     |Product         |Required fields| Specifica gli attributi obbligatori per i membri dell'entità Product.           
Nella regola di business seguente, l'[azione di convalida](../master-data-services/business-rule-actions-master-data-services.md) `is required` viene applicata in tutte le condizioni agli attributi specificati. I valori di attributo non possono essere Null o vuoti.  
```  
If  
    None  
Then  
    Name is required  
    ProductSubCategory is required  
    Color is required  
    StandardCost is required  
    SafetyStockLevel is required  
    ReorderPoint is required  
    InHouseManufacture is required  
    SellStartDate is required  
    FinishedGoodIndicator is required  
    ProductLine is required  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Description    
---------|---------|---------|-----------  
Product     | Product        |  Std Cost| Richiede che il costo standard sia maggiore di 0.        
Nella regola di business seguente, l'[azione della regola](../master-data-services/business-rule-actions-master-data-services.md) `must be greater than` viene applicata in tutte le condizioni all'attributo StandardCost dei prodotti.  
```  
If  
    None  
Then  
    StandardCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Description    
---------|---------|---------|------------  
Product     | Product        | FG MSRP Cost|Specifica che se il prodotto è un prodotto finito, il prezzo consigliato e il prezzo del rivenditore devono essere maggiori di 0.           
  
Nella regola di business seguente, se il valore dell'attributo FinishedGoodIndicator soddisfa la [condizione della regola](../master-data-services/business-rule-conditions-master-data-services.md) `is equal`, viene applicata l'[azione della regola](../master-data-services/business-rule-actions-master-data-services.md) `must be greater than` agli attributi MSRP e DealerCost.  
```  
If  
    FinishedGoodIndicator is equal to Y  
Then  
    MSRP must be greater than 0  
    DealerCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Description    
---------|---------|---------|------------  
Product     | Product        |  Default Name| Specifica il nome di prodotto predefinito in base ai valori degli attributi Color e Class. Quando il valore dell'attributo Color non è YLO e l'attributo Class non è NA, il nome predefinito è Yellow NA.         
Nella regola di business seguente, se gli attributi Color e Class non soddisfano la condizione della regola `is equal`, viene applicata l'[[azione della regola](../master-data-services/business-rule-actions-master-data-services.md)](Business%20Rule%20Conditions%20(Master%20Data%20Services).xml) `defaults to` all'attributo Name.  
```  
If  
    (Color is equal to YLO AND Class is equal to NA) is not true  
Then  
    Name defaults to Yellow NA  
Else  
    Name defaults to Other  
```  
  
**--------------------------------------------------**  
  
  
**Per visualizzare gli esempi delle regole di business nei modelli di esempio**  
1. Passare al sito Web [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] configurato dopo aver installato MDS e fare clic sulla casella **Amministrazione sistema**.   
Per istruzioni sulla configurazione del sito Web, vedere [Master Data Services](../sql-server/media/master-data-services.png).  
2. Fare clic sul modello di esempio contenente la regola di business, come indicato nelle tabelle precedenti, quindi fare clic su **Entità**.  
3. Fare clic sull'entità a cui si applica la regola, come indicato nelle tabelle precedenti, quindi fare clic su **Regole di business**.  
4. Fare clic sul nome della regola di business che si vuole visualizzare. L'interfaccia utente viene espansa per visualizzare le istruzioni **If**, **Then** ed **Else**.  
  
## Questo articolo è stato utile? Commenti e suggerimenti   
Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com)   
  
  
  
  
