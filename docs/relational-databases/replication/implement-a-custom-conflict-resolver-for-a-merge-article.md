---
title: "Implement a Custom Conflict Resolver for a Merge Article | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers"
  - "articles [SQL Server replication], conflict resolution"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Implement a Custom Conflict Resolver for a Merge Article
  In questo argomento viene descritto come implementare dei conflitti personalizzato per un articolo di merge in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[tsql](../../includes/tsql-md.md)] o [risoluzione dei conflitti personalizzato basato su COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
 **Contenuto dell'argomento**  
  
-   **Per implementare un sistema di risoluzione dei conflitti personalizzato per un articolo di tipo merge, utilizzando:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Sistema di risoluzione basato su COM](#COM)  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile scrivere un sistema di risoluzione dei conflitti personalizzato come stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] in ogni server di pubblicazione. Durante la sincronizzazione questa stored procedure viene richiamata quando vengono rilevati conflitti in un articolo per il quale il sistema di risoluzione è stato registrato e l'agente di merge passa le informazioni sulla riga con conflitti ai parametri obbligatori della procedura. I sistemi di risoluzione dei conflitti personalizzati basati su stored procedure vengono sempre creati nel server di pubblicazione.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sistemi di risoluzione stored procedure vengono richiamati solo per gestire conflitti causati da modifiche apportate alle righe. Non possono essere utilizzati per gestire altri tipi di conflitti, ad esempio errori di inserimento dovuti a violazioni di PRIMARY KEY o del vincolo di indice univoco.  
  
#### Per creare un sistema di risoluzione dei conflitti personalizzato basato su stored procedure  
  
1.  Nella pubblicazione o nel database **msdb** del server di pubblicazione creare una nuova stored procedure di sistema che implementi i parametri obbligatori seguenti:  
  
    |Parametro|Tipo di dati|Descrizione|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|**sysname**|Nome del proprietario della tabella per la quale risolvere un conflitto. Si tratta del proprietario della tabella nel database di pubblicazione.|  
    |**@tablename**|**sysname**|Nome della tabella per la quale risolvere un conflitto.|  
    |**@rowguid**|**uniqueidentifier**|Identificatore univoco per la riga in cui è presente il conflitto.|  
    |**@subscriber**|**sysname**|Nome del server da cui viene propagata una modifica in conflitto.|  
    |**@subscriber_db**|**sysname**|Nome del database da cui viene propagata una modifica in conflitto.|  
    |**@log_conflict OUTPUT**|**int**|Indica se il processo di merge deve registrare un conflitto da risolvere in un secondo momento:<br /><br /> **0** = non il conflitto non viene registrato.<br /><br /> **1** = sottoscrittore è la riga in conflitto ignorata.<br /><br /> **2** = server di pubblicazione è la riga in conflitto ignorata.|  
    |**@conflict_message OUTPUT**|**nvarchar(512)**|Messaggio da visualizzare per la risoluzione se il conflitto viene registrato.|  
    |**@destowner**|**sysname**|Proprietario della tabella pubblicata nel Sottoscrittore.|  
  
     Questa stored procedure utilizza i valori passati dall'agente di merge a questi parametri per implementare la logica di risoluzione dei conflitti personalizzata. Deve restituire un solo set di risultati della riga la cui struttura è identica a quella della tabella di base e che contiene i valori dei dati per la versione confermata della riga.  
  
2.  Concedere autorizzazioni EXECUTE sulla stored procedure a qualsiasi account di accesso utilizzato dai Sottoscrittori per la connessione al server di pubblicazione.  
  
#### Per utilizzare un sistema di risoluzione dei conflitti personalizzato con un nuovo articolo di tabella  
  
1.  Eseguire [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) per definire un articolo, specificando il valore **Microsoft SQL** **Server Stored Procedure Resolver** per il **@article_resolver** parametro e il nome della stored procedure che implementa la logica del sistema di risoluzione dei conflitti per il **@resolver_info** parametro. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per utilizzare un sistema di risoluzione dei conflitti personalizzato con un articolo di tabella esistente  
  
1.  Eseguire [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando **@publication**, **@article**, un valore di **article_resolver** per **@property**, e il valore **Microsoft SQL** **Server archiviati ProcedureResolver** per **@value**.  
  
2.  Eseguire [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando **@publication**, **@article**, un valore di **resolver_info** per **@property**, e il nome della stored procedure che implementa la logica del sistema di risoluzione dei conflitti per **@value**.  
  
##  <a name="COM"></a> Utilizzo di un sistema di risoluzione personalizzato basato su COM  
 Il <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> dello spazio dei nomi implementa un'interfaccia che consente di scrivere la logica di business complessa per gestire gli eventi e risolvere i conflitti che si verificano durante il processo di sincronizzazione della replica di merge. Per altre informazioni, vedere [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md). Per risolvere i conflitti, è inoltre possibile scrivere una logica di business personalizzata basata su codice nativo. Tale logica viene compilata come un componente COM in DLL, utilizzando prodotti quali [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++. Questo tipo un sistema di risoluzione di conflitti personalizzato basato su COM deve implementare il **ICustomResolver** interfaccia, che è progettato specificamente per la risoluzione dei conflitti.  
  
#### Per creare e registrare un sistema di risoluzione dei conflitti personalizzato basato su COM  
  
1.  In un ambiente di creazione compatibile con COM aggiungere riferimenti alla libreria del sistema di risoluzione dei conflitti personalizzato.  
  
2.  Per un progetto Visual C++ utilizzare la direttiva #import per importare la libreria nel progetto.  
  
3.  Creare una classe che implementa l'interfaccia **ICustomResolver** .  
  
4.  Implementare determinati metodi e proprietà.  
  
5.  Compilare il progetto per creare il file della libreria del sistema di risoluzione dei conflitti personalizzato.  
  
6.  Distribuire la libreria nella directory che contiene il file eseguibile dell'agente di merge, in genere \Microsoft SQL Server\100\COM.  
  
    > [!NOTE]  
    >  Un sistema di risoluzione dei conflitti personalizzato deve essere distribuito nel Sottoscrittore per una sottoscrizione pull, nel server di distribuzione per una sottoscrizione push o nel server Web utilizzato con sincronizzazione tramite il Web.  
  
7.  Registrare la libreria del sistema di risoluzione dei conflitti personalizzato utilizzando regsvr32.exe nella directory di distribuzione come descritto di seguito:  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Per verificare che la libreria non è già registrata come un sistema di risoluzione dei conflitti personalizzato.  
  
9. Per registrare la libreria come un sistema di risoluzione dei conflitti personalizzato, eseguire [sp_registercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), nel server di distribuzione. Specificare il nome descrittivo dell'oggetto COM per **@article_resolver**, ID (CLSID della raccolta di) per **@resolver_clsid**, e il valore **false** per **@is_dotnet_assembly**.  
  
    > [!NOTE]  
    >  Quando non è più necessario, un sistema di risoluzione dei conflitti personalizzato può essere annullata mediante [sp_unregistercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md).  
  
10. (Facoltativo) In un cluster ripetere i passaggi da 5 a 8 per registrare il sistema di risoluzione personalizzato in tutti i nodi del cluster. Tale operazione è necessaria per garantire che il sistema di risoluzione personalizzato sia in grado di caricare correttamente il riconciliatore in seguito a un failover.  
  
#### Per utilizzare un sistema di risoluzione dei conflitti personalizzato con un nuovo articolo di tabella  
  
1.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) e annotare il nome descrittivo del sistema di risoluzione desiderato.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Per definire un articolo. Specificare il nome descrittivo del sistema di risoluzione articolo ottenuto al passaggio 1 per **@article_resolver**. Per altre informazioni, vedere [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per utilizzare un sistema di risoluzione dei conflitti personalizzato con un articolo di tabella esistente  
  
1.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) e annotare il nome descrittivo del sistema di risoluzione desiderato.  
  
2.  Eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando **@publication**, **@article**, un valore di **article_resolver** per **@property**, e il nome descrittivo del sistema di risoluzione articolo ottenuto al passaggio 1 per **@value**.  
  
#### Visualizzazione di un sistema di risoluzione personalizzato di esempio  
  
1.  Un esempio è disponibile nei file di esempio di SQL Server 2000. Scaricare il file **sql2000samples.cab** dalla pagina relativa agli [esempi aggiornati per SQL Server 2000 Service Pack 3](http://www.microsoft.com/download/details.aspx?id=8560). Vengono scaricati 8 file per un totale di 6,9 MB.  
  
2.  Estrarre i file dal file con estensione cab compresso scaricato.  
  
3.  Eseguire **setup.exe**  
  
    > [!NOTE]  
    >  Quando si scelgono le opzioni di installazione, è necessario installare solo gli esempi relativi alla **replica** (Il percorso di installazione predefinito è **C:\Programmi\Microsoft file (x86) \Microsoft SQL Server 2000 Samples\1033\\**)  
  
4.  Passare alla cartella di installazione. (La cartella predefinita è **C:\Programmi\Microsoft file (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  Eseguire il **unzip_sqlreplSP3.exe** programma.  
  
    > [!NOTE]  
    >  Verrà installato il sistema di risoluzione com di esempio (per impostazione predefinita) per il **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** cartella.  
  
6.  Nel **subspres** cartella, trovare tutte le occorrenze di **#include Sqlres. h** in tutti i file di origine e sostituirle con **#import "replrec" no_namespace, raw_interfaces_only**  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Sistemi di risoluzione personalizzati basati su COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md)   
 [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  