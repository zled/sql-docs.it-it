---
title: Set di righe DISCOVER_DATASOURCES | Documenti Microsoft
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
apiname:
- DISCOVER_DATASOURCES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_DATASOURCES rowset
ms.assetid: f3ff26ab-a447-416b-ba54-1716df2283de
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9c91d5b1d3e0fb7ec972e47079a1bf36d8f9b87
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoverdatasources-rowset"></a>Set di righe DISCOVER_DATASOURCES
  Restituisce un elenco delle origini dati del provider XMLA (XML for Analysis) disponibili nel server o servizio Web. Le origini dati pubblicate vengono restituite da un URL del server Web dell'applicazione. Il client può connettersi a una delle origini dati incluse in questo elenco.  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_DATASOURCES** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_DATASOURCES** set di righe.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il client seleziona un'origine dati impostando il **DataSourceInfo** proprietà il [proprietà](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) elemento che viene inviata insieme al [comando](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md) elemento mediante il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo. Non costruire il contenuto di un client di **DataSourceInfo** proprietà per l'invio al server. Al contrario, il client deve utilizzare il **Discover** metodo per trovare le origini dati supportate dal provider. Il client invia quindi nuovamente lo stesso valore il **DataSourceInfo** proprietà ottenute dal **DISCOVER_DATASOURCES** set di righe.  
  
 Il **DISCOVER_DATASOURCES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DataSourceName**|**DBTYPE_WSTR**|Sì|Il nome dei dati di origine, ad esempio **Adventure Works**.|  
|**DataSourceDescription**|**DBTYPE_WSTR**||Descrizione dell'origine dei dati immessa dal server di pubblicazione.<br /><br /> Può restituire **NULL**.|  
|**URL**|**DBTYPE_WSTR**|Sì|Percorso univoco che indica la posizione da cui richiamare i metodi XMLA (XML for Analysis) per tale origine dati.<br /><br /> Può restituire **NULL**.|  
|**DataSourceInfo**|**DBTYPE_WSTR**||Una stringa che contiene eventuali informazioni aggiuntive necessarie per la connessione all'origine dati.<br /><br /> Può restituire **NULL**.|  
|**ProviderName**|**DBTYPE_WSTR**|Sì|Nome del provider per l'origine dati.<br /><br /> Esempio: `"MSOLAP"`<br /><br /> Può restituire **NULL**.|  
|**Tipoprovider**|**DBTYPE_WSTR**|Sì|Tipi di dati supportati dal provider. Questa matrice può includere uno o più dei tipi seguenti:<br /><br /> **Dati Multidimensionali**: provider di dati multidimensionali.<br /><br /> **Dominio di pubblicazione Trusted**: provider di dati tabulari.<br /><br /> **DMP**: provider di data mining (implementa OLE per il database per la specifica di Data Mining).|  
|**AuthenticationMode**|**DBTYPE_WSTR**|Sì|Specifica relativa al tipo di modalità di sicurezza utilizzata dall'origine dati. I valori possibili sono i seguenti:<br /><br /> **Non autenticate**: non deve essere inviato alcun ID utente o password.<br /><br /> **Autenticazione**: ID utente e password devono essere incluse le informazioni necessarie per connettersi all'origine dati.<br /><br /> **Integrata**: l'origine dati utilizza la sicurezza sottostante per determinare l'autorizzazione, ad esempio la sicurezza integrata fornita da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS).|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Il **DISCOVER_DATASOURCES** set di righe non è possibile eseguire query utilizzando query DMV e la sintassi del comando SELECT. Tuttavia, il **DISCOVER_DATASOURCES** set di righe possono essere eseguite utilizzando <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A>.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|06c03d41-f66d-49f3-b1b8-987f7af4cf18|  
|ADOMDNAME|DataSources|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

