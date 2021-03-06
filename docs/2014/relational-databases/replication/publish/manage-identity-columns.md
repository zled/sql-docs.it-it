---
title: Gestire le colonne Identity | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server replication]
- merge replication [SQL Server replication], identity range management
- publishing [SQL Server replication], identity columns
- transactional replication, identity range management
- identity columns [SQL Server], replication
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a05cbb061c2f0df716458de35b3a1bad9fbae7e2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198261"
---
# <a name="manage-identity-columns"></a>Gestione delle colonne Identity
  In questo argomento viene descritto come gestire le colonne Identity in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Quando gli inserimenti del Sottoscrittore vengono replicati nel server di pubblicazione, è necessario gestire le colonne Identity in modo da evitare l'assegnazione dello stesso valore Identity sia al Sottoscrittore che al server di pubblicazione. È possibile gestire automaticamente intervalli di valori Identity tramite la replica oppure scegliere di gestirli manualmente.  Per informazioni sulle opzioni di gestione degli intervalli di valori Identity fornite dalla replica, vedere [Replicare colonne Identity](replicate-identity-columns.md).  
  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Quando si pubblica una tabella in più di una pubblicazione, è necessario specificare le stesse opzioni di gestione degli intervalli di valori Identity per entrambi le pubblicazioni. Per altre informazioni, vedere "Pubblicazione di tabelle in più di una pubblicazione" in [Pubblicare dati e oggetti di database](publish-data-and-database-objects.md).  
  
-   Per creare un numero a incremento automatico da usare in più tabelle o da chiamare dalle applicazioni senza fare riferimento ad alcuna tabella, vedere [Numeri di sequenza](../../sequence-numbers/sequence-numbers.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare un'opzione per la gestione delle colonne Identity nella scheda **Proprietà** della finestra di dialogo **Proprietà articolo -\<Articolo>** della Creazione guidata nuova pubblicazione. Per altre informazioni sull'uso di questa procedura guidata, vedere [Creare una pubblicazione](create-a-publication.md). Nella Creazione guidata nuova pubblicazione:  
  
-   Se si seleziona **Pubblicazione di tipo merge** o **Pubblicazione transazionale con sottoscrizioni aggiornabili** nella pagina **Tipo di pubblicazione** , specificare se si desidera utilizzare la gestione automatica o manuale di intervalli di valori Identity. È consigliabile la gestione automatica, che è l'opzione predefinita. Dopo la pubblicazione della tabella la proprietà non può più essere modificata, mentre è possibile modificare altre proprietà correlate.  
  
-   Se si selezionano altri tipi di pubblicazioni, è necessario impostare la gestione degli intervalli di valori Identity su manuale.  
  
 Modificare le soglie e gli intervalli di valori Identity nella scheda **Proprietà** della finestra di dialogo **Proprietà articolo -\<Articolo>**, disponibile nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-an-identity-column-management-option"></a>Per specificare un'opzione per la gestione di colonne Identity  
  
1.  Se nel server di pubblicazione è in esecuzione una versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedente a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], nella pagina **Tipo di pubblicazione** della Creazione guidata nuova pubblicazione selezionare **Pubblicazione di tipo merge** o **Pubblicazione transazionale con sottoscrizioni aggiornabili**.  
  
2.  Nella pagina **Articoli** selezionare una tabella con una colonna Identity.  
  
3.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di tabella evidenziato**.  
  
4.  Nella scheda **Proprietà** della finestra di dialogo **Proprietà articolo - \<Articolo>**, nella sezione **Gestione intervalli di valori Identity**, impostare la proprietà **Gestisci automaticamente gli intervalli di valori Identity** su **Automatico** o **Manuale** (per i server di pubblicazione che eseguono [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva) oppure su **True** o **False** (per i server di pubblicazione che eseguono una versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedente a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]).  
  
5.  Se nel passaggio 4 è stato selezionato **Automatico** o **True** , immettere i valori per le opzioni nella tabella che segue. Per altre informazioni su come usare queste impostazioni, vedere la sezione "Assegnazione degli intervalli di valori Identity" di [Replicare colonne Identity](replicate-identity-columns.md).  
  
    |Opzione|valore|Description|  
    |------------|-----------|-----------------|  
    |**Dimensioni intervallo server di pubblicazione**|Valore intero per le dimensioni dell'intervallo, ad esempio 20000.|Vedere la sezione "Assegnazione degli intervalli di valori Identity" di [Replicare colonne Identity](replicate-identity-columns.md).|  
    |**Dimensioni intervallo Sottoscrittore**|Valore intero per le dimensioni dell'intervallo, ad esempio 10000.|Vedere la sezione "Assegnazione degli intervalli di valori Identity" di [Replicare colonne Identity](replicate-identity-columns.md).|  
    |**Percentuale soglia intervallo**|Valore intero percentuale per la soglia dell'intervallo, ad esempio 90 è equivalente a 90%.|Percentuale dei valori Identity totali utilizzati in corrispondenza di un nodo prima dell'assegnazione di un nuovo intervallo di valori Identity.<br /><br /> Nota: questo valore deve essere specificato, ma viene usato solo dai Sottoscrittori che usano sottoscrizioni ad aggiornamento in coda e dai Sottoscrittori per pubblicazioni di tipo merge che eseguono [!INCLUDE[ssEW](../../../includes/ssew-md.md)] o una versione precedente di altre edizioni di SQL Server. Per altre informazioni, vedere la sezione "Assegnazione degli intervalli di valori Identity" di [Replicare colonne Identity](replicate-identity-columns.md).|  
    |**Valore iniziale intervallo successivo**|Valore intero. Di sola lettura.|Il valore in corrispondenza del quale inizierà l'intervallo successivo. Ad esempio, se l'intervallo corrente è 5001-6000, questo valore sarà 6001.|  
    |**Valore Identity massimo**|Valore intero. Di sola lettura.|Il valore maggiore per la colonna Identity. Determinato dal tipo di dati di base della colonna.|  
    |**Incremento valore Identity**|Valore intero. Di sola lettura.|La quantità in base alla quale il numero nella colonna Identity deve aumentare o diminuire per ciascun inserimento: in genere è impostata su 1.|  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-modify-identity-ranges-and-thresholds-after-a-table-is-published"></a>Per modificare le soglie e gli intervalli di valori Identity dopo la pubblicazione di una tabella  
  
1.  Nella pagina **Articoli** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare una tabella con una colonna Identity.  
  
2.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di tabella evidenziato**.  
  
3.  Nella scheda **Proprietà** della finestra di dialogo **Proprietà articoli - \<Articolo>**, nella sezione **Gestione intervalli di valori Identity**, immettere i valori per una o più delle proprietà seguenti: **Dimensioni intervallo server di pubblicazione**, **Dimensioni intervallo Sottoscrittore** e **Percentuale soglia intervallo**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Fare clic su **OK** nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 È possibile utilizzare stored procedure di replica per specificare le opzioni di gestione degli intervalli di valori Identity durante la creazione di un articolo.  
  
#### <a name="to-enable-automatic-identity-range-management-when-defining-articles-for-a-transactional-publication"></a>Per abilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione transazionale  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql). Se la tabella di origine da pubblicare include una colonna Identity, specificare il valore **auto** per **@identityrangemanagementoption**, l'intervallo di valori Identity assegnati al server di pubblicazione per **@pub_identity_range**, l'intervallo di valori Identity assegnato a ciascun Sottoscrittore per **@identity_range**e la percentuale dei valori Identity totali utilizzata prima dell'assegnazione di un nuovo intervallo di valori Identity per **@threshold**. Per altre informazioni sulla definizione degli articoli, vedere [Definire un articolo](define-an-article.md).  
  
    > [!NOTE]  
    >  Assicurarsi che il tipo di dati della colonna Identity sia sufficiente per supportare l'intervallo totale di valori Identity da assegnare a tutti i Sottoscrittori.  
  
#### <a name="to-disable-automatic-identity-range-management-when-defining-articles-for-a-transactional-publication"></a>Per disabilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione transazionale  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql). Specificare il valore **manual** per **@identityrangemanagementoption**. Per altre informazioni sulla definizione degli articoli, vedere [Definire un articolo](define-an-article.md).  
  
2.  Assegnare intervalli a colonne Identity dell'articolo nel Sottoscrittore per evitare di generare conflitti durante l'aggiornamento dei Sottoscrittori. Per altre informazioni, vedere la sezione relativa all'assegnazione di intervalli per la gestione manuale degli intervalli di valori Identity nell'argomento [Replicare colonne Identity](replicate-identity-columns.md).  
  
#### <a name="to-enable-automatic-identity-range-management-when-defining-articles-for-a-merge-publication"></a>Per attivare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione di tipo merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Se la tabella di origine da pubblicare include una colonna Identity, specificare il valore **auto** per **@identityrangemanagementoption**, l'intervallo di valori Identity assegnati a una sottoscrizione server per **@pub_identity_range**, l'intervallo di valori Identity assegnato al server di pubblicazione e a ogni sottoscrizione client per **@identity_range**e la percentuale dei valori Identity totali utilizzata prima dell'assegnazione di un nuovo intervallo di valori Identity per **@threshold**. Per altre informazioni sull'assegnazione di nuovi intervalli di valori Identity, vedere "Assegnazione degli intervalli di valori Identity" nell'argomento [Replicare colonne Identity](replicate-identity-columns.md). Per altre informazioni sulla definizione degli articoli, vedere [Definire un articolo](define-an-article.md).  
  
    > [!NOTE]  
    >  Assicurarsi che il tipo di dati della colonna Identity sia sufficiente per supportare l'intervallo totale di valori Identity da assegnare a tutti i Sottoscrittori, in particolare ai Sottoscrittori con sottoscrizioni server.  
  
#### <a name="to-disable-automatic-identity-range-management-when-defining-articles-for-a-merge-publication"></a>Per disabilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione di tipo merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Specificare uno dei valori seguenti per **@identityrangemanagementoption**:  
  
    -   **manual** : per aggiornare i Sottoscrittori, gli intervalli di valori Identity devono essere assegnati manualmente.  
  
    -   **none** : le colonne Identity del server di pubblicazione non verranno definite come tali nel Sottoscrittore.  
  
     Per altre informazioni sulla definizione degli articoli, vedere [Definire un articolo](define-an-article.md).  
  
2.  Assegnare intervalli a colonne Identity dell'articolo nel Sottoscrittore per evitare di generare conflitti durante l'aggiornamento dei Sottoscrittori.  
  
#### <a name="to-change-automatic-identity-range-management-settings-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>Per modificare le impostazioni relative alla gestione automatica degli intervalli di valori Identity per un articolo esistente di una pubblicazione snapshot o transazionale  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql) e notare il valore di **identityrangemanagementoption** nel set di risultati. Se questo valore è **0**, la gestione automatica degli intervalli di valori Identity non è attivata.  
  
2.  Se il valore di **identityrangemanagementoption** nel set di risultati è **1**, modificare le impostazioni nel modo seguente:  
  
    -   Per modificare gli intervalli di valori Identity assegnati, eseguire [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) nel database di pubblicazione del server di pubblicazione. Specificare il valore **identity_range** o **pub_identity_range** per **@property** e il nuovo valore dell'intervallo per **@value**.  
  
    -   Per modificare la soglia di assegnazione di nuovi intervalli, eseguire [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) nel database di pubblicazione del server di pubblicazione. Specificare il valore **threshold** per **@property** e il nuovo valore soglia per **@value**.  
  
#### <a name="to-change-automatic-identity-range-management-settings-for-an-existing-article-in-a-merge-publication"></a>Per modificare le impostazioni relative alla gestione automatica degli intervalli di valori Identity per un articolo esistente di una pubblicazione di tipo merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) e notare il valore di **identity_support** nel set di risultati. Se questo valore è **0**, la gestione automatica degli intervalli di valori Identity non è attivata.  
  
2.  Se il valore di **identity_support** nel set di risultati è **1**, modificare le impostazioni nel modo seguente:  
  
    -   Per modificare gli intervalli di valori Identity assegnati, eseguire [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) nel database di pubblicazione del server di pubblicazione. Specificare il valore **identity_range** o **pub_identity_range** per **@property** e il nuovo valore dell'intervallo per **@value**.  
  
    -   Per modificare la soglia di assegnazione di nuovi intervalli, eseguire [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) nel database di pubblicazione del server di pubblicazione. Specificare il valore **threshold** per **@property** e il nuovo valore soglia per **@value**. Per altre informazioni sull'assegnazione di nuovi intervalli di valori Identity, vedere "Assegnazione degli intervalli di valori Identity" nell'argomento [Replicare colonne Identity](replicate-identity-columns.md).  
  
    -   Per disabilitare la gestione automatica degli intervalli di valori Identity, eseguire [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) nel database di pubblicazione del server di pubblicazione. Specificare il valore **identityrangemanagementoption** per **@property** e **manual** o **none** per **@value**.  
  
## <a name="see-also"></a>Vedere anche  
 [Peer-to-Peer Transactional Replication](../transactional/peer-to-peer-transactional-replication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Replicare colonne Identity](replicate-identity-columns.md)  
  
  
