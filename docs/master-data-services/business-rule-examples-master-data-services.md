---
title: Esempi di regole di business (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 01/05/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 3974b9be-4b7c-4a37-ab26-1a36ef455744
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4eca1a4ebb1c8b943709fba4b96e5bda96ab7747
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637719"
---
# <a name="business-rule-examples-master-data-services"></a>Esempi di regole di business (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo vengono illustrati esempi di regole di business per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Questi esempi sono disponibili nei modelli di esempio inclusi nell'installazione di [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].   
  
Per istruzioni su come distribuire i modelli di esempio, vedere [Installazione e configurazione di Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md).  
  
  
## <a name="business-rule-examples"></a>Esempi di regole di business  
Modello di esempio |Entità  |Nome della regola di business| Descrizione  
---------|---------|---------|-----------|  
Customer    | Customer   | Person pmt terms| Specifica le condizioni di pagamento predefinite per i clienti.          
Nella regola di business seguente, se il valore dell'attributo CustomerType soddisfa la `is equal` [rule condition](../master-data-services/business-rule-conditions-master-data-services.md), then the `defaults to` [rule action](../master-data-services/business-rule-conditions-master-data-services.md) is applied to the PaymentTerms attribute. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    CustomerType is equal to 2  
Then  
    PaymentTerms defaults to CASH  
Else  
    None      
```  
  
**--------------------------------------------------**  
  
Modello di esempio  |Entità  |Nome della regola di business|Descrizione    
---------|---------|---------|---------------  
Customer     | Customer    | Org pmt terms | Specifica le condizioni di pagamento predefinite per le organizzazioni.         
Nella regola di business seguente, se il valore dell'attributo CustomerType soddisfa la `is equal` [rule condition](../master-data-services/business-rule-conditions-master-data-services.md), then the `defaults to` [rule action](../master-data-services/business-rule-actions-master-data-services.md) is applied to the PaymentTerms attribute. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    CustomerType is equal to 1  
Then  
    PaymentTerms defaults to 210Net30  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business| Descrizione    
---------|---------|---------|-----------  
Prodotto     |  Prodotto       | DaysToManufacture |Specifica l'intervallo di giorni alla produzione per la produzione interna.          
Nella regola di business seguente, se il valore dell'attributo InHouseManufacture soddisfa la `is equal` [rule condition](../master-data-services/business-rule-conditions-master-data-services.md), then the `must be between` [rule action](../master-data-services/business-rule-actions-master-data-services.md) is applied to the DaysToManufacture attribute. In caso contrario, non viene eseguita alcuna azione.  
```  
If  
    InHouseManufacture is equal to Y  
Then  
    DaysToManufacture must be between 1 and 10  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Descrizione    
---------|---------|---------|-------------  
Prodotto     |Product         |Required fields| Specifica gli attributi obbligatori per i membri dell'entità Product.           
Nella regola di business seguente, l' `is required` [validation action](../master-data-services/business-rule-actions-master-data-services.md) is taken for the specified attributes. I valori di attributo non possono essere Null o vuoti.  
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
  
  
Modello di esempio  |Entità  |Nome della regola di business|Descrizione    
---------|---------|---------|-----------  
Prodotto     | Prodotto        |  Std Cost| Richiede che il costo standard sia maggiore di 0.        
Nella regola di business seguente, l' `must be greater than` [rule action](../master-data-services/business-rule-actions-master-data-services.md) is applied to the StandardCost attribute of products.  
```  
If  
    None  
Then  
    StandardCost must be greater than 0  
Else  
    None  
```  
  
**--------------------------------------------------**  
  
  
Modello di esempio  |Entità  |Nome della regola di business|Descrizione    
---------|---------|---------|------------  
Prodotto     | Prodotto        | FG MSRP Cost|Specifica che se il prodotto è un prodotto finito, il prezzo consigliato e il prezzo del rivenditore devono essere maggiori di 0.           
  
Nella regola di business seguente, se il valore dell'attributo FinishedGoodIndicator soddisfa la `is equal` [rule condition](../master-data-services/business-rule-conditions-master-data-services.md), the `must be greater than` [rule action](../master-data-services/business-rule-actions-master-data-services.md) is applied to the MSRP and DealerCost attributes.  
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
  
  
Modello di esempio  |Entità  |Nome della regola di business|Descrizione    
---------|---------|---------|------------  
Prodotto     | Prodotto        |  Default Name| Specifica il nome di prodotto predefinito in base ai valori degli attributi Color e Class. Quando il valore dell'attributo Color non è YLO e l'attributo Class non è NA, il nome predefinito è Yellow NA.         
Nella regola di business seguente, se gli attributi Color e Class non soddisfano la condizione della regola `is equal` , viene applicata l' `defaults to` [rule action](../master-data-services/business-rule-actions-master-data-services.md) is applied to the Name attribute.  
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
1. Passare al sito Web [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] configurato dopo aver installato MDS e fare clic sulla casella **Amministrazione sistema** .   
Per istruzioni sulla configurazione del sito Web, vedere [Installazione e configurazione di Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md).  
2. Fare clic sul modello di esempio contenente la regola di business, come indicato nelle tabelle precedenti, quindi fare clic su **Entità**.  
3. Fare clic sull'entità a cui si applica la regola, come indicato nelle tabelle precedenti, quindi fare clic su **Regole di business**.  
4. Fare clic sul nome della regola di business che si vuole visualizzare. L'interfaccia utente viene espansa per visualizzare le istruzioni **If**, **Then** ed **Else** .  
  
 
  
  
  
  

