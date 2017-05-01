---
title: "Finestra di dialogo Proprietà connessione | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connectionproperties.f1
helpviewer_keywords:
- Connection Properties dialog box
ms.assetid: 6df812ad-4d80-4503-8a23-47719ce85624
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8e258a6b81a9061c08ba4df098afa4e67c74df3a
ms.lasthandoff: 04/11/2017

---
# <a name="connection-properties-dialog-box"></a>Finestra di dialogo Proprietà connessione
Utilizzare questa finestra di dialogo per visualizzare le proprietà della connessione corrente. Questa finestra di dialogo è disponibile se si fa clic su **Visualizza proprietà connessione** in varie finestre di dialogo di Esplora oggetti. Le proprietà visualizzate in questa pagina sono di sola lettura.  
  
Per modificare proprietà quale **Database**, connettersi al database con Esplora oggetti prima di aprire la finestra di dialogo **Proprietà connessione** .  
  
Il periodo di timeout della query per SQL Azure è di 30 minuti.  
  
## <a name="authentication"></a>Autenticazione  
Consente di visualizzare le proprietà di autenticazione per la connessione corrente. Le proprietà di autenticazione sono costituite dall'account di accesso e dal metodo di autenticazione utilizzati al momento della connessione. Per modificare le proprietà di autenticazione, disconnettersi da [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]e riconnettere Esplora oggetti al server usando le opzioni di connessione appropriate.  
  
**Metodo di autenticazione**  
Metodo di autenticazione utilizzato per la connessione corrente.  
  
**Nome utente**  
Nome dell'utente dell'account di accesso utilizzato per l'autenticazione della connessione.  
  
## <a name="connection-category"></a>Connessione  
Consente di visualizzare le proprietà di connessione della connessione corrente. La maggior parte delle proprietà di connessione viene selezionata nella scheda **Proprietà connessione** della finestra di dialogo **Connetti al server** durante il processo di connessione.  
  
**Database**  
Nome del database al quale si è attualmente connessi. Per modificare questa impostazione, utilizzare la barra degli strumenti Editor SQL.  
  
**SPID**  
ID di processo di sistema assegnato dal server alla connessione. Non è possibile modificare questa impostazione per la connessione corrente.  
  
**Protocollo di rete**  
Protocollo di rete della connessione [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] . Per modificare questa impostazione, riconnettersi con le proprietà di connessione desiderate.  
  
**Dimensioni pacchetto di rete**  
Dimensioni di pacchetto utilizzate per la comunicazione con il server. Per modificare questa impostazione, riconnettersi con le proprietà di connessione desiderate.  
  
**Connection Timeout**  
Tempo di attesa in secondi per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] prima che si verifichi il timeout o venga restituito un errore di connessione all'utente. Per modificare questa impostazione, riconnettersi con le proprietà di connessione desiderate.  
  
**Execution Timeout**  
Tempo di attesa in secondi prima del completamento dell'esecuzione di un'attività nel server. Per modificare questa impostazione, riconnettersi con le proprietà di connessione desiderate.  
  
**Crittografata**  
Consente di indicare se la connessione corrente è crittografata. Per modificare questa impostazione, riconnettersi con le proprietà di connessione desiderate.  
  
## <a name="product-category"></a>Product Category  
Consente di visualizzare le proprietà del prodotto per la connessione corrente. Queste proprietà descrivono il prodotto server, la versione, il nome istanza e le regole di confronto. Le proprietà vengono impostate durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Nome prodotto**  
Il nome del prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Versione prodotto**  
La versione del prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Nome server**  
Il nome del computer su cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Nome istanza**  
Nome dell'istanza del server. L'istanza predefinita è vuota.  
  
**Lingua**  
Lingua della versione del prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Confronto**  
Regole di confronto del server.  
  
## <a name="server-environment-category"></a>Ambiente server  
Consente di visualizzare le proprietà dell'ambiente del server per la connessione corrente correlate all'hardware e al sistema operativo del server. Le proprietà non possono essere configurate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Nome computer**  
Nome del computer server che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Piattaforma**  
Nome del sistema operativo, nome del produttore e famiglia di CPU del server.  
  
**Sistema operativo**  
Versione di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows installata nel server.  
  
**Processori**  
Numero di processori presenti nel server.  
  
**Memoria sistema operativo**  
Quantità totale di memoria fisica disponibile nel server espressa in megabyte (MB).  
  
## <a name="see-also"></a>Vedere anche  
[Pagine delle proprietà in SQL Server Management Studio](../../ssms/property-pages-in-sql-server-management-studio.md)  
[Connetti al server &amp;#40;Pagina di accesso&amp;#41; Motore di database](../../ssms/f1-help/connect-to-server-login-page-database-engine.md)  
  

