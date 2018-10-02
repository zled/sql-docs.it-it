---
title: Installare SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a847748b0f0025402da1feb794f5c441ea2a3f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773569"
---
# <a name="install-sql-server-data-tools"></a>Installare SQL Server Data Tools
Questo argomento descrive come installare SQL Server Data Tools. Gli aggiornamenti per SQL Server Data Tools sono disponibili nella pagina di download di SQL Server Data Tools ([installare la versione più recente di SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)).  
  
Se si usa Visual Studio 2012 o Visual Studio 2013, installare gli ultimi aggiornamenti di SQL Server Data Tools per ottenere le funzionalità più recenti.  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>SQL Server Data Tools per Visual Studio 2013  
SQL Server Data Tools è disponibile in Visual Studio 2013 Express per Web, Visual Studio 2013 Express per Desktop, Visual Studio Community 2013 e in tutte le SKU a pagamento, incluse la SKU Professional e versioni successive. Dopo aver installato Visual Studio 2013, andare in Strumenti -> Estensioni e aggiornamenti -> Aggiornamenti per verificare se sono disponibili aggiornamenti da installare.  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>SQL Server Data Tools per Visual Studio 2012  
SQL Server Data Tools è disponibile nella versione Professional, o superiore, in Visual Studio 2012. Dopo aver installato Visual Studio 2012 e l'aggiornamento di novembre 2012 o un aggiornamento successivo di SQL Server Data Tools, SQL Server Data Tools può segnalare quando è disponibile un aggiornamento per l'installazione. Per altre informazioni, vedere [Finestra di dialogo Verifica disponibilità aggiornamenti](../ssdt/check-for-updates-dialog-box.md).  
  
Se Visual Studio 2012 non è installato, SQL Server Data Tools installerà Visual Studio 2012 Integrated Shell e SQL Server Data Tools.  
  
## <a name="administrative-installation-point"></a>Punto di installazione amministrativa  
Se è necessario installare SQL Server Data Tools in più computer o in computer privi di accesso a Internet, è possibile creare un layout di installazione amministrativa in una condivisione di rete o su un supporto fisico e quindi eseguire l'installazione da quel punto.  
  
Per creare un layout di installazione, scaricare SSDTSetup.EXE ed eseguirlo con l'opzione `/layout`*percorso* per creare un layout nel *percorso*. Gli utenti possono quindi eseguire SSDTSetup.Exe dal *percorso*.  
  
Per scaricare SSDTSetup.exe, accedere alla pagina [Installare la versione più recente di SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714), fare clic sul collegamento per la versione in uso di Visual Studio e quindi scaricare SSDTSetup.exe per la propria lingua.  
  
