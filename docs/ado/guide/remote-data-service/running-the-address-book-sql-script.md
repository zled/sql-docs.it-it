---
title: Eseguire lo Script SQL di libro indirizzo | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4751361a50f4fe594ad4ffc9d4233b41a4918361
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="running-the-address-book-sql-script"></a>Eseguire lo Script SQL libro di indirizzo
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 È necessario utilizzare l'utilità della riga di comando ISQL/Query Analyzer o SQL Server Enterprise Manager per eseguire lo script SQL incluso (Sampleemp.sql) che:  
  
-   Crea un nuovo database, AddrBookDB, sul dispositivo predefinito.  
  
-   Si connette al database, AddrBookDB.  
  
-   Crea una tabella Employee.  
  
-   Popola la tabella con dati di esempio.  
  
-   Esegue un'istruzione SELECT semplice per verificare il popolamento della tabella di database.  
  
-   Consente di impostare un account utente denominato "adcdemo" con la password "adcdemo".  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-65"></a>Per eseguire lo script Sampleemp.sql in Microsoft SQL Server 6.5  
  
1.  Fare clic su **avviare**, scegliere **programmi**e quindi **Microsoft SQL Server 6.5**. Fare clic su **SQL Enterprise Manager**.  
  
2.  Dal **strumenti** menu, fare clic su **strumento Query SQL**.  
  
3.  Fare clic su **carica Script SQL** e passare a c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
4.  Selezionare il file Sampleemp.sql. Fare clic su **Apri**.  
  
5.  Fare clic su di **Esegui Query** (la freccia verde sulla barra degli strumenti).  
  
6.  Dopo l'esecuzione, chiudere il **Query** e **Enterprise Manager** windows.  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-70"></a>Per eseguire lo script Sampleemp.sql in Microsoft SQL Server 7.0  
  
1.  Fare clic su **avviare**, scegliere **programmi**e quindi **Microsoft SQL Server 7.0**. Fare clic su **Enterprise Manager**.  
  
2.  Assicurarsi che il Server SQL che si desidera utilizzare sia selezionato dall'elenco dei server registrati in Enterprise Manager.  
  
3.  Dal **strumenti** menu, fare clic su **Query Analyzer di SQL Server**.  
  
4.  Fare clic su di **carica Script SQL** pulsante (vale a dire la cartella aperta sulla barra degli strumenti) e accedere a c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.  
  
5.  Selezionare il file Sampleemp.sql. Fare clic su **Apri**.  
  
6.  Fare clic su di **Esegui Query** (la freccia verde sulla barra degli strumenti) o **F5**.  
  
7.  Dopo l'esecuzione, chiudere il **Query**, **Query Analyzer**, e **Enterprise Manager** windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione dell'applicazione di esempio Address Book](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)



