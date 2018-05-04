---
title: L'installazione di SQL Server Migration Assistant per Access (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
caps.latest.revision: 31
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4232c955646b44be8c1d41a9095146a47aa75e97
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>L'installazione di SQL Server Migration Assistant per Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) per l'accesso è stato installato utilizzando una procedura guidata basata su Windows Installer. In questo argomento fornisce informazioni sui prerequisiti di installazione, un collegamento all'ultima versione di SSMA e istruzioni per l'installazione, licenze, la disinstallazione e l'aggiornamento di SSMA.  
  
## <a name="prerequisites"></a>Prerequisiti  
Prima di installare SSMA, assicurarsi che il sistema soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive, o Windows Server 2008 o versione successiva.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework versione 4.0 o versione successiva. È disponibile in .NET Framework versione 4.0 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] disco del prodotto e con le informazioni nel [Guida di Microsoft .NET](https://docs.microsoft.com/en-us/dotnet/framework/).
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]database SQL di Azure a cui si desidera migrare gli oggetti di database e i dati.  
  
-   Microsoft oggetto DAO (Data Access) versione 12.0 o 14.0 del provider. È possibile installare il provider DAO dal prodotto di Microsoft Office 2010 o 2007 o scaricarlo dal sito web Microsoft.  
  
-   Il SQL Server Native Access Client (SNAC) versione 10.5 e versioni successive per la migrazione a SQL Azure. È possibile ottenere la versione più recente di SNAC da [Feature Pack di Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB di RAM (consigliato).  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmaforaccess).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione da prima di poter installare SSMA.

> [!IMPORTANT]  
> -   Disinstallare tutte le versioni precedenti di SSMA per l'accesso prima di installare la nuova versione.  
  
**Per installare SSMA**  
  
1.  Fare doppio clic su SSMA per Access *n*con estensione msi, in cui *n* è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, viene visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di avere installato tutti i prerequisiti e quindi eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza dell'utente finale. Se si accetta, selezionare **accetto il contratto**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per Access.  
  
## <a name="uninstalling-ssma-for-access"></a>La disinstallazione di SSMA per l'accesso  
Disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi** nel Pannello di controllo. Tenere presente che il programma di disinstallazione non eliminare i file di progetto SSMA o file di log.  
  
**Per disinstallare di SSMA**  
  
1.  Fare clic su **avviare**, fare clic su **Pannello di controllo**, quindi fare clic su **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Access**, quindi fare clic su **rimuovere**.  
  
## <a name="upgrading-to-a-later-version"></a>L'aggiornamento a una versione successiva  
Se si desidera eseguire l'aggiornamento a una versione successiva di SSMA per l'accesso, è necessario prima disinstallare SSMA per l'accesso e quindi installare la versione più recente. Seguire le istruzioni in SSMA disinstallazione per la sezione di accesso completare questo processo.  
  
Se si apre un progetto creato in una versione precedente di SSMA per l'accesso, SSMA viene chiesto se si desidera convertire il progetto alla versione più recente. Fare clic su **Sì** per funzionare con il progetto alla versione più recente di SSMA.  
  
## <a name="see-also"></a>Vedere anche  
[Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[La migrazione dei database di Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Collegamento applicazioni l'accesso a SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
