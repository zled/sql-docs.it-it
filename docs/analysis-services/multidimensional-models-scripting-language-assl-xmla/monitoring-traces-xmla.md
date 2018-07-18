---
title: Monitoraggio di tracce (XMLA) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 24aab35b34ed9339ec2d7950efab21a94b2c0d96
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021518"
---
# <a name="monitoring-traces-xmla"></a>Monitoraggio di tracce (XMLA)
  È possibile utilizzare il [Sottoscrivi](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md) comando XML for Analysis (XMLA) per monitorare una traccia esistente definita in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Il **Sottoscrivi** comando restituisce i risultati di una traccia in un set di righe.  
  
## <a name="specifying-a-trace"></a>Specifica di una traccia  
 Il [oggetto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) proprietà del **Sottoscrivi** comando deve contenere un riferimento a uno oggetto un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza o una traccia in un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza. Se il **oggetto** proprietà non è specificata, o un identificatore di traccia non è specificato nella **oggetto** proprietà, il **Sottoscrivi** comando consente di monitorare la traccia della sessione per impostazione predefinita la sessione esplicita specificata nell'intestazione SOAP per il comando.  
  
## <a name="returning-results"></a>Restituzione di risultati  
 Il **Sottoscrivi** comando restituisce un set di righe contenente gli eventi di traccia acquisiti dalla traccia specificata. Il **Sottoscrivi** comando restituisce i risultati della traccia fino a quando non viene annullato il comando mediante il [Annulla](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) comando.  
  
 Nel set di righe sono contenute le colonne elencate nella tabella seguente.  
  
|Colonna|Tipo di dati|Descrizione|  
|------------|---------------|-----------------|  
|EventClass|Valore intero|Classe di evento dell'evento ricevuto dalla traccia.|  
|EventSubclass|Long integer|Sottoclasse di evento dell'evento ricevuto dalla traccia.|  
|CurrentTime|DateTime|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|DateTime|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|DateTime|Ora di fine dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".<br /><br /> Questa colonna non viene popolata per classi di evento che descrivono l'inizio di un processo o di un'azione.|  
|Durata|Long integer|Durata dell'evento (in millisecondi).|  
|CPUTime|Long integer|Tempo processore utilizzato per l'evento (in millisecondi).|  
|JobID|Long integer|Identificatore di processo.|  
|SessionID|String|Identificatore della sessione per cui si è verificato l'evento.|  
|SessionType|String|Tipo della sessione per cui si è verificato l'evento.|  
|ProgressTotal|Long integer|Numero o quantità complessiva dello stato di avanzamento segnalato dall'evento.|  
|IntegerData|Long integer|Dati di tipo integer associati all'evento. Il contenuto di questa colonna dipende dalla classe e dalla sottoclasse di evento.|  
|ObjectID|String|Identificatore dell'oggetto per cui si è verificato l'evento.|  
|ObjectType|String|Tipo dell'oggetto specificato in ObjectName.|  
|ObjectName|String|Nome dell'oggetto per cui si è verificato l'evento.|  
|ObjectPath|String|Percorso gerarchico dell'oggetto per cui si è verificato l'evento. Il percorso viene rappresentato come una stringa delimitata da virgole di identificatori di oggetto per i padri dell'oggetto specificato in ObjectName.|  
|ObjectReference|String|Rappresentazione XML del riferimento all'oggetto per l'oggetto specificato in ObjectName.|  
|NestLevel|Valore intero|Livello della transazione per cui si è verificato l'evento.|  
|NumSegments|Long integer|Numero di segmenti di dati interessati o utilizzati dal comando per cui si è verificato l'evento.|  
|Severity|Valore intero|Livello di gravità di un'eccezione per l'evento. I possibili valori della colonna sono i seguenti:<br /><br /> <br /><br /> 0: operazione riuscita<br /><br /> <br /><br /> 1: informazioni<br /><br /> <br /><br /> 2: avviso<br /><br /> <br /><br /> 3: errore|  
|Esito positivo|Boolean|Indica se un comando ha avuto esito positivo o negativo.|  
|Errore|Long integer|Numero di errore di un evento, se applicabile.|  
|ConnectionID|String|Identificatore della connessione per cui si è verificato l'evento.|  
|DatabaseName|String|Nome del database per cui si è verificato l'evento.|  
|NTUserName|String|Nome utente di Windows dell'utente associato all'evento.|  
|NTDomainName|String|Dominio di Windows dell'utente associato all'evento.|  
|ClientHostName|String|Nome del computer in cui viene eseguita l'applicazione client. Questa colonna viene popolata con i valori passati dall'applicazione client.|  
|ClientProcessID|Long integer|Identificatore di processo dell'applicazione client.|  
|ApplicationName|String|Nome dell'applicazione client che ha creato la connessione all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione client anziché con il nome visualizzato del programma.|  
|NTCanonicalUserName|String|Nome utente di Windows in forma canonica dell'utente associato all'evento.|  
|SPID|String|ID del processo server (SPID) della sessione per cui si è verificato l'evento. Il valore di questa colonna corrisponde direttamente all'ID di sessione specificato nell'intestazione SOAP del messaggio XMLA per cui si è verificato l'evento.|  
|TextData|String|Dati di testo associati all'evento. Il contenuto di questa colonna dipende dalla classe e dalla sottoclasse di evento.|  
|ssSqlProfiler|String|Nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per cui si è verificato l'evento.|  
|RequestParameters|String|Parametri della query con parametri o del comando XMLA per cui si è verificato l'evento.|  
|RequestProperties|String|Proprietà del metodo XMLA per cui si è verificato l'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
