---
title: Schermata 1, il Driver ODBC per SQL Server, dell'origine dati | Documenti Microsoft
ms.custom: 
ms.date: 09/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 7529882acd6a96576c95c18c368397f58df1aa40
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="data-source-wizard-screen-1"></a>Schermata di creazione guidata origine dati 1

Specificare il nome e descrizione dell'origine dati e il nome del server che esegue SQL Server a cui si connetterà l'origine dati. 
    
## <a name="options"></a>Opzioni

### <a name="name"></a>Nome

Nome dell'origine dati utilizzato da un'applicazione ODBC quando richiede una connessione all'origine dati, ad esempio "Personale". Il nome dell'origine dati è visualizzato nella finestra di dialogo Amministrazione origine dati ODBC.

### <a name="description"></a>Description

Descrizione facoltativa dell'origine dati, ad esempio "Date collaborazioni, cronologia stipendi e situazione corrente di tutti i dipendenti".

### <a name="select-or-enter-a-server-name"></a>Selezionare o immettere il nome di un server

Il nome di un'istanza di SQL Server nella rete. Sarà necessario specificare un server nella casella di modifica successiva.

Nella maggior parte dei casi, il driver ODBC è possibile connettersi utilizzando l'ordine dei protocolli predefinito e il nome del server fornito in questa casella. Se si desidera creare un alias per il server o configurare librerie di rete client, utilizzare Gestione configurazione SQL Server.

È possibile immettere "(local)" nella finestra di server quando si utilizza lo stesso computer di SQL Server. L'utente può quindi connettersi all'istanza locale di SQL Server, anche quando si esegue una versione non in rete di SQL Server. Più istanze di SQL Server è possono eseguire nello stesso computer. Per specificare un'istanza denominata di SQL Server, il nome del server viene specificato come _ServerName_\\_InstanceName_.

Per ulteriori informazioni sui nomi di server per diversi tipi di reti, vedere la documentazione di installazione di SQL Server nella documentazione Online di SQL Server.

### <a name="finish"></a>Fine

Se le informazioni specificate in questa schermata sono tutto ciò che è necessaria per connettersi a SQL Server, è possibile fare clic su **fine**. Per tutti gli attributi specificati nelle altre schermate della procedura guidata verranno utilizzate le impostazioni predefinite.

### <a name="next"></a>Avanti

Per passare alla schermata successiva della procedura guidata, fare clic su **Avanti**.

## <a name="next-steps"></a>Passaggi successivi

[Schermata di creazione guidata origine dati 2](../../../connect/odbc/windows/dsn-wizard-2.md)

