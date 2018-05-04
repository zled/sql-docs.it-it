---
title: Scelta dei dati di un'origine o il Driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], selecting driver
- connecting to data source [ODBC], selecting data source
- data sources [ODBC], selecting
- ODBC drivers [ODBC], selecting
ms.assetid: 10aaf570-01ab-4478-8339-bdde2a5e3dd1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ea84e234291056901c9d759e9aa206301a24641
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="choosing-a-data-source-or-driver"></a>Scelta dei dati di un Driver o origine
L'origine dati o il driver utilizzato da un'applicazione è a volte hardcoded nell'applicazione. Ad esempio, un'applicazione personalizzata programmata dal dipartimento MIS per trasferire dati da un'origine dati a un'altra contiene i nomi di tali origini dati, ovvero semplicemente l'applicazione non funziona con tutte le altre origini dati. Un altro esempio è un'applicazione verticale, ad esempio un oggetto utilizzato per l'inserimento dell'ordine. Tale applicazione sempre utilizza la stessa origine dati, che ha uno schema predefinito noto dall'applicazione.  
  
 Altre applicazioni selezionare l'origine dati o i driver in fase di esecuzione. In genere, queste sono applicazioni generiche eseguire query ad hoc, ad esempio un foglio di calcolo che utilizza ODBC per importare i dati. Tali applicazioni, in genere, elencare le origini dati disponibili o i driver e consentono agli utenti di scegliere quelli a cui che si desidera utilizzare. Se un'applicazione generica sono elencate le origini dati, il driver o entrambi spesso varia a seconda che l'applicazione utilizzi driver basati su DBMS o basata su file.  
  
 Driver basati su DBMS richiedono in genere un set complesso di informazioni di connessione, ad esempio l'indirizzo di rete, il protocollo di rete, nome del database e così via. Lo scopo di un'origine dati è nascondere tutte queste informazioni. Pertanto, il paradigma di origine dati si presta da utilizzare con i driver basati su DBMS. Un'applicazione può visualizzare un elenco di origini dati per l'utente in uno dei due modi. È possibile chiamare **SQLDriverConnect** con il **DSN** (parola chiave) (nome dell'origine dati) e nessun valore associato; the Driver Manager verrà visualizzato un elenco di nomi di origine dati. Se l'applicazione deve controllare l'aspetto dell'elenco, chiama **SQLDataSources** per recuperare un elenco di disponibili origini dati e crea una finestra di dialogo. Questa funzione è implementata da Gestione Driver e può essere chiamata prima che vengano caricati i driver. Quindi, l'applicazione chiama una funzione di connessione e passa il nome dell'origine dati scelto.  
  
 Se un'origine dati non è specificata, viene utilizzata l'origine dati predefinito indicato dalle informazioni sul sistema. (Per ulteriori informazioni, vedere [predefinito sottochiave](../../../odbc/reference/install/default-subkey.md).) Se **SQLConnect** viene chiamato utilizzando un *ServerName* argomento che non è stato trovato, è un puntatore null o è "DEFAULT", gestione Driver si connette all'origine dati predefinito. Il valore predefinito di origine dati viene utilizzata anche se la stringa di connessione viene utilizzato in una chiamata a **SQLDriverConnect** o **SQLBrowseConnect** contiene il **DSN** (parola chiave) impostata su "DEFAULT "o se l'origine dati specificata non viene trovato. Inoltre, l'impostazione predefinita l'origine dati viene utilizzata se la stringa di connessione è utilizzata in una chiamata a **SQLDriverConnect** non contiene il **DSN** (parola chiave).  
  
 Con i driver basati su file, è possibile utilizzare un paradigma di file. Per i dati archiviati nel computer locale, gli utenti spesso sappiano che i dati in un determinato file, ad esempio Employee. dbf. Anziché selezionare un'origine dati sconosciuti, è più semplice per tali utenti di selezionare il file che già conoscono. Per implementare questa operazione, l'applicazione chiama prima **SQLDrivers**. Questa funzione è implementata da Gestione Driver e può essere chiamata prima che vengano caricati i driver. **SQLDrivers** restituisce un elenco dei driver disponibili; restituisce inoltre i valori per il **FileUsage** e **FileExtns** parole chiave. Il **FileUsage** (parola chiave) viene fatto driver basati su file considerati file come tabelle, non Xbase o come database, nell'effettua Microsoft® Access. Il **FileExtns** (parola chiave) Elenca le estensioni di nome file, ad esempio con estensione dbf per ottenere un driver Xbase il driver riconosce. Utilizza queste informazioni, l'applicazione crea una finestra di dialogo tramite il quale l'utente sceglie un file. In base all'estensione di file scelto, quindi l'applicazione si connette al driver chiamando **SQLDriverConnect** con il **DRIVER** (parola chiave).  
  
 Non è necessario arrestare un'applicazione da utilizzare un'origine dati con un driver basati su file o di chiamare **SQLDriverConnect** con il **DRIVER** (parola chiave) per connettersi a un driver basati su DBMS. Ecco alcuni usi comuni del **DRIVER** (parola chiave) per i driver basati su DBMS:  
  
-   **Non creare origini dati.** Ad esempio, un'applicazione personalizzata potrebbe utilizzare un driver specifico e un database. Se il nome del driver e tutte le informazioni necessarie per connettersi al database è hardcoded nell'applicazione, gli utenti non debbano creare un'origine dati nel proprio computer per eseguire l'applicazione. È necessario completare è installare l'applicazione e i driver.  
  
     Uno svantaggio di questo metodo è che l'applicazione deve essere ricompilata e ridistribuita se le informazioni di connessione viene modificata. Se un nome origine dati è hardcoded nell'applicazione anziché le informazioni di connessione completa, ogni utente deve modificare solo le informazioni nell'origine dati.  
  
-   **L'accesso a un determinato DBMS una sola volta.** Ad esempio, in cui potrebbe contenere un foglio di calcolo che recupera i dati mediante la chiamata di funzioni ODBC il **DRIVER** (parola chiave) per identificare un driver specifico. Poiché il nome del driver è significativo per tutti gli utenti che dispongono di tale driver, è possibile passare il foglio di calcolo per gli utenti. Se il foglio di calcolo contiene un nome origine dati, ogni utente deve creare la stessa origine dati per l'utilizzo del foglio di calcolo.  
  
-   **Esplorazione del sistema per tutti i database accessibili a un driver specifico.** Per ulteriori informazioni, vedere [connessione con SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md), più avanti in questa sezione.
