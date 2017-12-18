---
title: Importare il modulo SQLPS | Microsoft Docs
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 360350a7b8e051bcab2e24df508ea97b742c52a4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="import-the-sqlps-module"></a>Importare il modulo SQLPS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Il metodo consigliato per gestire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da PowerShell consiste nell'importare il modulo **sqlps** in un ambiente Windows PowerShell. Il modulo carica e registra gli snap-in e gli assembly di gestibilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  A partire da Windows PowerShell 3.0, i moduli vengono importati automaticamente quando un cmdlet o una funzione nel modulo viene usato in un comando. Questa funzionalità può essere usata in tutti i moduli di una directory inclusi nel valore della variabile di ambiente PSModulePath.  Per altre informazioni, vedere [Importing a PowerShell Module (Importazione di un modulo di PowerShell)](https://msdn.microsoft.com/library/dd878284(v=vs.85).aspx)
  
1.  **Prima di iniziare:**  [Sicurezza](#Security)  
  
2.  **Per caricare il modulo:**  [Caricare il Modulo sqlps](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Dopo avere importato il modulo **sqlps** in Windows PowerShell, è quindi possibile:  
  
-   Eseguire in modo interattivo comandi di Windows PowerShell.  
  
-   Eseguire file script di Windows PowerShell.  
  
-   Eseguire cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Utilizzare i percorsi del provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Utilizzare i modelli a oggetti per la gestibilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ad esempio Microsoft.SqlServer.Management.Smo, per gestire oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  I verbi usati nei nomi di due cmdlet di SQL Server (**Encode-Sqlname** e **Decode-Sqlname**) non corrispondono ai verbi approvati per Windows PowerShell. Ciò non ha effetto sull'operazione, tuttavia Windows PowerShell genera un avviso quando il modulo **sqlps** viene importato in una sessione.  
  
###  <a name="Security"></a> Sicurezza  
 Per impostazione predefinita, Windows PowerShell viene eseguito con i criteri di esecuzione degli script impostati su **Restricted**, che impediscono l'esecuzione degli script di Windows PowerShell. Per caricare il modulo **sqlps** , è possibile usare il cmdlet **Set-ExecutionPolicy** che consente di abilitare l'esecuzione di script firmati o di qualsiasi script. Eseguire solo script da origini attendibili e proteggere tutti i file di input e output utilizzando le autorizzazioni NTFS appropriate. Per altre informazioni sull'abilitazione degli script di Windows PowerShell, vedere [Running Windows PowerShell Scripts](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx)(Esecuzione di script di Windows PowerShell).  
  
##  <a name="LoadSqlps"></a> Caricare il Modulo sqlps  
 **Per caricare il modulo sqlps in Windows PowerShell**  
  
1.  Usare il cmdlet **Set-ExecutionPolicy** per impostare i criteri di esecuzione degli script appropriati.  
  
2.  Usare il cmdlet **Import-Module** per importare il modulo sqlps. Specificare il parametro **DisableNameChecking** per eliminare l'avviso su **Encode-Sqlname** e **Decode-Sqlname**.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene caricato il modulo **sqlps** con verifica del nome disabilitata.  
  
```powershell 
# Import the SQL Server Module.    
Import-Module Sqlps -DisableNameChecking;

# To check whether the module is installed.
Get-Module -ListAvailable -Name Sqlps;
```  
  
> [!NOTE]  
>  Se il modulo **sqlps** non è presente nel percorso, cambiare il percorso del modulo o usare il percorso completo nello script, racchiudendo tra virgolette i nomi di cartella del percorso se contengono spazi. Il modulo **sqlps** si trova nella cartella Tools\Powershell dell'istanza di SQL Server.  
  
 ![Icona freccia usata con il collegamento Torna all'inizio](../../analysis-services/instances/media/uparrow16x16.gif "Icona freccia usata con il collegamento Torna all'inizio") [&#91;Torna all'inizio&#93;]()  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [Provider PowerShell per SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Utilizzo di cmdlet del motore di database](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
 [Installazione di un modulo di PowerShell](https://msdn.microsoft.com/library/dd878350(v=vs.85).aspx)  
 [Import-Module](https://technet.microsoft.com/library/hh849725.aspx)
  
  
