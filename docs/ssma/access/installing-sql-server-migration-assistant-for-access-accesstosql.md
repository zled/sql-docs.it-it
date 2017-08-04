---
title: L'installazione di SQL Server Migration Assistant per Access (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
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
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2915318b5bbe85ad21a5e5095a7322013dfa7b44
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>L'installazione di SQL Server Migration Assistant per Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) per l'accesso viene installata usando una procedura guidata basata su Windows Installer. In questo argomento fornisce informazioni sui prerequisiti di installazione, un collegamento all'ultima versione di SSMA e istruzioni per l'installazione, licenze, la disinstallazione e l'aggiornamento di SSMA.  
  
## <a name="prerequisites"></a>Prerequisiti  
Prima di installare SSMA, assicurarsi che il sistema soddisfi i requisiti seguenti:  
  
-   Windows 7 o versioni successive, o Windows Server 2008 o versione successiva.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3.1 o versione successiva.  
  
-   Il [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework versione 4.0 o versione successiva. È disponibile in .NET Framework versione 4.0 di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] disco del prodotto e dal [Microsoft .NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=48882) sito Web.  
  
-   Per l'accesso e autorizzazioni sufficienti nel computer che ospita l'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]database SQL di Azure in cui si desidera migrare gli oggetti di database e i dati.  
  
-   DAO provider versione 12.0 o 14.0. È possibile installare il provider DAO dal prodotto di Microsoft Office 2010 o 2007 o scaricarlo dal sito web Microsoft.  
  
-   Il SQL Server Native Access Client (SNAC) versione 10.5 e versioni successive per la migrazione a SQL Azure. È possibile ottenere la versione più recente di SNAC da [Feature Pack di Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB di RAM consigliato.  
  
## <a name="installing-ssma"></a>L'installazione di SSMA  
SSMA è un download Web. Per scaricare la versione più recente, vedere il [pagina di download di SQL Server Migration Assistant](http://aka.ms/ssmaforaccess).  
  
Dopo aver scaricato la versione più recente, è necessario estrarre i file di installazione da prima di poter installare SSMA.  
  
**Per installare SSMA**  
  
1.  Fare doppio clic su SSMA per l'accesso  *n* . Install.exe, in cui  *n*  è il numero di build.  
  
2.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
    Se non si dispone di installati i prerequisiti, verrà visualizzato un messaggio che indica che è necessario innanzitutto installare i componenti necessari. Assicurarsi di avere installato tutti i prerequisiti e quindi eseguire nuovamente il programma di installazione.  
  
3.  Leggere il contratto di licenza. Se si accetta, selezionare **accetto i termini del contratto di licenza**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
5.  Fare clic su **Installa**.  
  
> [!IMPORTANT]  
> 1.  Disinstallare tutte le versioni precedenti di SSMA per l'accesso prima di installare la nuova versione.  
  
Il percorso di installazione predefinito è C:\Program Files\Microsoft SQL Server Migration Assistant per Access.  
  
## <a name="uninstalling-ssma-for-access"></a>La disinstallazione di SSMA per l'accesso  
Disinstallare SSMA utilizzando **Aggiungi / Rimuovi programmi** nel Pannello di controllo. Tenere presente che il programma di disinstallazione non eliminare i file di progetto SSMA o i file di log.  
  
**Per disinstallare SSMA**  
  
1.  Fare clic su **avviare**, fare clic su **Pannello di controllo**, quindi fare clic su **Aggiungi / Rimuovi programmi**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Access**, quindi fare clic su **rimuovere**.  
  
## <a name="upgrading-to-a-later-version"></a>L'aggiornamento a una versione successiva  
Se si desidera eseguire l'aggiornamento a una versione successiva di SSMA per l'accesso, è necessario prima disinstallare SSMA per l'accesso e quindi installare la versione più recente. Seguire le istruzioni in questo argomento per l'installazione e disinstallazione.  
  
Se si apre un progetto da una versione precedente di SSMA per l'accesso, SSMA chiederà se si desidera convertire il progetto alla versione più recente. È necessario fare clic su **Sì** per funzionare con il progetto alla versione più recente di SSMA.  
  
## <a name="see-also"></a>Vedere anche  
[Preparazione dei database di Access per la migrazione](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Il collegamento alle applicazioni di accesso di SQL Server](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)  
  

