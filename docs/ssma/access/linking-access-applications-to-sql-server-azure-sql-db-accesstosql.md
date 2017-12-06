---
title: 'Collegamento alle applicazioni di accesso di SQL Server: database SQL di Azure | Documenti Microsoft'
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, linking to SQL Azure
- Access databases, linking to SQL Server
- auto-increment columns
- data types, unsupported
- hyperlink columns
- linking tables
- migrating databases, post-migration issues
- post-migration issues
- reference, post-migration issues
- refreshing linked tables
- slow performance
- unlinking tables
ms.assetid: 82374ad2-7737-4164-a489-13261ba393d4
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: b4ac30b2c0275de85f7ebab7cb8c7d0876f3142f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>Il collegamento alle applicazioni di accesso di SQL Server: database SQL di Azure (AccessToSQL)
Se si desidera utilizzare le applicazioni Access esistenti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile collegare le tabelle di Access originale dopo la migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure. Collegamento di modifica nel database di Access in modo che i dati di utilizzare pagine di accesso ai dati, moduli, report e query di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure anziché i dati nel database di Access.  
  
> [!NOTE]  
> Le tabelle di Access rimangono in Access, ma non vengono aggiornate con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli aggiornamenti di SQL Azure. Dopo si collegano le tabelle e verificare la funzionalità, è possibile eliminare le tabelle di Access.  
  
## <a name="linking-access-and-sql-server-tables"></a>Il collegamento delle tabelle di Access e SQL Server  
Quando si collega una tabella di accesso per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabella di SQL Azure, il motore di database Jet archivia le informazioni di connessione e i metadati della tabella, ma i dati vengono archiviati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Questo collegamento consente le applicazioni Access funzionano a fronte delle tabelle del database anche se le tabelle effettive e i dati sono [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure.  
  
> [!NOTE]  
> Se si utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, la password viene archiviato in testo non crittografato in tabelle collegate di Access. È consigliabile utilizzare l'autenticazione di Windows.  
  
**Per collegare le tabelle**  
  
1.  In Visualizzatore metadati di accesso, selezionare le tabelle che si desidera collegare.  
  
2.  Fare doppio clic su **tabelle**, quindi selezionare **collegamento**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) per l'accesso viene eseguito il backup della tabella di accesso originale e crea una tabella collegata.  
  
Dopo aver collegato le tabelle, le tabelle in SSMA vengono visualizzati con un'icona di collegamento di piccole dimensioni. In Access, le tabelle vengono visualizzati con un'icona di "collegata", ovvero un globo con una freccia con punta a esso.  
  
Quando si apre una tabella in Access, i dati vengono recuperati utilizzando un cursore keyset. Di conseguenza, per le tabelle di grandi dimensioni, tutti i dati non vengono recuperati contemporaneamente. Tuttavia, durante l'esplorazione tramite la tabella, accesso recupera dati aggiuntivi in base alle esigenze.  
  
> [!IMPORTANT]  
> Per collegare le tabelle di access con un database di Azure, è necessario Client(SNAC) nativo di SQL Server versione 10.5 o versione successiva.   
> È possibile ottenere la versione più recente di SNAC da [Microsoft® SQL Server® 2008 R2 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=196940).  
  
## <a name="unlinking-access-tables"></a>Scollegamento di tabelle di Access  
Quando si scollega una tabella di Access da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabella di SQL Azure, SSMA consente di ripristinare la tabella di accesso originale e i relativi dati.  
  
**Per eliminare il collegamento delle tabelle**  
  
1.  In Visualizzatore metadati di accesso, selezionare le tabelle che si desidera scollegare.  
  
2.  Fare doppio clic su **tabelle**, quindi selezionare **Scollega**.  
  
## <a name="linking-tables-to-a-different-server"></a>Collegamento delle tabelle in un altro server  
Se sono state collegate delle tabelle del database a un'istanza di SQL Server e in seguito si desidera modificare i collegamenti a un'altra istanza, è necessario collegare nuovamente le tabelle.  
  
**Per collegare le tabelle in un altro server**  
  
1.  In Visualizzatore metadati di accesso, selezionare le tabelle che si desidera scollegare.  
  
2.  Fare doppio clic su **tabelle** e quindi selezionare **Scollega**.  
  
3.  Fare clic su di **Riconnetti a SQL Server** pulsante.  
  
4.  Connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o a cui si desidera collegare le tabelle di accesso di SQL Azure.  
  
5.  In Visualizzatore metadati di accesso, selezionare le tabelle che si desidera collegare.  
  
6.  Fare doppio clic su **tabelle**, quindi selezionare **collegamento**.  
  
## <a name="updating-linked-tables"></a>Aggiornamento delle tabelle collegate  
Se il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o le definizioni delle tabelle di SQL Azure vengono modificati, è possibile scollegare e quindi collegare le tabelle in SSMA nuovamente utilizzando le procedure illustrate in precedenza in questo argomento. È inoltre possibile aggiornare le tabelle utilizzando l'accesso.  
  
**Per aggiornare le tabelle collegate tramite accesso**  
  
1.  Aprire il database di Access.  
  
2.  Nel **oggetti** elenco, fare clic su **tabelle**.  
  
3.  Fare doppio clic su una tabella collegata e quindi selezionare **Gestione tabelle collegate**.  
  
4.  Selezionare la casella di controllo accanto a ogni tabella collegata che si desidera aggiornare e quindi fare clic su **OK**.  
  
## <a name="possible-post-migration-issues"></a>Possibili problemi di post-migrazione  
Le sezioni seguenti problemi di elenco che si verificano in applicazioni Access esistenti dopo la migrazione di database da Access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e quindi collegare le tabelle, nonché le cause e le risoluzioni.  
  
### <a name="slow-performance-with-linked-tables"></a>Rallentamento delle prestazioni con le tabelle collegate  
**Causa:** alcune query può essere lenta dopo upsizing per i motivi seguenti:  
  
-   L'applicazione dipende dalle funzioni che non esistono in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, provocando Jet per tabelle in locale per eseguire una query di selezione a discesa.  
  
-   Le query che aggiornano o eliminano molte righe vengono inviate da Jet come una query con parametri per ogni riga.  
  
**Risoluzione:** convertire le query con esecuzione prolungata in viste, stored procedure o query pass-through. La conversione in una query pass-through presenta i seguenti problemi:  
  
-   Query pass-through non può essere modificata. Modifica il risultato della query o l'aggiunta di nuovi record deve essere effettuata in un modo alternativo, ad esempio richiedendo esplicita **modifica** o **Aggiungi** pulsanti nel form di cui è associato alla query.  
  
-   Alcune query richiedono l'input dell'utente, ma le query pass-through non supportano l'input dell'utente. Da Visual Basic per il codice richiesto per i parametri Applications (VBA) o da un modulo viene utilizzato come un controllo di input, è possibile ottenere l'input dell'utente. In entrambi i casi, il codice VBA invia la query con l'input dell'utente al server.  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>Colonne a incremento automatico non vengono aggiornate finché non viene aggiornato il record  
**Causa:** dopo la chiamata a RecordSet.AddNew Jet, la colonna a incremento automatico è disponibile prima che il record viene aggiornato. Ciò non è possibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Il nuovo valore il nuovo valore della colonna identity è disponibile solo dopo aver salvato il nuovo record.  
  
**Risoluzione:** nell'esempio di Visual Basic, Applications Edition (VBA) di eseguire prima l'accesso al campo di identità:  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>Nuovi record non sono disponibili  
**Causa:** quando si aggiunge un record per un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o una tabella di SQL Azure utilizzando VBA, se il campo della tabella dell'indice univoco ha un valore predefinito e non si assegna un valore per tale campo non viene visualizzato il nuovo record fino a quando non si riapre la tabella in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Se si tenta di ottenere un valore del nuovo record, è visualizzato il messaggio di errore seguente:  
  
`Run-time error '3167' Record is deleted.`  
  
**Risoluzione:** quando si apre il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure tramite il codice VBA di tabella, includere il `dbSeeChanges` opzione, come nell'esempio seguente:  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>Dopo la migrazione, alcune query non consentirà all'utente di aggiungere un nuovo record  
**Causa:** se una query non include tutte le colonne incluse in un indice univoco, è possibile aggiungere nuovi valori utilizzando la query.  
  
**Risoluzione:** verificare che tutte le colonne incluse in almeno un indice univoco facciano parte della query.  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Non è possibile modificare uno schema di tabella collegata con accesso  
**Causa:** dopo la migrazione dei dati e le tabelle di collegamento, l'utente non è possibile modificare lo schema di una tabella di accesso.  
  
**Risoluzione:** modificare lo schema della tabella utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]e quindi aggiornare il collegamento di accesso.  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>Funzionalità di collegamento ipertestuale viene persa dopo la migrazione dei dati  
**Causa:** dopo la migrazione dei dati, i collegamenti ipertestuali nelle colonne perdono le proprie funzionalità e sarà più facile **nvarchar (max)** colonne.  
  
**Risoluzione:** nessuno.  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>Alcuni tipi di dati di SQL Server non sono supportati da Access  
**Causa:** se si aggiorna successivamente il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tabelle di SQL Azure per contenere i tipi di dati che non sono supportati da Access, accesso non è possibile aprire la tabella.  
  
**Risoluzione:** è possibile definire una query di accesso che restituisce solo le righe con tipi di dati supportati.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
