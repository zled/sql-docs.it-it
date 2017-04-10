---
title: "Considerazioni sulla sicurezza per il runtime R in SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Considerazioni sulla sicurezza per il runtime R in SQL Server
  In questo argomento viene fornita una panoramica delle considerazioni di sicurezza per l'utilizzo di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per ulteriori informazioni sulla gestione del servizio e su come eseguire il provisioning di account utente utilizzato per eseguire gli script R, vedere [configurare e gestire Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
  
## Usare il firewall per limitare l'accesso alla rete da parte del runtime R  
 Nel metodo di installazione consigliato si usa una regola di Windows Firewall per impedire ai processi del runtime R l'accesso alla rete in uscita. È consigliabile creare regole del firewall per impedire che il processo del runtime R scarichi pacchetti o effettui altre chiamate di rete che potrebbero essere potenzialmente dannose.  
  
 Si consiglia di attivare Windows Firewall (o un qualsiasi altro firewall) per impedire al runtime R di accedere alla rete.  
  
 Se si usa un programma firewall diverso, è anche possibile creare regole per bloccare la connessione di rete in uscita per il runtime R, impostando regole per gli account utente locali o per il gruppo rappresentato dal pool di account utente.   
Per altre informazioni, vedere [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
  
## Metodi di autenticazione supportati per i contesti di elaborazione remota 
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] supporta ora gli account di accesso sia l'autenticazione integrata di Windows e SQL durante la creazione di connessioni tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un client di analisi scientifica dei dati remota. 
  
 Ad esempio, se si sviluppa una soluzione di R sul computer portatile e si desidera eseguire i calcoli nel computer SQL Server, creare un'origine dati SQL Server in R, usando il **rx** funzioni e la definizione di una stringa di connessione in base alle credenziali di Windows. Quando si modifica il _calcolo contesto_ dal computer portatile per il computer SQL Server, se l'account di Windows disponga delle autorizzazioni necessarie, tutto il codice R verrà eseguito nel computer SQL Server. Inoltre, qualsiasi query SQL eseguite come parte del codice R verranno eseguite anche le credenziali. 
 
 Sebbene un account di accesso SQL può anche essere utilizzati nella stringa di connessione per un'origine dati SQL Server, utilizzare un account di accesso è necessario che l'istanza di SQL Server consentano l'autenticazione in modalità mista.
 
 ### Autenticazione implicita
  
 In generale il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Avvia il runtime R ed esegue gli script R con il proprio account. Tuttavia, se lo script R effettua una chiamata ODBC, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] rappresenterà le credenziali dell'utente che ha inviato il comando per verificare che la chiamata ODBC non esito negativo. Questa operazione è detta *autenticazione implicita*. 
 
 > [!IMPORTANT] 
 >
 > Per l'autenticazione implicita abbia esito positivo, il gruppo di utenti Windows che contiene gli account di lavoro (per impostazione predefinita, **SQLRUser**) deve disporre di un account nel database master per l'istanza e questo account deve disporre delle autorizzazioni per connettersi all'istanza.  
  
## Nessun supporto per la crittografia dei dati inattivi  
 La tecnologia Transparent Data Encryption non è supportata per i dati inviati o ricevuti dal runtime R. Di conseguenza, la crittografia a riposo **non** da applicare a tutti i dati utilizzati negli script R, i dati salvati su disco o i risultati intermedi persistenti.  
 
 ## Vedere anche
 [Immettere qui la descrizione collegamento](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 
  