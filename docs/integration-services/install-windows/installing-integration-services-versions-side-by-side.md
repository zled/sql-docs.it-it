---
title: Installazione di Integration Services versioni Side-by | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d642d8d9d732a51c210e5d83cecf2b090ac2f426
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="installing-integration-services-versions-side-by-side"></a>Installazione side-by-side di versioni di Integration Services
  È possibile installare   
      [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Integration Services (SSIS) side-by-side con versioni precedenti di SSIS. Questo argomento descrive alcune limitazioni delle installazioni side-by-side.  
  
## <a name="designing-and-maintaining-packages"></a>Progettazione e gestione dei pacchetti  
 Per progettare e gestire pacchetti destinati a SQL Server 2016, SQL Server 2014 o SQL Server 2012 usare SQL Server Data Tools (SSDT) per Visual Studio 2015. Per ottenere SSDT, vedere [Scaricare la versione più recente di SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
 Nelle pagine delle proprietà per un progetto di Integration Services, nella scheda **Generale** di **Proprietà di configurazione**selezionare la proprietà **TargetServerVersion** , quindi scegliere SQL Server 2016, SQL Server 2014 o SQL Server 2012.  
  
|Versione di destinazione di SQL Server|Ambiente di sviluppo per pacchetti SSIS|  
|----------------------------------|-----------------------------------------------|  
|2016|SQL Server Data Tools per Visual Studio 2015|  
|2014|SQL Server Data Tools per Visual Studio 2015<br /><br /> o<br /><br /> SQL Server Data Tools - Business Intelligence per Visual Studio 2013|  
|2012|SQL Server Data Tools per Visual Studio 2015<br /><br /> o<br /><br /> SQL Server Data Tools - Business Intelligence per Visual Studio 2012|  
|2008|Business Intelligence Development Studio in SQL Server 2008|  
  
 Quando si aggiunge un pacchetto esistente a un progetto esistente, il pacchetto viene convertito nel formato di destinazione dal progetto.  
  
## <a name="running-packages"></a>Esecuzione di pacchetti  
 È possibile usare la versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dell'utilità **dtexec** o di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per eseguire i pacchetti di Integration Services creati nelle versioni precedenti degli strumenti di sviluppo. Quando gli strumenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] caricano un pacchetto sviluppato in una versione precedente degli strumenti di sviluppo, lo strumento converte temporaneamente il pacchetto in memoria nel formato pacchetto usato da [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] . Se il pacchetto presenta problemi che impediscono la conversione, lo strumento [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] non riesce a eseguire il pacchetto fino a quando tali problemi non vengono risolti. Per altre informazioni, vedere [Aggiornare pacchetti di Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
  
