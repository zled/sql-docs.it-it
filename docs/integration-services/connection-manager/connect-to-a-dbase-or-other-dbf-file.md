---
title: Connettersi a un file dBASE o a un altro file DBF | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: connection-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting to DBF files
- dBase files
- DBF files
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 27078fb038e9cee60a4da76a6548c648ea46085f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-a-dbase-or-other-dbf-file"></a>Connessione a un file dBASE o a un altro file DBF
  È possibile connettersi a un file dBASE o un altro file di database con estensione dbf in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilizzando una gestione connessione OLE DB e selezionando il provider Microsoft OLE DB per Jet 4.0.  
  
> [!NOTE]  
>  l'Importazione/Esportazione guidata SQL Server disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta l'importazione da o l'esportazione in file dBASE o altri file DBF. È possibile utilizzare Microsoft Access o Microsoft Excel per importare i dati dai file DBF in un database di Access o in fogli di calcolo di Excel e quindi utilizzare l'Importazione/Esportazione guidata SQL Server.  
  
### <a name="to-configure-a-connection-manager-to-connect-to-a-dbase-or-other-dbf-file"></a>Per configurare una gestione connessione per la connessione a un file dBASE o a un altro file DBF  
  
1.  Aggiungere una nuova gestione connessione OLE DB al pacchetto. Per altre informazioni, vedere [Add, Delete, or Share a Connection Manager in a Package](http://msdn.microsoft.com/library/6f2ba4ea-10be-4c40-9e80-7efcf6ee9655).  
  
2.  Nella pagina **Connessione** della finestra di dialogo **Gestione connessione** selezionare il provider OLE DB nativo o il provider OLE DB Microsoft Jet 4.0 come **Provider**.  
  
3.  Quando si utilizzano i file DBF, la cartella rappresenta il database e i singoli file DBF rappresentano le tabelle. La casella di testo **Nome file di database** deve pertanto contenere il percorso della cartella in cui si trova il file DBF e non deve includere il nome di file. È possibile digitare o incollare il percorso della cartella oppure usare il pulsante **Sfoglia** per selezionare il file DBF e quindi rimuovere il nome di file dalla parte finale del percorso.  
  
4.  Nella pagina **Tutte** della finestra di dialogo **Gestione connessione** immettere **dBASE III**, **dBASE IV**o **dBASE 5.0**, in base a quanto necessario, come valore delle proprietà estese.  
  
5.  Fare clic su **Test connessione** per convalidare i valori immessi. Verrà visualizzato il messaggio "Test della connessione riuscito". Fare clic su **OK** per chiudere la finestra di messaggio.  
  
6.  Fare clic su **OK** per salvare la configurazione per la gestione connessione.  
  
7.  Per utilizzare la gestione connessione nel flusso di dati del pacchetto, selezionare un'origine o una destinazione OLE DB e configurarla per l'utilizzo della gestione connessione creata tramite la procedura precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  
