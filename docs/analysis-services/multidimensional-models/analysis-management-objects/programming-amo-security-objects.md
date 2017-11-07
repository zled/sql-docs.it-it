---
title: Programmazione di oggetti di sicurezza AMO | Documenti Microsoft
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
- programming [AMO]
- Analysis Management Objects, security
- AMO, security
ms.assetid: 5d963721-6e6e-46eb-bc9b-18724dd0b751
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 450ae3165942cfdf290a074dd637b220e1c740d8
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-security-objects"></a>Programmazione di oggetti di sicurezza AMO
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], gli oggetti di sicurezza di programmazione o si eseguono applicazioni che utilizzano oggetti di sicurezza AMO è necessario essere un membro del gruppo amministratore del Server o il gruppo amministratore del Database. Amministratore del server e amministratore del Database sono un accesso livelli forniti da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] l'utente può accedere a un oggetto tramite la combinazione di ruoli e autorizzazioni assegnati all'oggetto specifico. Per ulteriori informazioni, vedere [classi di sicurezza AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-security-classes.md).  
  
## <a name="role-and-permission-objects"></a>Oggetti Role e Permission  
 I ruoli del server contengono esclusivamente un ruolo nella raccolta, ovvero il ruolo Administrators. Non è possibile aggiungere nuovi ruoli alla raccolta dei ruoli del server. L'appartenenza al ruolo Administrators consente l'accesso completo a ogni oggetto presente nel server  
  
 Gli oggetti <xref:Microsoft.AnalysisServices.Role> vengono creati a livello di database. Per la gestione del ruolo è necessario solo aggiungere o rimuovere membri dal ruolo nonché aggiungere o eliminare ruoli dall'oggetto <xref:Microsoft.AnalysisServices.Database>. Non è possibile eliminare un ruolo se è presente un qualsiasi oggetto <xref:Microsoft.AnalysisServices.Permission> associato al ruolo stesso. Per eliminare un ruolo, è necessario ricercare tutti gli oggetti <xref:Microsoft.AnalysisServices.Permission> presenti nell'oggetto <xref:Microsoft.AnalysisServices.Database> e rimuovere l'oggetto <xref:Microsoft.AnalysisServices.Role> dalle autorizzazioni, prima che l'oggetto <xref:Microsoft.AnalysisServices.Role> possa essere eliminato dall'oggetto <xref:Microsoft.AnalysisServices.Database>.  
  
 Le autorizzazioni definiscono le azioni abilitate sull'oggetto in cui viene fornita l'autorizzazione. Le autorizzazioni possono essere fornite negli oggetti <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MiningStructure> e <xref:Microsoft.AnalysisServices.MiningModel>. La gestione delle autorizzazioni comporta la concessione o la revoca dell'accesso abilitato dalla proprietà di accesso corrispondente. Per ogni accesso abilitato, è disponibile una proprietà che può essere impostata sul livello di accesso desiderato. L'accesso può essere definito per le operazioni Process, ReadDefinition, Read, Write e Administer. L'amministrazione dell'accesso viene definita solo nell'oggetto <xref:Microsoft.AnalysisServices.Database>. Il livello di sicurezza di amministratore di database viene ottenuto quando il ruolo viene concesso con l'autorizzazione relativa al database Administer.  
  
 Nell'esempio seguente vengono creati quattro ruoli, ovvero Database Administrators, Processors, Writers e Readers.  
  
 Gli appartenenti al ruolo Database Administrators possono amministrare il database fornito.  
  
 Gli appartenenti al ruolo Processors possono elaborare tutti gli oggetti in un database e verificare i risultati. Per verificare i risultati, è necessario abilitare in modo esplicito l'accesso in lettura all'oggetto di database per il cubo fornito poiché le autorizzazioni di lettura non vengono applicate agli oggetti figlio.  
  
 Gli appartenenti al ruolo Writers possono leggere e scrivere nel cubo fornito e l'accesso alla cella è limitato alla dimensione "United States" relativa al cliente.  
  
 Gli appartenenti al ruolo Readers possono leggere nel cubo fornito e l'accesso alla cella è limitato alla dimensione "United States" relativa al cliente.  
  
```  
static public void CreateRolesAndPermissions(Database db, Cube cube)  
{  
    Role role;  
    DatabasePermission dbperm;  
    CubePermission cubeperm;  
  
    #region Create the Database Administrators role  
  
    // Create the Database Administrators role.  
    role = db.Roles.Add("Database Administrators");  
    role.Members.Add(new RoleMember("")); // e.g. domain\user  
    role.Update();  
  
    // Assign administrative permissions to this role.  
    // Members of this role can perform any operation within the database.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Administer = true;  
    dbperm.Update();  
  
    #endregion  
  
    #region Create the Processors role  
  
    // Create the Processors role.  
    role = db.Roles.Add("Processors");  
    role.Members.Add(new RoleMember("")); // e.g. myDomain\johndoe  
    role.Update();  
  
    // Assign Read and Process permissions to this role.  
    // Members of this role can process objects in the database and query them to verify results.  
    // Process permission applies to all contained objects, i.e. all dimensions and cubes.  
    // Read permission does not apply to contained objects, so we must assign the permission explicitly on the cubes.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Process = true;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Writers role  
  
    // Create the Writers role.  
    role = db.Roles.Add("Writers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read and Write permissions to this role.  
    // Members of this role can discover, query and writeback to the Adventure Works cube.  
    // However cell access and writeback is restricted to the United States (in the Customer dimension).  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    cubeperm.Write = WriteAccess.Allowed;  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.Read, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.CellPermissions.Add(new CellPermission(CellPermissionAccess.ReadWrite, "[Customer].[Country-Region].CurrentMember is [Customer].[Country-Region].[Country-Region].&[United States]"));  
    cubeperm.Update();  
  
    #endregion  
  
    #region Create the Readers role  
  
    // Create the Readers role.  
    role = db.Roles.Add("Readers");  
    role.Members.Add(new RoleMember("")); // e.g. redmond\johndoe  
    role.Update();  
  
    // Assign Read permissions to this role.  
    // Members of this role can discover and query the Adventure Works cube.  
    // However the Customer dimension is restricted to the United States.  
    dbperm = db.DatabasePermissions.Add(role.ID);  
    dbperm.Read = ReadAccess.Allowed;  
    dbperm.Update();  
  
    cubeperm = cube.CubePermissions.Add(role.ID);  
    cubeperm.Read = ReadAccess.Allowed;  
    Dimension dim = db.Dimensions.GetByName("Customer");  
    DimensionAttribute attr = dim.Attributes.GetByName("Country-Region");  
    CubeDimensionPermission cubedimperm = cubeperm.DimensionPermissions.Add(dim.ID);  
    cubedimperm.Read = ReadAccess.Allowed;  
    AttributePermission attrperm = cubedimperm.AttributePermissions.Add(attr.ID);  
    attrperm.AllowedSet = "{[Customer].[Country-Region].[Country-Region].&[United States]}";  
    cubeperm.Update();  
  
    #endregion  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Programmazione di oggetti di sicurezza AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [Le autorizzazioni e diritti di accesso &#40; Analysis Services - dati multidimensionali &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

