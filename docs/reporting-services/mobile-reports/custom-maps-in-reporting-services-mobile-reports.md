---
title: Mappe personalizzate nei report di Reporting Services per dispositivi mobili | Microsoft Docs
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a3786fcf92c767905c6295dffc8a24e7a86d2cbe
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813944"
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Esegue il mapping personalizzato nei report di Reporting Services per dispositivi mobili
Le mappe geografiche in SQL Server Mobile Report Publisher sono definite in un formato noto come *file di forma ESRI*.  
  
Inizialmente progettato da una società privata, oggi è un formato semi aperto molto diffuso, usato in gran parte delle applicazioni GIS. In conformità con questo formato, Mobile Report Publisher richiede di fornire due file durante la definizione di una mappa:  
  
- Un file SHP per geometrie di forma  
- Un file DBF per i metadati  
  
I nomi dei file di base devono corrispondere (ad esempio, *canada.shp* e *canada.dbf*). I metadati devono includere il campo *NAME* con il valore del nome della forma corrispondente (chiave), che verrà usato durante la compilazione della mappa con dati.  
  
> **Nota**: le dimensioni dei due file di mapping, ossia SHP e DBF, non possono superare insieme i 512 KB. Se i file di mapping sono troppo grandi, usare uno strumento come [https://mapshaper.org/](https://mapshaper.org/) per ridurne le dimensioni.  
  
Vedere come [aggiungere mappe personalizzate ai report per dispositivi mobili](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## <a name="technical-information"></a>Informazioni tecniche  
  
- Specifica ufficiale: [https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Articolo di Wikipedia sui file di forma: [https://en.wikipedia.org/wiki/Shapefile](https://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>Creazione e modifica della geometria di mapping  
  
La creazione e la modifica dei file di forma è un processo complesso che esula dall'ambito di questo documento. Di seguito sono riportate alcune risorse e applicazioni utili per iniziare:  
  
- ArcGIS: [https://www.arcgis.com/](https://www.arcgis.com/)  
- Plug-in MAPublisher per Adobe Illustrator: [https://www.avenza.com/mapublisher](https://www.avenza.com/mapublisher)  
- QuantumGIS (gratuito): [https://www.qgis.org/](https://www.qgis.org/)  
- Manco ShapeFile Editor: [https://www.mancosoftware.com/ShapeFileEditor](https://www.mancosoftware.com/ShapeFileEditor)  
  
## <a name="existing-shapefiles"></a>File di forma esistenti  
  
Molti file di forma esistenti possono essere scaricati dal Web, da siti come i seguenti:  
  
- Diva-GIS: [https://www.diva-gis.org/Data](https://www.diva-gis.org/Data)  
- OpenStreetMap: [https://openstreetmapdata.com/data](https://openstreetmapdata.com/data)  
  
### <a name="see-also"></a>Vedere anche  
- [Eseguire il mapping nei report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
