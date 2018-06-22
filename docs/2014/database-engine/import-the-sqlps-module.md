---
title: Importare il modulo SQLPS | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: 9
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: 8c20daf51270931609fb876b9a7035da343d19f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068990"
---
# <a name="import-the-sqlps-module"></a>Importare il modulo SQLPS
  Il metodo consigliato per gestire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] da PowerShell consiste nell'importare il modulo `sqlps` in un ambiente Windows PowerShell 2.0. Il modulo carica e registra gli snap-in e gli assembly di gestibilità di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
1.  **Prima di iniziare:** [Sicurezza](#Security)  
  
2.  **Per caricare il modulo:**  [Caricare il Modulo sqlps](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Dopo avere importato il modulo `sqlps` in Windows PowerShell, è quindi possibile:  
  
-   Eseguire in modo interattivo comandi di Windows PowerShell.  
  
-   Eseguire file script di Windows PowerShell.  
  
-   Eseguire cmdlet di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Utilizzare i percorsi del provider di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Utilizzare i modelli a oggetti per la gestibilità di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , ad esempio Microsoft.SqlServer.Management.Smo, per gestire oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  I verbi utilizzati nei nomi di due SQL Server cmdlet (`Encode-Sqlname` e `Decode-Sqlname`) non corrispondono ai verbi approvati per Windows PowerShell 2.0. Non produce alcun effetto sull'operazione, tuttavia Windows PowerShell genera un avviso quando il `sqlps` modulo viene importato in una sessione.  
  
###  <a name="Security"></a> Sicurezza  
 Per impostazione predefinita, Windows PowerShell viene eseguito con i criteri di esecuzione degli script impostati su **Restricted**, che impediscono l'esecuzione degli script di Windows PowerShell. Per caricare il modulo `sqlps`, è possibile utilizzare il cmdlet `Set-ExecutionPolicy` per abilitare l'esecuzione di script firmati o di qualsiasi script. Eseguire solo script da origini attendibili e proteggere tutti i file di input e output utilizzando le autorizzazioni NTFS appropriate. Per altre informazioni sull'abilitazione degli script di Windows PowerShell, vedere [Running Windows PowerShell Scripts](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx)(Esecuzione di script di Windows PowerShell).  
  
##  <a name="LoadSqlps"></a> Caricare il Modulo sqlps  
 **Per caricare il modulo sqlps in Windows PowerShell**  
  
1.  Utilizzare il `Set-ExecutionPolicy` cmdlet per impostare i criteri di esecuzione degli script appropriati.  
  
2.  Utilizzare il `Import-Module` per importare il modulo sqlps. Specificare il `DisableNameChecking` parametro se si desidera eliminare l'avviso sui `Encode-Sqlname` e `Decode-Sqlname`.  
  
### <a name="example-powershell"></a>Esempio (PowerShell)  
 In questo esempio viene caricato il modulo `sqlps` con verifica del nome disabilitata.  
  
```  
## Import the SQL Server Module.  
  
Import-Module “sqlps” -DisableNameChecking  
  
```  
  

  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)   
 [Provider PowerShell per SQL Server](../powershell/sql-server-powershell-provider.md)   
 [Usare cmdlet del motore di database](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  