---
title: Editor destinazione ADO NET (pagina Gestione connessione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.connection.f1
ms.assetid: a3b11286-32c8-40e1-8ae7-090e2590345a
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 887f881ad6a4cefec80620ebedb2ac210692ce5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090098"
---
# <a name="ado-net-destination-editor-connection-manager-page"></a>Editor destinazione ADO NET (pagina Gestione connessione)
  Usare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione ADO NET** per selezionare la connessione [!INCLUDE[vstecado](../includes/vstecado-md.md)] per la destinazione. Tramite questa pagina è inoltre possibile selezionare una tabella o una vista del database.  
  
 Per ulteriori informazioni sulla destinazione ADO NET, vedere [ADO NET Destination](data-flow/ado-net-destination.md).  
  
 **Per aprire la pagina Gestione connessione**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], aprire il pacchetto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] con la destinazione ADO NET.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sulla destinazione ADO NET.  
  
3.  In **Editor destinazione ADO NET**fare clic su **Gestione connessione**.  
  
## <a name="static-options"></a>Opzioni statiche  
 **Connection manager**  
 Selezionare una gestione connessione esistente nell'elenco o crearne una nuova facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione usando la finestra di dialogo **Configura gestione connessione ADO.NET** .  
  
 **Tabella o vista**  
 Consente di selezionare una tabella o vista esistente nell'elenco oppure di creare una nuova tabella facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova tabella o vista usando la finestra di dialogo **Crea tabella** .  
  
> [!NOTE]  
>  Quando si fa clic su **Nuova**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] genera un'istruzione CREATE TABLE predefinita basata sull'origine dati connessa. Questa istruzione CREATE TABLE predefinita non includerà l'attributo FILESTREAM anche se la tabella di origine include una colonna con l'attributo FILESTREAM dichiarato. Per eseguire un componente [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] con l'attributo FILESTREAM, implementare innanzitutto l'archiviazione di FILESTREAM nel database di destinazione. Aggiungere quindi l'attributo FILESTREAM all'istruzione CREATE TABLE nella finestra di dialogo **Crea tabella**. Per altre informazioni, vedere [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Anteprima risultati query** . L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
 **Utilizza inserimento bulk, se disponibile**  
 Specificare se usare l'interfaccia <xref:System.Data.SqlClient.SqlBulkCopy> per migliorare le prestazioni delle operazioni di inserimento bulk.  
  
 Solo i provider ADO.NET che restituiscono un oggetto <xref:System.Data.SqlClient.SqlConnection> supportano l'uso dell'interfaccia <xref:System.Data.SqlClient.SqlBulkCopy> . Il provider di dati .NET per SQL Server (SqlClient) restituisce un oggetto <xref:System.Data.SqlClient.SqlConnection> e un provider personalizzato può restituire un oggetto <xref:System.Data.SqlClient.SqlConnection> .  
  
 È possibile usare il Provider di dati .NET per SQL Server (SqlClient) per connettersi a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].  
  
 Se si seleziona **Usa Inserimento bulk quando possibile**e si imposta l'opzione **Errore** su **Reindirizza riga**, il batch di dati che la destinazione reindirizza all'output degli errori può includere righe corrette. Per altre informazioni sulla gestione degli errori nelle operazioni bulk, vedere [Gestione degli errori nei dati](data-flow/error-handling-in-data.md). Per altre informazioni sul **errore** opzione, vedere [Editor destinazione ADO NET &#40;pagina Output degli errori&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md).  
  
> [!NOTE]  
>  Se una tabella di origine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o Sybase include una colonna Identity, è necessario utilizzare Esegui attività di SQL per eseguire un'istruzione SET IDENTITY_INSERT prima e dopo la destinazione di ADO NET. La proprietà della colonna Identity specifica un valore incrementale per la colonna. L'istruzione SET IDENTITY_INSERT consente l'inserimento di valori espliciti nella colonna Identity. Per eseguire le istruzioni CREATE TABLE e SET IDENTITY sulla stessa connessione al database, impostare il `RetainSameConnection` proprietà del [!INCLUDE[vstecado](../includes/vstecado-md.md)] gestione connessione da `True`. Inoltre, utilizzare la stessa gestione connessione [!INCLUDE[vstecado](../includes/vstecado-md.md)] per le attività Esegui SQL e la destinazione ADO NET.  
>   
>  Per altre informazioni, vedere [SET IDENTITY_INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-identity-insert-transact-sql) e [IDENTITY &#40;proprietà&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).  
  
## <a name="external-resources"></a>Risorse esterne  
 Articolo tecnico [Loading data to Windows Azure SQL Database the fast way](http://go.microsoft.com/fwlink/?LinkId=244333)(Modalità rapida di caricamento di dati nel database SQL di Windows Azure) nel sito Web sqlcat.com  
  
## <a name="see-also"></a>Vedere anche  
 [Editor destinazione ADO NET &#40;pagina mapping&#41;](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)   
 [Editor destinazione ADO NET &#40;pagina dell'Output degli errori&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)   
 [Gestione connessione ADO.NET](connection-manager/ado-net-connection-manager.md)   
 [Attività Esegui SQL](control-flow/execute-sql-task.md)  
  
  
