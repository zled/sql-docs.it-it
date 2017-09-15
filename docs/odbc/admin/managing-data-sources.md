---
title: Gestione delle origini dati | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting data sources [ODBC], ODBC data source administrator
- data sources [ODBC], ODBC data source administrator
- adding data sources [ODBC], ODBC data source administrator
- removing data sources [ODBC], ODBC data source administrator
- ODBC data source administrator [ODBC], data source management
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d80594ac41f27d28051fc64f489b5cad59335c00
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="managing-data-sources"></a>Gestione delle origini dati
Dopo aver installato un driver ODBC dal programma di installazione del driver, è possibile definire una o più origini dati per tale. Il nome di origine dati (DSN) deve fornire una descrizione univoca dei dati. ad esempio, *retribuzioni* o *contabilità fornitori*. Le origini dati utente e di sistema definiti per tutti i driver attualmente installati sono elencate nel **DSN utente** o **DSN di sistema** schede del **amministratore di origine dati ODBC**la finestra di dialogo. Sono elencate le origini dati di file in una directory specificata nel **DSN su File** scheda; la directory da visualizzare viene immesso nel **Cerca in** casella il **DSN su File** scheda.  
  
> [!NOTE]  
>  Per gestire un'origine dati che si connette a un driver a 32 bit in piattaforme a 64 bit, utilizzare c:\windows\sysWOW64\odbcad32.exe. Per gestire un'origine dati che si connette a un driver a 64 bit, utilizzare c:\windows\system32\odbcad32.exe. In **strumenti di amministrazione** in un sistema operativo Windows 8 a 64 bit, sono presenti icone per il 32 bit e 64 bit **Amministrazione origine dati ODBC** la finestra di dialogo.  
  
 Se si utilizza il odbcad32.exe a 64 bit per configurare o rimuovere un DSN che si connette a un driver a 32 bit, ad esempio, **Driver do Microsoft Access (\*con estensione mdb)**, si riceverà il messaggio di errore seguente:  
  
```  
The specified DSN contains an architecture mismatch between the Driver and Application  
```  
  
 Per correggere l'errore, utilizzare il odbcad32.exe 32 bit per configurare o rimuovere il DSN.  
  
 Un'origine dati, un driver ODBC specifico associa i dati che si desidera accedere tramite il driver. Ad esempio, è possibile creare un'origine dati per utilizzare il driver ODBC dBASE per accedere a uno o più file dBASE in una directory sul disco rigido o un'unità di rete specifica. Utilizzare Amministrazione origine dati ODBC, è possibile aggiungere, modificare ed eliminare origini dati, come descritto nella tabella seguente.  
  
|Azione|Description|  
|------------|-----------------|  
|Aggiunta di origini dati|È possibile aggiungere più origini dati, ciascuno di essi l'associazione di un driver con alcuni dati a cui che si desidera accedere tramite il driver. Assegnare un nome che identifica in modo che l'origine dati di ogni origine dati. Ad esempio, se si crea un'origine dati per un set di file dBASE che contengono informazioni sul cliente, è possibile denominare l'origine dati "Customers". Le applicazioni in genere visualizzano i nomi di origine dati per gli utenti scelgano da.<br /><br /> Aggiunta di un'origine dati di file è leggermente diversa dall'aggiunta di origini dati di sistema o di utente. Per ulteriori informazioni, vedere l'amministratore dell'origine dati ODBC nel file della Guida.|  
|Modifica delle origini dati|A seconda dei requisiti, potrebbe essere necessario riconfigurare le origini dati. È possibile reimpostare le opzioni, fare clic su **configura** in qualsiasi finestra di dialogo programma di installazione di driver.|  
|Eliminazione di origini dati|Fare clic su **rimuovere** dopo aver selezionato un'origine dati.|  
  
 Per ulteriori informazioni sulle origini dati di file, vedere [connessione utilizzando le origini dati](../../odbc/reference/develop-app/connecting-using-file-data-sources.md) o [funzione SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione origine dati ODBC](../../odbc/admin/odbc-data-source-administrator.md)
