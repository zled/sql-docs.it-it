---
title: Protezione delle stringhe di connessione | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69ce8557-5260-4ea4-81b8-d0c5481f0868
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a69727d252d2e8d51d462a691f65379432096eb
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="securing-connection-strings"></a>Protezione delle stringhe di connessione
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La protezione dell'accesso all'origine dati è uno degli obiettivi più importanti di un'applicazione. Per limitare l'accesso all'origine dati, è necessario adottare alcune precauzioni per garantire la protezione delle informazioni di connessione quali ID utente, password e nome dell'origine dei dati. L'archiviazione di un ID utente e della password in testo normale, ad esempio nel codice sorgente, comporta un problema serio di protezione. Anche se si fornisce una versione compilata del codice contenente le informazioni su ID utente e password in un'origine esterna, il codice compilato potrebbe essere disassemblato e l'ID utente e la password risultare quindi esposti. Di conseguenza, è di fondamentale importanza che informazioni critiche quali ID utente e password non siano presenti nel codice.  
  
 È consigliabile non archiviare la password insieme all'URL di connessione nel codice sorgente dell'applicazione, ma piuttosto in un file distinto con accesso limitato. L'accesso al file può essere concesso in base al contesto in cui viene eseguita l'applicazione.  
  
 Un altro metodo è l'archiviazione della password crittografata in un file. Utilizzare un'API di crittografia che non richieda la chiave per l'archiviazione e che non sia stata derivata dalla password dell'utente. Ad esempio, è consigliabile valutare l'opportunità di utilizzare coppie di chiavi pubbliche/private basate sui certificati oppure un metodo in cui le due parti utilizzano un protocollo di chiave concordata (algoritmo di Diffie-Hellman) per generare le stesse chiavi private per la crittografia senza mai dover trasmettere la chiave privata.  
  
 Se le informazioni sulla stringa di connessione provengono da un'origine esterna, ad esempio un utente che fornisce un ID utente e la relativa password, sarà necessario convalidare tutti gli input dell'origine per assicurarsi che il formato sia corretto e che non contenga ulteriori parametri che interessano la la connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni del Driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

