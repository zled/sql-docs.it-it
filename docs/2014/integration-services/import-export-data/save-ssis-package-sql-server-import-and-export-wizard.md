---
title: Salvare il pacchetto SSIS (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 71f0b516b53a7682665c54be4403c5d10a4e5417
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167702"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>Salva pacchetto SSIS (Importazione/Esportazione guidata SQL Server)
  Utilizzare la **Salva pacchetto SSIS** pagina per denominare, descrivere e salvare un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) del pacchetto per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` del database o a un file che ha l'estensione dtsx estensione.  
  
> [!NOTE]  
>  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'opzione per salvare il pacchetto creato dalla procedura guidata non è disponibile.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [SQL Server di importazione / esportazione guidata](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Per ulteriori informazioni sulle opzioni di avvio della procedura guidata e sulle autorizzazioni necessarie per eseguire correttamente la procedura guidata, vedere [eseguire il Server importazione / esportazione guidata SQL](start-the-sql-server-import-and-export-wizard.md).  
  
 Lo scopo di Importazione/Esportazione guidata SQL Server è la copia di dati da un'origine a una destinazione. La procedura guidata può inoltre creare automaticamente un database di destinazione e le tabelle di destinazione. Se tuttavia è necessario copiare più database o tabelle, o altri tipi di oggetti di database, è preferibile utilizzare Copia guidata database. Per altre informazioni, vedere [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Opzioni statiche  
 **Nome**  
 Consente di specificare un nome univoco per il pacchetto.  
  
 **Descrizione**  
 Consente di specificare una descrizione per il pacchetto. È consigliabile includere nella descrizione informazioni sugli scopi del pacchetto, in modo da ottenere pacchetti autodocumentati più semplici da gestire.  
  
 **Destinazione**  
 Visualizzare la destinazione ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o file) che è stata specificata in precedenza per il file di destinazione.  
  
## <a name="target-dynamic-options"></a>Opzioni dinamiche di Destinazione  
  
### <a name="target--sql-server"></a>Destinazione = SQL Server  
 **Nome server**  
 Se è stata selezionata una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], digitare o selezionare il nome del server di destinazione.  
  
 **Usa autenticazione di Windows**  
 Se è stata selezionata una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare se connettersi al server utilizzando l'autenticazione integrata di Windows. Questo è il metodo di autenticazione ottimale.  
  
 **Usa autenticazione di SQL Server**  
 Se è stata selezionata una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione, specificare se connettersi al server tramite l'autenticazione di SQL Server.  
  
 **Nome utente**  
 Se è stata selezionata una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione, ed è stata specificata l'autenticazione di SQL Server, digitare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nome utente.  
  
 **Password**  
 Se è stata selezionata una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destinazione, ed è stata specificata l'autenticazione di SQL Server, digitare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] password.  
  
### <a name="target--file-system"></a>Destinazione = File System  
 **Nome file**  
 Dopo aver selezionato una destinazione file, digitare il percorso del file di destinazione, oppure usare il **Sfoglia** pulsante.  
  
 **Sfoglia**  
 Dopo aver selezionato una destinazione file, selezionare il file di destinazione utilizzando il **Salva pacchetto** finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i pacchetti](../save-packages.md)  
  
  