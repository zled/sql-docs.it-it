---
title: "Impostazione delle opzioni dello schema | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemi [replica di SQL Server], opzioni"
  - "articoli [replica di SQL Server], opzioni di replica transazionale"
  - "articoli [replica di SQL Server], opzioni di replica di tipo merge"
  - "articoli [replica di SQL Server], opzioni dello schema"
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Impostazione delle opzioni dello schema
  In questo argomento si illustra come impostare le opzioni dello schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Quando si pubblica una tabella o una vista, è possibile controllare le opzioni di creazione degli oggetti che vengono replicate per l'oggetto pubblicato. È possibile impostare queste opzioni quando viene creato l'articolo ed è possibile modificarle anche successivamente. Se queste opzioni non vengono specificate in modo esplicito per un articolo, verrà definito un set predefinito di opzioni.  
  
> [!NOTE]  
>  Le opzioni predefinite dello schema disponibili quando si utilizzano le stored procedure di replica possono essere diverse dalle opzioni predefinite utilizzate quando gli articoli vengono aggiunti tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per specificare le opzioni dello schema tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se si modificano le opzioni dello schema dopo la creazione di una pubblicazione, è necessario generare un nuovo snapshot.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Per l'elenco completo delle opzioni di schema, vedere il **@schema_option** parametro [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) e [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare le opzioni di schema, ad esempio se copiare i vincoli e trigger ai sottoscrittori, nel **proprietà** scheda della finestra di **Proprietà articolo - \< articolo>** la finestra di dialogo. Questa scheda è disponibile nella creazione guidata pubblicazione e la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare le opzioni dello schema  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare un articolo e quindi fare clic su **Proprietà articolo**.  
  
2.  Selezionare gli articoli a cui si applicano le modifiche delle opzioni dello schema:  
  
    -   Fare clic su **impostare proprietà di evidenziate \< ObjectType> articolo** per avviare il **Proprietà articolo - \< ObjectName>** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate solo all'oggetto evidenziato nel riquadro degli oggetti nel **articoli** pagina.  
  
    -   Fare clic su **impostare le proprietà di tutti \< ObjectType> articoli** per avviare il **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo; Proprietà le modifiche apportate in questa finestra di dialogo vengono applicate a tutti gli oggetti di quel tipo nel riquadro degli oggetti nel **articoli** pagina, inclusi quelli non ancora selezionati per la pubblicazione.  
  
        > [!NOTE]  
        >  Modifiche delle proprietà apportate nel **le proprietà per tutti \< ObjectType> articoli** la finestra di dialogo sostituire qualsiasi apportate in precedenza il **Proprietà articolo - \< ObjectName>** la finestra di dialogo. Se ad esempio si desidera impostare alcuni valori predefiniti per tutti gli articoli di un tipo di oggetto e, al contempo, alcune proprietà per singoli oggetti, è necessario impostare innanzitutto i valori predefiniti per tutti gli articoli, quindi le proprietà relative ai singoli oggetti.  
  
3.  Nel **Copia oggetti e impostazioni nel Sottoscrittore** e **oggetto di destinazione** sezioni del **proprietà** scheda il **Proprietà articolo - \< articolo>** finestra di dialogo specificare valori per le opzioni.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
5.  Se è la **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 Le opzioni dello schema vengono specificate come un valore esadecimale di [| (OR bit per bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) risultato di una o più opzioni. Per ulteriori informazioni, vedere [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) e [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
> [!NOTE]  
>  È necessario convertire i valori delle opzioni dello schema da **binario** a **int** prima di eseguire un'operazione bit per bit. Per ulteriori informazioni, vedere [CAST e CONVERT & #40; Transact-SQL & #41;](../../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
#### Per specificare le opzioni dello schema durante la definizione di un articolo per una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, il tipo di oggetto di database per **@type**, e [| (OR bit per bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) risultato di uno o più opzioni dello schema per **@schema_option**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per specificare le opzioni dello schema durante la definizione di un articolo per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, un nome per l'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**, e [| (OR bit per bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) risultato di uno o più opzioni dello schema per **@schema_option**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### Per modificare le opzioni dello schema per un articolo esistente in una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Specificare il nome della pubblicazione cui appartiene l'articolo per **@publication** e il nome dell'articolo per **@article**. Si noti il valore di **schema_option** colonna nel set di risultati.  
  
2.  Eseguire un [& (AND bit per bit)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) valore per determinare se l'impostazione dell'opzione operazione utilizzando il valore del passaggio 1 e lo schema desiderato.  
  
    -   Se il risultato è **0**, l'opzione non è impostata.  
  
    -   Se il risultato corrisponde al valore dell'opzione, l'opzione è già impostata.  
  
3.  Se l'opzione non è impostata, eseguire una [| (OR bit per bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) operazione utilizzando il valore ottenuto al passaggio 1 e il valore dell'opzione dello schema desiderato.  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, il nome dell'articolo per **@article**, un valore di **schema_option** per **@property**, e il risultato esadecimale del passaggio 3 per **@value**.  
  
5.  Eseguire l'agente snapshot per generare un nuovo snapshot. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### Per modificare le opzioni dello schema per un articolo esistente in una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Specificare il nome della pubblicazione cui appartiene l'articolo per **@publication** e il nome dell'articolo per **@article**. Si noti il valore di **schema_option** colonna nel set di risultati.  
  
2.  Eseguire un [& (AND bit per bit)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) valore per determinare se l'impostazione dell'opzione operazione utilizzando il valore del passaggio 1 e lo schema desiderato.  
  
    -   Se il risultato è **0**, l'opzione non è impostata.  
  
    -   Se il risultato corrisponde al valore dell'opzione, l'opzione è già impostata.  
  
3.  Se l'opzione non è impostata, eseguire una [| (OR bit per bit)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) operazione utilizzando il valore ottenuto al passaggio 1 e il valore dell'opzione dello schema desiderato.  
  
4.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare il nome della pubblicazione a cui appartiene l'articolo per **@publication**, il nome dell'articolo per **@article**, un valore di **schema_option** per **@property**, e il risultato esadecimale del passaggio 3 per **@value**.  
  
5.  Eseguire l'agente snapshot per generare un nuovo snapshot. Per altre informazioni, vedere [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Opzioni degli articoli per la replica transazionale](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
  