---
title: "Impostazione del metodo di propagazione per le modifiche ai dati negli articoli transazionali | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transactional replication, propagation methods"
  - "propagazione di modifiche ai dati [replica di SQL Server]"
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Impostazione del metodo di propagazione per le modifiche ai dati negli articoli transazionali
  In questo argomento viene descritto come impostare il metodo di propagazione per le modifiche ai dati negli articoli transazionali in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Per impostazione predefinita, la replica transazionale propaga le modifiche ai Sottoscrittori tramite un set di stored procedure per ogni articolo. È possibile sostituire tali procedure con procedure personalizzate. Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
-   **Per impostare il metodo di propagazione per la modifica dei dati negli articoli transazionali tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   È consigliabile prestare particolare attenzione quando si modificano i file di snapshot generati dalla replica. È necessario testare e supportare la logica personalizzata nelle stored procedure personalizzate. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] non fornisce supporto per la logica personalizzata.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare il metodo di propagazione nel **proprietà** scheda della finestra di **Proprietà articolo - \< articolo>** la finestra di dialogo, disponibile nella creazione guidata pubblicazione e il **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare il metodo di propagazione  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella e quindi fare clic su **Proprietà articolo**.  
  
2.  Fare clic su **Imposta proprietà dell'articolo tabella evidenziato**.  
  
3.  Nel **proprietà** scheda del **Proprietà articolo - \< articolo>** della finestra di dialogo di **Recapito istruzione** sezione, specificare il metodo di propagazione per ogni operazione mediante il **Formato recapito INSERT**, **Formato recapito UPDATE**, e **Formato recapito DELETE** menu.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### Per generare e utilizzare stored procedure personalizzate  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella e quindi fare clic su **Proprietà articolo**.  
  
2.  Fare clic su **Imposta proprietà dell'articolo tabella evidenziato**.  
  
     Nel **proprietà** scheda del **Proprietà articolo - \< articolo>** della finestra di dialogo di **Recapito istruzione** selezionare la sintassi di chiamata dal menu Formato recapito appropriato (**Formato recapito INSERT**, **Formato recapito UPDATE**, o **Formato recapito DELETE**) e quindi digitare il nome della procedura da utilizzare **stored procedure INSERT**, **stored procedure di eliminazione**, o **stored procedure di aggiornamento**. Per ulteriori informazioni sulla sintassi di chiamata, vedere la sezione "Sintassi Call per stored procedure" in [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
5.  Quando lo snapshot per la pubblicazione viene generato, esso include la procedura specificata nel passaggio precedente. Le procedure utilizzeranno la sintassi CALL specificata, ma includeranno la logica predefinita utilizzata dalla replica.  
  
     Dopo la generazione dello snapshot, passare alla cartella snapshot per la pubblicazione cui appartiene questo articolo e individuare il file con estensione **sch** che presenta lo stesso nome dell'articolo. Aprire il file mediante Blocco note o un altro editor di testo, individuare il comando CREATE PROCEDURE per le stored procedure di inserimento, aggiornamento o eliminazione, quindi modificare la definizione della procedura in modo da fornire qualsiasi logica personalizzata per la propagazione delle modifiche ai dati. Se lo snapshot viene rigenerato, è necessario ricreare la stored procedura personalizzata.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 La replica transazionale consente di controllare la modalità con cui le modifiche vengono propagate dal server di pubblicazione ai Sottoscrittori. Questo metodo di propagazione può inoltre essere impostato a livello di programmazione quando un articolo viene creato e in seguito modificato tramite le stored procedure di replica.  
  
> [!NOTE]  
>  È possibile specificare un metodo di propagazione diverso per ogni tipo di operazione DML (Data Manipulation Language), ovvero inserimento, aggiornamento o eliminazione, che si verifica in una riga di dati pubblicati.  
  
 Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Per creare un articolo che utilizza comandi Transact-SQL per propagare le modifiche ai dati  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, e il valore **SQL** per almeno uno dei seguenti parametri:  
  
    -   **@ins_cmd** -Controlla la replica dei [inserire](../../../t-sql/statements/insert-transact-sql.md) comandi.  
  
    -   **@upd_cmd** -Controlla la replica dei [aggiornamento](../../../t-sql/queries/update-transact-sql.md) comandi.  
  
    -   **@del_cmd** -Controlla la replica dei [eliminare](../../../t-sql/statements/delete-transact-sql.md) comandi.  
  
    > [!NOTE]  
    >  Quando si specifica un valore di **SQL** per uno dei parametri indicati in precedenza, i comandi di quel tipo verranno replicati nel Sottoscrittore come appropriato [!INCLUDE[tsql](../../../includes/tsql-md.md)] comando.  
  
     Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per creare un articolo che non propaga le modifiche ai dati  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, e il valore **NONE** per almeno uno dei seguenti parametri:  
  
    -   **@ins_cmd** -Controlla la replica dei [inserire](../../../t-sql/statements/insert-transact-sql.md) comandi.  
  
    -   **@upd_cmd** -Controlla la replica dei [aggiornamento](../../../t-sql/queries/update-transact-sql.md) comandi.  
  
    -   **@del_cmd** -Controlla la replica dei [eliminare](../../../t-sql/statements/delete-transact-sql.md) comandi.  
  
    > [!NOTE]  
    >  Quando si specifica un valore di **NONE** per uno dei parametri indicati in precedenza, i comandi di tale tipo non essere replicati al sottoscrittore.  
  
     Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per creare un articolo con stored procedure personalizzate modificate dall'utente  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, un valore per il **@schema_option** maschera di bit che contiene il valore **0x02** (consente la generazione automatica di stored procedure personalizzate) e almeno uno dei seguenti parametri:  
  
    -   **@ins_cmd** -specificare un valore di **chiamata sp_Msins _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    -   **@del_cmd** -specificare un valore di **sp_Msdel _ chiamata*article_name*** o **XCALL sp_Msdel _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    -   **@upd_cmd** -specificare un valore di **SCALL sp_Msupd _*article_name***, **sp_Msupd _ chiamata*article_name***, **XCALL sp_Msupd _*article_name***, o **MCALL sp_Msupd _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    > [!NOTE]  
    >  Per ognuno dei parametri di comando indicati in precedenza, è possibile specificare il nome desiderato per le stored procedure generate dalla replica.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sulla sintassi di chiamata, SCALL, XCALL e MCALL, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
     Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Dopo la generazione dello snapshot, passare alla cartella snapshot per la pubblicazione cui appartiene questo articolo e individuare il file con estensione **sch** che presenta lo stesso nome dell'articolo. Aprire il file mediante Notepad.exe, individuare il comando CREATE PROCEDURE per le stored procedure di inserimento, aggiornamento o eliminazione e modificare la definizione della procedura per specificare la logica personalizzata per la propagazione delle modifiche ai dati. Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Per creare un articolo con scripting personalizzato nelle stored procedure personalizzate per propagare le modifiche ai dati  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, un valore per il **@schema_option** maschera di bit che contiene il valore **0x02** (consente la generazione automatica di stored procedure personalizzate) e almeno uno dei seguenti parametri:  
  
    -   **@ins_cmd** -specificare un valore di **chiamata sp_Msins _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    -   **@del_cmd** -specificare un valore di **sp_Msdel _ chiamata*article_name*** o **XCALL sp_Msdel _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    -   **@upd_cmd** -specificare un valore di **SCALL sp_Msupd _*article_name***, **sp_Msupd _ chiamata*article_name***, **XCALL sp_Msupd _*article_name***, **MCALL sp_Msupd _*article_name***, dove ***article_name*** è il valore specificato per **@article**.  
  
    > [!NOTE]  
    >  Per ognuno dei parametri di comando indicati in precedenza, è possibile specificare il nome desiderato per le stored procedure generate dalla replica.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sulla sintassi di chiamata, SCALL, XCALL e MCALL, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
     Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Nel server di pubblicazione nel database di pubblicazione, utilizzare il [ALTER PROCEDURE](../../../t-sql/statements/alter-procedure-transact-sql.md) istruzione per modificare [sp_scriptpublicationcustomprocs](../../../relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql.md) in modo che restituisca un [CREATE PROCEDURE](../../../t-sql/statements/create-procedure-transact-sql.md) script per l'insert, update e delete personalizzato archiviati procedure. Per ulteriori informazioni, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
#### Per modificare il metodo di propagazione delle modifiche per un articolo esistente  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Specificare **@publication**, **@article**, un valore di **ins_cmd**, **upd_cmd**, o **del_cmd** per **@property**, nonché il metodo di propagazione appropriato per **@value**.  
  
2.  Ripetere il passaggio 1 per ogni metodo di propagazione da modificare.  
  
## Vedere anche  
 [Impostazione della modalità di propagazione delle modifiche per gli articoli transazionali](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [Creare, modificare ed eliminare le pubblicazioni e articoli e 40 #; Replica & #41;](../../../relational-databases/replication/publish/create-modify-and-delete-publications-and-articles-replication.md)  
  
  