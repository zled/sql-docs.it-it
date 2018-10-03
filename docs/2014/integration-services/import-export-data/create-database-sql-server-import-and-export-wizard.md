---
title: Crea database (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3720e3301eeffc73c8d89c901f2a4a337e1094d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099631"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a>Crea database (Importazione/Esportazione guidata SQL Server)
  Usare la **Create Database** pagina per definire un nuovo database per un file di destinazione.  
  
 Nella pagina è incluso un subset delle opzioni disponibili per la creazione di un nuovo database. Per visualizzare tutte le opzioni, utilizzare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Per altre informazioni su questa procedura guidata, vedere [SQL Server importazione / esportazione guidata](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Per altre informazioni sulle opzioni per l'avvio della procedura guidata e sulle autorizzazioni necessarie per eseguire correttamente la procedura guidata, vedere [esecuzione di SQL Server importazione / esportazione guidata](start-the-sql-server-import-and-export-wizard.md).  
  
 Lo scopo di Importazione/Esportazione guidata SQL Server è la copia di dati da un'origine a una destinazione. La procedura guidata può inoltre creare automaticamente un database di destinazione e le tabelle di destinazione. Se tuttavia è necessario copiare più database o tabelle, o altri tipi di oggetti di database, è preferibile utilizzare Copia guidata database. Per altre informazioni, vedere [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di specificare un nome univoco per il database di SQL Server di destinazione. Accertarsi di rispettare le convenzioni di denominazione dei database di SQL Server.  
  
 **Nome file di dati**  
 Consente di visualizzare il nome del file di dati. Tale nome è tratto dal nome del database specificato precedentemente.  
  
 **Nome file di log**  
 Consente di visualizzare il nome del file di log. Tale nome è tratto dal nome del database specificato precedentemente.  
  
 **Dimensioni iniziali (file di dati)**  
 Consente di specificare il numero di megabyte per le dimensioni iniziali del file di dati.  
  
 **Aumento dimensioni non consentito (file di dati)**  
 Consente di indicare se le dimensioni del file di dati possono eccedere le dimensioni iniziali specificate.  
  
 **Aumento dimensioni in percentuale (file di dati)**  
 Consente di specificare che le dimensioni del file di dati possono aumentare in base a un valore percentuale.  
  
 **Aumento dimensioni (file di dati)**  
 Consente di specificare che le dimensioni del file di dati possono aumentare in base a un numero di megabyte.  
  
 **Dimensioni iniziali (file di log)**  
 Consente di specificare il numero di megabyte per le dimensioni iniziali del file di log.  
  
 **Aumento dimensioni non consentito (file di log)**  
 Consente di indicare se le dimensioni del file di log possono eccedere le dimensioni iniziali specificate.  
  
 **Aumento dimensioni in percentuale (file di log)**  
 Consente di specificare che le dimensioni del file di log possono aumentare in base a un valore percentuale.  
  
 **Aumento dimensioni (file di log)**  
 Consente di specificare che le dimensioni del file di log possono aumentare in base a un numero di megabyte.  
  
  
