---
title: Gestione dei ruoli pacchetto a livello di programmazione (servizio SSIS) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4dfedb872ff34db30a99cdc9eced24d69691905
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Gestione dei ruoli pacchetto a livello di programmazione (servizio SSIS)
  Quando si utilizzano i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a livello di programmazione, può essere necessario determinare quali ruoli possono essere applicati ai pacchetti oppure determinare o impostare i ruoli applicati a un singolo pacchetto. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> dello spazio dei nomi <xref:Microsoft.SqlServer.Dts.Runtime> fornisce un'ampia varietà di metodi e classi per soddisfare questi requisiti.  
  
 I ruoli si applicano solo ai pacchetti archiviati nel database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**. Per altre informazioni sui ruoli pacchetto, vedere [Ruoli Integration Services &#40;servizio SSIS&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
 Tutti i metodi descritti in questo argomento richiedono un riferimento all'assembly **Microsoft.SqlServer.ManagedDTS**. Dopo aver aggiunto il riferimento in un nuovo progetto, importare lo spazio dei nomi <xref:Microsoft.SqlServer.Dts.Runtime> con un'istruzione **using** o **Imports**.  
  
> [!IMPORTANT]  
>  I metodi della classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> per l'utilizzo dell'archivio pacchetti SSIS supportano solo ".", localhost o il nome del server locale. Non è possibile utilizzare "(local)".  
  
## <a name="determining-which-roles-are-available"></a>Verifica dei ruoli disponibili  
 Per determinare quali ruoli sono disponibili per i pacchetti archiviati in un determinato server, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> della classe <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
## <a name="determining-which-roles-are-assigned"></a>Verifica dei ruoli assegnati  
 Per determinare quali ruoli sono già stati assegnati a un determinato pacchetto, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Per assegnare ruoli a un pacchetto, chiamare il metodo <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Ruoli Integration Services &#40;servizio SSIS&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)  
  
  
