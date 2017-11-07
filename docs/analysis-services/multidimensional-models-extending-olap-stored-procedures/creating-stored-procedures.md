---
title: Creazione di Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1212037722863a4dc72ddb99387308cf2e33fc33
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="creating-stored-procedures"></a>Creazione di stored procedure
  Tutte le stored procedure devono essere associate a una classe CLR (Common Language Runtime) o COM (Component Object Model) per poter essere utilizzate. La classe deve essere installata nel server, in genere sotto forma di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® libreria a collegamento dinamico (DLL) e registrata come assembly nel server o in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.  
  
 Le stored procedure vengono registrate in un server o in un database. Le stored procedure del server possono essere chiamate da qualsiasi contesto di query, mentre le stored procedure di database sono accessibili solo se il contesto del database è il database nel quale è stata definita la stored procedure. Se in un assembly sono presenti funzioni che chiamano funzioni di un assembly diverso, è necessario registrare entrambi gli assembly nello stesso contesto (server o database). Per un server o un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in un server, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per registrare un assembly. Per un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile utilizzare Progettazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per registrare un assembly nel progetto.  
  
> [!IMPORTANT]  
>  Gli assembly COM potrebbero comportare un rischio per la sicurezza. A causa di tale rischio e di altre considerazioni, gli assembly COM sono stati deprecati in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)] e potrebbero non essere supportati nelle versioni future.  
  
## <a name="registering-a-server-assembly"></a>Registrazione di un assembly server  
 In Esplora oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] gli assembly server vengono elencati nella cartella Assembly in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli assembly server possono contenere sia assembly .NET (CLR) sia librerie COM.  
  
### <a name="to-create-a-server-assembly"></a>Per creare un assembly server  
  
1.  Espandere l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Esplora oggetti, fare doppio clic su di **assembly** cartella e quindi fare clic su **nuovo Assembly**. Consente di visualizzare il **registra Assembly Server** la finestra di dialogo.  
  
2.  Per **tipo** specificare il tipo di assembly:  
  
    -   Per una DLL (CLR) con codice gestito, specificare Assembly .NET.  
  
    -   Per una DLL (COM) con codice nativo, specificare DLL COM.  
  
3.  Per **nome File**, specificare la DLL contenente la stored procedure.  
  
4.  Per **nome Assembly**, specificare un nome per l'assembly.  
  
5.  Se si tratta di una build di debug della libreria che si desidera utilizzare per eseguire il debug di stored procedure, selezionare il **Includi informazioni di debug** casella di controllo. Per ulteriori informazioni sul debug di stored procedure, vedere [il debug di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md).  
  
6.  È possibile fare clic su **OK** per registrare l'assembly immediatamente oppure sulla barra degli strumenti finestra di dialogo, è possibile scegliere un comando di **Script** menu per l'azione di registrazione in una finestra query, un file o negli Appunti di script.  
  
 Dopo aver registrato un assembly di server, è possibile configurare facendo clic in Esplora oggetti e quindi fare clic su **proprietà**.  
  
## <a name="registering-a-database-assembly-on-the-server"></a>Registrazione di un assembly database nel server  
 In Esplora oggetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] gli assembly database vengono elencati nella cartella Assembly in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli assembly database possono contenere sia assembly .NET (CLR) sia librerie COM.  
  
### <a name="to-create-a-database-assembly-on-a-server"></a>Per creare un assembly database in un server  
  
1.  Espandere l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Esplora oggetti di database, fare doppio clic su di **assembly** cartella e quindi fare clic su **nuovo Assembly**. Consente di visualizzare il **registra Assembly Database** la finestra di dialogo.  
  
2.  Per **tipo** specificare il tipo di assembly:  
  
    -   Per una DLL (CLR) con codice gestito, specificare Assembly .NET.  
  
    -   Per una DLL (COM) con codice nativo, specificare DLL COM.  
  
3.  Per **nome File**, specificare la DLL contenente la stored procedure.  
  
4.  Per **nome Assembly**, specificare un nome per l'assembly.  
  
5.  Se si tratta di una build di debug della libreria che si desidera utilizzare per eseguire il debug di stored procedure, selezionare il **Includi informazioni di debug** casella di controllo. Per ulteriori informazioni sul debug di stored procedure, vedere [il debug di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md).  
  
6.  È possibile fare clic su **OK** per registrare l'assembly immediatamente oppure sulla barra degli strumenti finestra di dialogo, è possibile scegliere un comando di **Script** menu per l'azione di registrazione in una finestra query, un file o negli Appunti di script.  
  
 Dopo aver registrato un assembly database, è possibile configurare facendo clic in Esplora oggetti e quindi fare clic su **proprietà**.  
  
## <a name="registering-a-database-assembly-in-a-project"></a>Registrazione di un assembly database in un progetto  
 In Esplora soluzioni in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] gli assembly database vengono elencati nella cartella Assembly in un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Gli assembly database possono contenere sia assembly .NET (CLR) sia librerie COM.  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a>Per creare un assembly database in un progetto di Analysis Services  
  
1.  Espandere l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Esplora oggetti di database, fare doppio clic su di **assembly** cartella e quindi fare clic su **nuovo riferimento ad Assembly**. Consente di visualizzare il **Aggiungi riferimento** la finestra di dialogo. Il **.NET** scheda della finestra il **Aggiungi riferimento** la finestra di dialogo sono elencati gli assembly .NET (CLR) esistenti, mentre il **progetti** scheda vengono elencati i progetti.  
  
2.  È possibile fare clic su un progetto o un componente esistente e quindi fare clic su **Aggiungi** per aggiungerlo al [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. Per aggiungere un riferimento a una DLL COM, fare clic su di **Sfoglia** scheda per individuare il file. Il **progetti e componenti selezionati** sono elencati il nome, tipo, versione e percorso di ogni componente che si sta aggiungendo al progetto.  
  
3.  Dopo aver terminato di selezione dei componenti da aggiungere, fare clic su **OK** per aggiungerli al [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto.  
  
## <a name="script-format-for-an-assembly"></a>Formatto dello script di un assembly  
 Registrare un assembly .NET è un'operazione piuttosto semplice. Per aggiungere un assembly .NET a un database in formato binario è possibile utilizzare il formato seguente:  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

