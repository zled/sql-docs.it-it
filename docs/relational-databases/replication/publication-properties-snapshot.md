---
title: "Propriet&#224; pubblicazione, Snapshot | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.snapshotformat.f1"
ms.assetid: 8e9133b1-fc37-4a85-8a7c-d5eaf172fbef
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Propriet&#224; pubblicazione, Snapshot
  Il **Snapshot** pagina la **Proprietà pubblicazione** la finestra di dialogo consente di impostare il formato dello snapshot, percorso della cartella snapshot e script da eseguire prima e dopo l'applicazione dello snapshot. La cartella dello snapshot deve essere designata come condivisione e disporre delle autorizzazioni sufficienti per la lettura e la scrittura dei file nella cartella da parte degli agenti. Per ulteriori informazioni sulla protezione della cartella in modo appropriato, vedere [sicurezza della cartella Snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  In caso di modifiche, sarà necessario un nuovo snapshot per la pubblicazione. Per ulteriori informazioni, vedere [Modifica proprietà della pubblicazione e articolo](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Opzioni  
 **Formato snapshot**  
 Consente di selezionare la modalità nativa o la modalità carattere per il formato dello snapshot.  
  
-   Selezionare **nativo di SQL Server - tutti i sottoscrittori devono essere server che esegue SQL Server** se tutti i sottoscrittori sono istanze di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diverso da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Il formato nativo dello snapshot offre le migliori prestazioni.  
  
-   Selezionare **carattere: obbligatorio se un server di pubblicazione o sottoscrizione non è in esecuzione SQL Server** se tutti i Sottoscrittori eseguono [!INCLUDE[ssEW](../../includes/ssew-md.md)] oppure non sono[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori.  
  
 **Percorso dei file di snapshot**  
 Consente di selezionare il percorso per l'archiviazione dei file di snapshot. Questi file possono essere archiviati nel percorso predefinito. È inoltre possibile archiviarli in un percorso alternativo in sostituzione o in aggiunta al percorso predefinito. I file archiviati in un percorso alternativo possono essere archiviati.  
  
-   Selezionare **inserire file nella cartella predefinita** da utilizzare nella cartella snapshot predefinita per il server di pubblicazione. Il percorso della cartella snapshot è di sola lettura nella finestra di dialogo, in quanto può essere modificata solo per il server di pubblicazione nel **proprietà server di distribuzione** la finestra di dialogo. Per ulteriori informazioni, vedere [specificare la posizione predefinita degli Snapshot & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   Selezionare **inserire file nella cartella seguente** per specificare un percorso alternativo anziché o oltre a, il percorso predefinito. Immettere un percorso nella casella di testo oppure fare clic su **Sfoglia** e passare al percorso. Selezionare **comprimere i file di snapshot nella cartella** per comprimere i file nella cartella snapshot alternativa. Il percorso alternativo può trovarsi in un altro server, in un'unità di rete oppure in un supporto rimovibile, ad esempio un CD-ROM o un disco rimovibile. Per ulteriori informazioni, vedere [percorsi della cartella Snapshot alternativa](../../relational-databases/replication/alternate-snapshot-folder-locations.md) e [gli snapshot compressi](../../relational-databases/replication/compressed-snapshots.md).  
  
 **Script aggiuntivi**  
 Consente di specificare gli script da eseguire prima e dopo l'applicazione dello snapshot nel Sottoscrittore. Gli script non è possibile specificare se **formato dello Snapshot** è **carattere**.  
  
 L'utilizzo degli script è facoltativo, tuttavia esso rappresenta un metodo pratico per eseguire comandi e applicare modifiche amministrative nei Sottoscrittori. Per ulteriori informazioni sull'esecuzione di script, vedere [eseguire script prima e dopo l'applicazione dello Snapshot](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Immettere un percorso nella **prima di applicare lo snapshot, Esegui lo script seguente** casella di testo oppure fare clic su **Sfoglia** per specificare un percorso per lo script.  
  
-   Immettere un percorso nella **dopo aver applicato lo snapshot, Esegui lo script seguente** casella di testo oppure fare clic su **Sfoglia** per specificare un percorso per lo script.  
  
## Vedere anche  
 [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzazione e modifica delle proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Creazione e applicazione dello snapshot iniziale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Pubblicazione di dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  