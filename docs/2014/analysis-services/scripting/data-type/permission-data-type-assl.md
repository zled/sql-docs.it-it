---
title: Tipo di dati Permission (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Permission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d12fb71a8ed19ca083e8ec506fba6338f6b58a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101942"
---
# <a name="permission-data-type-assl"></a>Tipo di dati Permission (ASSL)
  Definisce un tipo di dati primitivo astratto che rappresenta le informazioni su una singola autorizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[CubePermission](../objects/cubepermission-element-assl.md), [DatabasePermission](../objects/databasepermission-element-assl.md), [DimensionPermission](permission-data-type-assl.md), [MiningModelPermission](../objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nome](../properties/name-element-assl.md), [Processo](../properties/process-element-assl.md), [lettura](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [scrivere](../properties/write-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 `Permission` viene usato come tipo di base astratto per numerosi tipi di autorizzazione derivati utilizzati in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Questo tipo di dati presenta le convalide seguenti in DeploymentMode, valore 2 (modalità server tabulare).  
  
-   *Processo* valore predefinito dell'attributo è impostato su `False`, tranne quando l'utente dispone di **aggiornare** l'autorizzazione. Per gli utenti con il **Refresh** autorizzazione il *processo* valore dell'attributo è impostato su `True`.  
  
-   *ReadDefinition* valore dell'attributo è impostato su `None`; qualsiasi altro valore viene generato un errore.  
  
-   *Lettura* valore dell'attributo è impostato su `Allowed` per gli utenti con il **utente** autorizzazione e di ottenere `None` quando gli utenti vengono assegnati al **Aggiorna** autorizzazione; se un utente dispone di entrambi **Utente** e **aggiornare** autorizzazioni, quindi l'attributo è impostato su `Allowed`. Per utenti con privilegi amministrativi il valore dell'attributo è impostato su `Allowed`.  
  
-   *Scrivere* valore dell'attributo è impostato su `None`; qualsiasi altro valore viene generato un errore.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
