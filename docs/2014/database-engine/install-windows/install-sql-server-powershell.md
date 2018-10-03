---
title: Installare SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 961f5793732dcfabd19b07f0a22b467591a980c7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203241"
---
# <a name="install-sql-server-powershell"></a>Installare SQL Server PowerShell
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Se rileva di aver selezionato l'installazione si interrompe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità che includono i componenti PowerShell, ma Windows PowerShell 2.0 non è installato. È necessario installare PowerShell tramite Windows Management Framework, quindi rieseguire l'installazione.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>Installazione del supporto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Per installare il software che fornisce il supporto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell utilizzare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quando si seleziona qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta funzionalità che richiedono PowerShell, il programma di installazione verifica che Windows PowerShell 2.0 sia installato. Se PowerShell 2.0 è presente, il programma di installazione installa quindi quanto segue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i componenti di PowerShell:  
  
-   Gli snap-in di PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Gli snap-in sono file DLL che implementano due tipi di supporto di Windows PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   Set di cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I cmdlet sono comandi che implementano un'azione specifica, ad esempio **Invoke-Sqlcmd** esegue uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] o XQuery che può essere eseguito anche con l'utilità **sqlcmd** , mentre **Invoke-PolicyEvaluation** segnala se gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono conformi ai criteri di gestione basata su criteri.  
  
    -   Provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il provider consente di spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando un percorso simile a un percorso del file system. Ciascun oggetto è associato a una classe dei modelli SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). È possibile utilizzare i metodi e le proprietà della classe per eseguire azioni sugli oggetti. Utilizzando il comando cd per un oggetto di database in un percorso, ad esempio, è possibile utilizzare i metodi e le proprietà della classe Microsoft.SqlServer.Management.SMO.Database per gestire il database.  
  
-   Il **sqlps** modulo importato nelle sessioni di Windows PowerShell 2.0 per caricare il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-in.  
  
-   Deprecate **sqlps** utilità che avvia una sessione di Windows PowerShell 2.0 e Importa il **sqlps** modulo.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supporta l'avvio delle sessioni di Windows PowerShell dall'albero di Esplora oggetti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supporta i passaggi del processo di Windows PowerShell.  
  
 Se Windows PowerShell 2.0 non è stato installato oppure è stato disinstallato, è necessario installarlo seguendo le istruzioni nella [Windows Management Framework](http://go.microsoft.com/fwlink/?LinkId=186214) pagina.  
  
 Se Windows PowerShell viene disinstallato al termine dell'installazione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le funzionalità per Windows PowerShell non funzionerà. Windows PowerShell può essere disinstallato dagli utenti di Windows. La disinstallazione di Windows PowerShell potrebbe inoltre essere necessaria per eseguire alcuni aggiornamenti del sistema operativo Windows. Per utilizzare le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell è necessario reinstallare PowerShell 2.0 tramite Windows Management Framework.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
