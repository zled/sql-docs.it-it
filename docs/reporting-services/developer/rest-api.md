---
title: Sviluppo con le API REST per Reporting Services | Documenti Microsoft
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
ms.date: 10/19/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 7c2c34047ac316045387b036cf10ee149175580a
ms.contentlocale: it-it
ms.lasthandoff: 10/20/2017

---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Sviluppo con le API REST per Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

Microsoft SQL Server 2017 Reporting Services supporta Representational State Transfer (REST) API. Le API REST sono gli endpoint che supportano un set di operazioni HTTP (metodi), che forniscono creazione del servizio, recuperare, aggiornare o eliminare l'accesso per le risorse all'interno di un server di report.

L'API REST fornisce l'accesso programmatico agli oggetti in un catalogo di server di report di Reporting Services di SQL Server 2017. Esempi di oggetti sono cartelle, report, gli indicatori KPI, origini dati, set di dati, i piani di aggiornamento, le sottoscrizioni e altro ancora. Usando l'API REST, è possibile, ad esempio, esplorare la gerarchia di cartelle, individuare il contenuto di una cartella o scaricare una definizione del report. È anche possibile creare, aggiornare ed eliminare oggetti. Esempi di utilizzo di oggetti di caricamento di un report, eseguire un piano di aggiornamento, eliminazione di una cartella e così via.

## <a name="components-of-a-rest-api-requestresponse"></a>Componenti di una richiesta/risposta di API REST

Una coppia richiesta-risposta API REST può essere suddivise in cinque componenti:

* Il **URI della richiesta**, costituito da: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Anche se l'URI della richiesta è incluso nell'intestazione del messaggio di richiesta, viene chiamato separatamente perché la maggior parte dei linguaggi o Framework necessario passare separatamente dal messaggio di richiesta.

    * Schema URI: indica il protocollo utilizzato per trasmettere la richiesta. Ad esempio, `http` o `https`.
    * Host dell'URI: Specifica il nome di dominio o l'indirizzo IP del server in cui l'endpoint REST del servizio è ospitato, ad esempio `myserver.contoso.com`.
    * Percorso della risorsa: specifica la risorsa o raccolta di risorse, che può includere più segmenti utilizzati dal servizio per determinare la selezione di tali risorse. Ad esempio: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` può essere utilizzato per ottenere le proprietà specificate per il CatalogItem.
    * (Facoltativo) stringa di query: fornisce parametri semplici aggiuntivi, ad esempio i criteri di selezione API versione o una risorsa.

* Campi di intestazione messaggio di richiesta HTTP:

    * Richiesta [metodo HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (noto anche come un'operazione o una verbo), che indica il tipo di operazione di richiesta al servizio. Reporting che API REST di servizi supportano DELETE, GET, HEAD, PUT, POST e metodi di PATCH.
    * Campi di intestazione aggiuntivi facoltativi, come richiesto dal metodo URI e HTTP specificato.

* HTTP facoltativo **corpo del messaggio di richiesta** i campi, per supportare l'operazione di URI e HTTP. Ad esempio, operazioni POST contengono oggetti con codifica MIME che vengono passati come parametri complessi. Per le operazioni di POST o PUT, il tipo di codifica MIME per il corpo deve essere specificato nel `Content-type` nonché intestazione della richiesta. Alcuni servizi è necessario utilizzare un tipo MIME specifico, ad esempio `application/json`.

* HTTP **intestazione del messaggio di risposta** campi:

    * Un [codice di stato HTTP](http://www.w3.org/Protocols/HTTP/HTRESP.html), gamma dai codici di esito positivo 2xx 4xx o 5xx in codici di errore. In alternativa, un codice di stato definito dal servizio può essere restituito come indicato nella documentazione dell'API.
    * I campi di intestazione aggiuntivi facoltativi, come richiesto per supportare la risposta della richiesta, ad esempio un `Content-type` intestazione della risposta.

* HTTP facoltativo **corpo del messaggio di risposta** campi:

    * Gli oggetti con codifica MIME risposta vengono restituiti nel corpo della risposta HTTP, ad esempio una risposta da un metodo GET che restituisce dati. In genere, questi oggetti vengono restituiti in un formato strutturato, ad esempio JSON o XML, come indicato dal `Content-type` intestazione della risposta.

## <a name="api-documentation"></a>Documentazione dell'API

Un'API REST moderna chiama per documentazione API. L'API REST si basa sulla specifica OpenAPI (anche noto come la specifica di swagger) e la documentazione è disponibile in [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0). Oltre alla documentazione relativa all'API, SwaggerHub consente di generare una libreria client nella lingua scelta, JavaScript, TypeScript, c#, Java, Python, Ruby e altro ancora.

## <a name="testing-api-calls"></a>Chiamate API di test

È uno strumento per il testing di messaggi di richiesta/risposta HTTP [Fiddler](http://www.telerik.com/fiddler). Fiddler è un web gratuito debug proxy che può intercettare le richieste REST, semplificando la diagnosi della richiesta HTTP / messaggi di risposta.

## <a name="next-steps"></a>Passaggi successivi

Esaminare le API disponibili nella [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0).

Esempi sono disponibili su [GitHub](https://github.com/Microsoft/Reporting-Services). L'esempio include un'applicazione HTML5 basata su TypeScript e React webpack con un esempio di PowerShell.

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
