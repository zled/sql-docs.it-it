---
title: Comando pulsanti di Address Book | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
caps.latest.revision: "16"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 878878f11c6d1083d261e592a57a6b28ae793b56
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="address-book-command-buttons"></a>Pulsanti di Address Book comando
L'applicazione Address Book include i pulsanti di comando seguenti:  
  
-   Oggetto **trovare** pulsante per inviare una query al database.  
  
-   Oggetto **deselezionare** pulsante per deselezionare le caselle di testo prima di avviare una nuova ricerca.  
  
-   Un **Update Profile** pulsante per salvare le modifiche a un record dipendente.  
  
-   Oggetto **Cancel Changes** pulsante per annullare le modifiche.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Pulsante Trova  
 Fare clic su di **trovare** pulsante Attiva Find_OnClick routine Sub di VBScript, che crea e invia la query SQL. Fare clic su questo pulsante consente di popolare la griglia dei dati.  
  
## <a name="building-the-sql-query"></a>La creazione della Query SQL  
 La prima parte della routine Sub Find_OnClick compila la query SQL, una frase contemporaneamente, mediante l'aggiunta di stringhe di testo a un'istruzione SQL SELECT globale. Impostando la variabile `myQuery` a un'istruzione SQL SELECT che richiede tutte le righe di dati dalla tabella di origine dati. Successivamente, la routine Sub analizza ognuna delle quattro caselle di input nella pagina.  
  
 Poiché il programma utilizza la parola `like` nella creazione delle istruzioni SQL, le query sono ricerche delle sottostringhe piuttosto che corrispondenze esatte.  
  
 Ad esempio, se il **cognome** casella conteneva la voce "Berge" e **titolo** casella conteneva la voce "Program Manager", l'istruzione SQL (valore di `myQuery`) leggerà:  
  
```  
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 Se la query ha esito positivo, tutte le persone con un cognome che contiene il testo "Berge" (ad esempio Berge e Berger) e con un titolo che includono le parole "Program Manager" (ad esempio, Program Manager, le tecnologie avanzate) vengono visualizzate nella griglia dei dati HTML.  
  
## <a name="preparing-and-sending-the-query"></a>La preparazione e l'invio di Query  
 L'ultima parte della routine Sub Find_OnClick è costituita da due istruzioni. La prima istruzione assegna il [SQL](../../../ado/reference/rds-api/sql-property.md) proprietà del [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto uguale alla query di SQL compilata in modo dinamico. La seconda istruzione determina la **RDS. DataControl** oggetto (`DC1`) per eseguire query sul database e quindi visualizzare i nuovi risultati della query nella griglia.  
  
```  
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Pulsante di aggiornamento del profilo  
 Fare clic su di **Update Profile** pulsante Attiva Update_OnClick routine Sub di VBScript, che esegue il [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) e [aggiornamento](../../../ado/reference/rds-api/refresh-method-rds.md) metodi.  
  
```  
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Quando `DC1.SubmitChanges` viene eseguito, il servizio dati remoto tutte le informazioni sull'aggiornamento dei pacchetti e lo invia al server tramite HTTP. L'aggiornamento è radicale; Se una parte dell'aggiornamento ha esito negativo, nessuna delle modifiche viene eseguita e viene restituito un messaggio di stato. `DC1.Refresh`non è necessario dopo **SubmitChanges** con Remote Data Service, ma garantisce dati aggiornati.  
  
## <a name="cancel-changes-button"></a>Pulsante di annullamento delle modifiche  
 Fare clic su **Cancel Changes** di VBScript routine Sub Cancel_OnClick, che esegue il [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto (`DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) metodo.  
  
```  
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Quando `DC1.CancelUpdate` esegue, Elimina tutte le modifiche apportate dall'utente a un record dipendente nella griglia di dati dall'ultima query o aggiornamento. Ripristina i valori originali.  
  
## <a name="see-also"></a>Vedere anche  
 [Pulsanti di spostamento della Rubrica di indirizzi](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


