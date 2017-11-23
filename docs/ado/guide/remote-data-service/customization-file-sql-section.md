---
title: Sezione relativa alla personalizzazione File SQL | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e596d2c1ae90e86931e5656ac7ccdbdeb95e4d5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="customization-file-sql-section"></a>Sezione relativa alla personalizzazione File SQL
Il **sql** sezione può contenere una nuova stringa SQL che sostituisce la stringa di comando del client. Se non è presente alcuna stringa SQL nella sezione, la sezione verrà ignorata.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 La nuova stringa SQL potrebbe essere *con parametri*. Ovvero, i parametri nel **sql** sezione stringa SQL (designato dal '?' caratteri) possono essere sostituiti dagli argomenti corrispondenti in un *identificatore* nella stringa di comando di client (designato da un elenco delimitato da parentesi). L'identificatore e un elenco di argomenti si comportano come una chiamata di funzione.  
  
 Si supponga ad esempio la stringa di comando del client è `"CustomerByID(4)"`, l'intestazione di sezione SQL è `[SQL CustomerByID]`, e la nuova stringa sezione SQL `"SELECT * FROM Customers WHERE CustomerID = ?".` genererà il gestore del `"SELECT * FROM Customers WHERE CustomerID = 4"` e utilizzare tale stringa per eseguire query sull'origine dati.  
  
 Se la nuova istruzione SQL è la stringa null (""), la sezione verrà ignorato.  
  
 Se la nuova stringa di istruzione SQL non è valida, l'esecuzione dell'istruzione avrà esito negativo. Il parametro di client in modo efficace viene ignorato. È possibile farlo intenzionalmente per "disattivare" tutti i comandi SQL client specificando:  
  
```  
[SQL default]   
SQL = " "  
```  
  
## <a name="syntax"></a>Sintassi  
 Sostituzione di stringa SQL è nel formato:  
  
 **SQL =**   
 ***sqlString***  
  
|Parte|Description|  
|----------|-----------------|  
|**SQL**|Una stringa letterale che indica che si è una voce della sezione SQL.|  
|***sqlString***|Una stringa SQL che sostituisce la stringa di client.|  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare il File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione Log File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione UserList File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sui File di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


