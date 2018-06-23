---
title: Tipo di dati Permission (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff5fb67e4f7989fb329e60a106ea8e6d0c734c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055082"
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
|Elementi figlio|[Annotazioni](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [nome](../properties/name-element-assl.md), [Processo](../properties/process-element-assl.md), [lettura](../properties/read-element-assl.md), [ReadDefinition](../properties/readdefinition-element-assl.md), [RoleID](../properties/roleid-element-assl.md), [scrivere](../properties/write-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Remarks  
 `Permission` serve come il tipo di base astratto per una serie di tipi di autorizzazione derivati utilizzati in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Questo tipo di dati presenta le convalide seguenti in DeploymentMode, valore 2 (modalità server tabulare).  
  
-   *Processo* valore predefinito dell'attributo è impostata su `False`, salvo quando l'utente dispone di **aggiornare** l'autorizzazione. Per gli utenti con il **Refresh** autorizzazione il *processo* valore di attributo è impostato su `True`.  
  
-   *ReadDefinition* valore di attributo è impostato su `None`; qualsiasi altro valore viene generato un errore.  
  
-   *Lettura* valore di attributo è impostato su `Allowed` per gli utenti con il **utente** autorizzazione e al `None` quando gli utenti assegnati al **aggiornare** autorizzazione; se un utente dispone di entrambi **Utente** e **aggiornare** autorizzazioni, quindi l'attributo è impostato su `Allowed`. Per utenti con privilegi amministrativi il valore dell'attributo è impostato su `Allowed`.  
  
-   *Scrivere* valore di attributo è impostato su `None`; qualsiasi altro valore viene generato un errore.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Permission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  