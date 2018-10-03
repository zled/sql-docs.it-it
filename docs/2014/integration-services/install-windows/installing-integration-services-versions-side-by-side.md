---
title: Interoperabilità e coesistenza (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9f5b9bcd179e5485ad4959df02fd0b05b638998f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200891"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Interoperabilità e coesistenza (Integration Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) può coesistere in modalità affiancata con [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services e [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services.  
  
## <a name="features-and-differences"></a>Funzionalità e differenze  
 Nella tabella seguente sono riportate alcune delle differenze esistenti tra la versione corrente e le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Funzionalità|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Ambiente di sviluppo|[SQL Server 2014 Data Tools – Business Intelligence per Visual Studio 2012 CTP 2](http://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence per Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Data Tools per Visual Studio 2010](http://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools – Business Intelligence per Visual Studio 2012](http://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Ambiente di gestione|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Tabella di sistema principale in msdb per l'archivio di pacchetti|sysssispackages|sysssispackages|sysssispackages|  
|Utilità del prompt dei comandi principale per i pacchetti in esecuzione|**dtexec** (dtexec.exe), versione 2014|**dtexec** (dtexec.exe), versione 2012|**dtexec** (dtexec.exe), versione 2008|  
|Cartella radice del file system predefinita|C:\Programmi\Microsoft SQL Server\120\DTS|C:\Programmi\Microsoft SQL Server\110\DTS|C:\Programmi\Microsoft SQL Server\100\DTS|  
|Chiave del Registro di sistema radice predefinita|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Problemi di compatibilità di installazioni side-by-side  
 Quando [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services è installato in modalità affiancata con [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services e [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services, è possibile eseguire le attività seguenti:  
  
-   **Progettare pacchetti in SQL Server Data Tools**. È possibile usare gli strumenti seguenti per sviluppare e gestire i pacchetti in base alle versioni corrispondenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Utilizzare la versione [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] di Business Intelligence Development Studio per sviluppare e gestire pacchetti basati su [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)].  
  
    -   Usare la [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] versione di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per sviluppare e gestire pacchetti basati su [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Usare la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] versione di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per sviluppare e gestire pacchetti basati su [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Caricare ed eseguire pacchetti**. È possibile caricare ed eseguire pacchetti sviluppati in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], nella [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] versione di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Quando si aggiunge il pacchetto a un progetto esistente, il pacchetto viene aggiornato in modo permanente al formato usato da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Quando si apre il file del pacchetto in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], il pacchetto viene aggiornato temporaneamente al formato usato da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Se si salva la modifica al pacchetto, quest'ultimo viene aggiornato in modo permanente. Una volta salvati nel formato che [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Usa i servizi di integrazione, i pacchetti non possono più essere aperti nel corrispondente [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oppure [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] versione di Business Intelligence Development Studio, né eseguiti dagli corrispondente [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services o [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] gli strumenti di Integration Services.  
  
-   **Gestire i pacchetti in SQL Server Management Studio**. Non è possibile connettersi a un'istanza del [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] versione del [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servizio, il [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o il [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] versione di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Non è possibile connettersi a un'istanza del [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o il [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] versione del [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] servizio il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] versione di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. È possibile utilizzare la versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per gestire pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] archiviati in un'istanza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. È necessario modificare il file di configurazione del servizio per aggiungere l'istanza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] all'elenco dei percorsi gestiti dal servizio. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Archiviare i pacchetti in SQL Server**. È possibile archiviare i pacchetti nei database seguenti.  
  
    |Formato pacchetto|Database|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services|database msdb di un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services|database msdb di un'istanza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services|database msdb di un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     In un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], è possibile importare pacchetti da un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o da un'istanza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ma è possibile esportare pacchetti in un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o a un'istanza di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
     In un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] non è possibile importare pacchetti da né esportare pacchetti in un'istanza della versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   **Eseguire i pacchetti**. È possibile eseguire [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services e [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pacchetti di Integration Services tramite il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] versione del **dtexec** utilità o di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'agente. Ogni volta che un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dello strumento di Integration Services carica un pacchetto sviluppato in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oppure [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lo strumento converte temporaneamente, in memoria, il pacchetto nel formato che [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] Usa. Se il [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oppure [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pacchetto presenta problemi che impediscono la conversione, il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] degli strumenti di Integration Services non è possibile eseguire il pacchetto fino a quando non vengono risolti i problemi. Per altre informazioni, vedere [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  
