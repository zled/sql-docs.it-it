---
title: Tipo di elemento (DimensionAttribute) (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element (DimensionAttribute)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 64fce1f5-39b7-4d0a-ae60-21203a03bd0d
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 25fed477ca48cb539ccf6c98f789f2243d67d078
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="type-element-dimensionattribute-assl"></a>Elemento Type (DimensionAttribute) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il tipo dell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <Type>...</Type>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Regular*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Account*|L'attributo rappresenta il nome di un conto.|  
|*AccountNumber*|L'attributo rappresenta il numero di un conto.|  
|*AccountType*|L'attributo rappresenta il tipo di un conto.|  
|*Indirizzo*|L'attributo rappresenta un indirizzo.|  
|*AddressBuilding*|L'attributo rappresenta un identificatore di edificio per un indirizzo.|  
|*AddressCity*|L'attributo rappresenta la città per un indirizzo.|  
|*AddressCountry*|L'attributo rappresenta un paese/area geografica per un indirizzo.|  
|*AddressFax*|L'attributo rappresenta un numero di fax.|  
|*AddressFloor*|L'attributo rappresenta un identificatore di piano per un indirizzo.|  
|*AddressHouse*|L'attributo rappresenta il numero civico per un indirizzo.|  
|*AddressPhone*|L'attributo rappresenta un numero di telefono.|  
|*AddressQuarter*|L'attributo rappresenta un quartiere per un indirizzo.|  
|*AddressRoom*|L'attributo rappresenta l'identificatore di stanza per un indirizzo.|  
|*AddressStateOrProvince*|L'attributo rappresenta la provincia per un indirizzo.|  
|*AddressStreet*|L'attributo rappresenta la via per un indirizzo.|  
|*AddressZip*|L'attributo rappresenta un codice postale per un indirizzo.|  
|*BOMResource*|L'attributo rappresenta una risorsa per una distinta base.|  
|*Caption*|L'attributo rappresenta una didascalia.|  
|*CaptionAbbreviation*|L'attributo rappresenta un'abbreviazione.|  
|*CaptionDescription*|L'attributo rappresenta una descrizione.|  
|*Channel*|L'attributo rappresenta un canale.|  
|*City*|L'attributo rappresenta una città.|  
|*Società*|L'attributo rappresenta una società.|  
|*Continente*|L'attributo rappresenta un continente.|  
|*Paese*|L'attributo rappresenta un paese.|  
|*Provincia*|L'attributo rappresenta una regione.|  
|*CurrencyDestination*|L'attributo rappresenta la valuta di destinazione di un cambio di valuta.|  
|*CurrencyISOcode*|L'attributo rappresenta il codice ISO di una valuta.|  
|*CurrencName*|L'attributo rappresenta il nome di una valuta.|  
|*CurrencySource*|L'attributo rappresenta la valuta di origine di un cambio di valuta.|  
|*CustomerGroup*|L'attributo rappresenta un gruppo di clienti.|  
|*CustomerHousehold*|L'attributo rappresenta un'unità familiare dei clienti.|  
|*Customers*|L'attributo rappresenta un cliente.|  
|*Data*|L'attributo rappresenta una data.|  
|*DateCanceled*|L'attributo rappresenta una data di annullamento.|  
|*DateDuration*|L'attributo rappresenta una durata.|  
|*DateEnded*|L'attributo rappresenta una data di fine.|  
|*DateModified*|L'attributo rappresenta una data di modifica.|  
|*DateStart*|L'attributo rappresenta una data di inizio.|  
|*DayOfHalfYears*|L'attributo rappresenta il numero ordinale di giorno di un semestre.|  
|*DayOfMonth*|L'attributo rappresenta il numero ordinale di giorno di un mese.|  
|*DayOfQuarter*|L'attributo rappresenta il numero ordinale di giorno di un trimestre.|  
|*DayOfTrimester*|L'attributo rappresenta il numero ordinale di giorno di un quadrimestre.|  
|*DayOfWeek*|L'attributo rappresenta il numero ordinale di giorno di una settimana.|  
|*DayOfYear*|L'attributo rappresenta il numero ordinale di giorno di un anno.|  
|*Giorni*|L'attributo rappresenta i giorni.|  
|*DaysOfTenDays*|L'attributo rappresenta il numero ordinale di giorno di una decade.|  
|*FiscalDay*|L'attributo rappresenta i giorni in un calendario fiscale.|  
|*FiscalDayOfHalfYears*|L'attributo rappresenta il numero ordinale di giorno di un semestre in un calendario fiscale.|  
|*FiscalDayOfMonth*|L'attributo rappresenta il numero ordinale di giorno di un mese in un calendario fiscale.|  
|*FiscalDayOfQuarter*|L'attributo rappresenta il numero ordinale di giorno di un trimestre in un calendario fiscale.|  
|*FiscalDayOfTrimester*|L'attributo rappresenta il numero ordinale di giorno di un quadrimestre in un calendario fiscale.|  
|*FiscalDayOfWeek*|L'attributo rappresenta il numero ordinale di giorno di una settimana in un calendario fiscale.|  
|*FiscalDayOfYear*|L'attributo rappresenta il numero ordinale di giorno di un anno in un calendario fiscale.|  
|*FiscalHalfYears*|L'attributo rappresenta i semestri in un calendario fiscale.|  
|*FiscalHalfYearsOfYear*|L'attributo rappresenta il numero ordinale di semestre di un anno in un calendario fiscale.|  
|*FiscalMonth*|L'attributo rappresenta i mesi in un calendario fiscale.|  
|*FiscalMonthOfHalfYears*|L'attributo rappresenta il numero ordinale di mese di un semestre in un calendario fiscale.|  
|*FiscalMonthOfQuarter*|L'attributo rappresenta il numero ordinale di mese di un trimestre in un calendario fiscale.|  
|*FiscalMonthOfTrimester*|L'attributo rappresenta il numero ordinale di mese di un quadrimestre in un calendario fiscale.|  
|*FiscalMonthOfYear*|L'attributo rappresenta il numero ordinale di mese di un anno in un calendario fiscale.|  
|*FiscalQuarter*|L'attributo rappresenta i trimestri n un calendario fiscale.|  
|*FiscalQuarterOfHalfYear*|L'attributo rappresenta il numero ordinale di trimestre di un semestre in un calendario fiscale.|  
|*FiscalQuarterOfYear*|L'attributo rappresenta il numero ordinale di trimestre di un anno in un calendario fiscale.|  
|*FiscalTrimester*|L'attributo rappresenta i quadrimestri in un calendario fiscale.|  
|*FiscalTrimesterOfYear*|L'attributo rappresenta il numero ordinale di quadrimestre di un anno in un calendario fiscale.|  
|*FiscalWeek*|L'attributo rappresenta le settimane in un calendario fiscale.|  
|*FiscalWeekOfHalfYears*|L'attributo rappresenta il numero ordinale di settimana di un semestre in un calendario fiscale.|  
|*FiscalWeekOfMonth*|L'attributo rappresenta il numero ordinale di settimana di un mese in un calendario fiscale.|  
|*FiscalWeekOfQuarter*|L'attributo rappresenta il numero ordinale di settimana di un trimestre in un calendario fiscale.|  
|*FiscalWeekOfTrimester*|L'attributo rappresenta il numero ordinale di settimana di un quadrimestre in un calendario fiscale.|  
|*FiscalWeekOfYear*|L'attributo rappresenta il numero ordinale di settimana di un anno in un calendario fiscale.|  
|*FiscalYear*|L'attributo rappresenta gli anni.|  
|*FormattingColor*|L'attributo rappresenta il colore utilizzato per la formattazione.|  
|*FormattingFont*|L'attributo rappresenta il tipo di carattere utilizzato per la formattazione.|  
|*FormattingFontEffects*|L'attributo rappresenta gli effetti di carattere utilizzati per la formattazione.|  
|*FormattingFontSize*|L'attributo rappresenta le dimensioni del carattere utilizzate per la formattazione.|  
|*FormattingOrder*|L'attributo rappresenta l'ordinamento utilizzato per la formattazione.|  
|*FormattingSubtotal*|L'attributo rappresenta un sottototale.|  
|*GeoBoundaryBottom*|L'attributo rappresenta il valore più in basso di un confine geografico.|  
|*GeoBoundaryFront*|L'attributo rappresenta il valore più anteriore di un confine geografico.|  
|*GeoBoundaryLeft*|L'attributo rappresenta il valore più a sinistra di un confine geografico.|  
|*GeoBoundaryPolygon*|L'attributo rappresenta la definizione di poligono di un confine geografico.|  
|*GeoBoundaryRear*|L'attributo rappresenta il valore più posteriore di un confine geografico.|  
|*GeoBoundaryRight*|L'attributo rappresenta il valore più a destra di un confine geografico.|  
|*GeoBoundaryTop*|L'attributo rappresenta il valore più in alto di un confine geografico.|  
|*GeoCentroidX*|L'attributo rappresenta il centro dell'asse X per un'area geografica.|  
|*GeoCentroidY*|L'attributo rappresenta il centro dell'asse Y per un'area geografica.|  
|*GeoCentroidZ*|L'attributo rappresenta il centro dell'asse Z per un'area geografica.|  
|*HalfYears*|L'attributo rappresenta i semestri.|  
|*HalfYearsOfYear*|L'attributo rappresenta il numero ordinale di semestre di un anno.|  
|*Ore*|L'attributo rappresenta le ore.|  
|*Id*|L'attributo rappresenta un identificatore o una chiave.|  
|*IsHoliday*|L'attributo indica se una data rappresenta un giorno festivo.|  
|*ISO8601DayOfWeek*|L'attributo rappresenta il numero ordinale di giorno di una settimana in un calendario ISO 8601.|  
|*ISO8601DayOfYear*|L'attributo rappresenta il numero ordinale di  giorno di un anno in un calendario ISO 8601.|  
|*ISO8601Days*|L'attributo rappresenta i giorni in un calendario ISO 8601.|  
|*ISO8601Week*|L'attributo rappresenta le settimane in un calendario ISO 8601.|  
|*ISO8601WeekOfYear*|L'attributo rappresenta il numero ordinale di  settimana di un anno in un calendario ISO 8601.|  
|*ISO8601Year*|L'attributo rappresenta gli anni in un calendario ISO 8601.|  
|*IsWeekDay*|L'attributo indica se una data rappresenta un giorno feriale.|  
|*IsWorkingDay*|L'attributo indica se una data rappresenta un giorno lavorativo.|  
|*ManufacturingDay*|L'attributo rappresenta i giorni in un calendario di produzione.|  
|*ManufacturingDayOfHalfYears*|L'attributo rappresenta il numero ordinale di giorno di un semestre in un calendario di produzione.|  
|*ManufacturingDayOfMonth*|L'attributo rappresenta il numero ordinale di giorno di un mese in un calendario di produzione.|  
|*ManufacturingDayOfQuarter*|L'attributo rappresenta il numero ordinale di giorno di un trimestre in un calendario di produzione.|  
|*ManufacturingDayOfTrimester*|L'attributo rappresenta il numero ordinale di giorno di un quadrimestre in un calendario di produzione.|  
|*ManufacturingDayOfWeek*|L'attributo rappresenta il numero ordinale di giorno di una settimana in un calendario di produzione.|  
|*ManufacturingDayOfYear*|L'attributo rappresenta il numero ordinale di giorno di un anno in un calendario di produzione.|  
|*ManufacturingHalfYears*|L'attributo rappresenta i semestri in un calendario di produzione.|  
|*ManufacturingHalfYearsOfYear*|L'attributo rappresenta il numero ordinale di semestre di un anno in un calendario di produzione.|  
|*ManufacturingMonth*|L'attributo rappresenta i mesi in un calendario di produzione.|  
|*ManufacturingMonthOfHalfYears*|L'attributo rappresenta il numero ordinale di mese di un semestre in un calendario di produzione.|  
|*ManufacturingMonthOfQuarter*|L'attributo rappresenta il numero ordinale di mese di un trimestre in un calendario di produzione.|  
|*ManufacturingMonthOfTrimester*|L'attributo rappresenta il numero ordinale di mese di un quadrimestre in un calendario di produzione.|  
|*ManufacturingMonthOfYear*|L'attributo rappresenta il numero ordinale di mese di un anno in un calendario di produzione.|  
|*ManufacturingQuarter*|L'attributo rappresenta i trimestri in un calendario di produzione.|  
|*ManufacturingQuarterOfHalfYear*|L'attributo rappresenta il numero ordinale di trimestre di un semestre in un calendario di produzione.|  
|*ManufacturingQuarterOfYear*|L'attributo rappresenta il numero ordinale di trimestre di un anno in un calendario di produzione.|  
|*ManufacturingTrimester*|L'attributo rappresenta i quadrimestri in un calendario di produzione.|  
|*ManufacturingTrimesterOfYear*|L'attributo rappresenta il numero ordinale di quadrimestre di un anno in un calendario di produzione.|  
|*ManufacturingWeek*|L'attributo rappresenta le settimane in un calendario di produzione.|  
|*ManufacturingWeekOfHalfYears*|L'attributo rappresenta il numero ordinale di settimana di un semestre in un calendario di produzione.|  
|*ManufacturingWeekOfMonth*|L'attributo rappresenta il numero ordinale di settimana di un mese in un calendario di produzione.|  
|*ManufacturingWeekOfQuarter*|L'attributo rappresenta il numero ordinale di settimana di un trimestre in un calendario di produzione.|  
|*ManufacturingWeekOfTrimester*|L'attributo rappresenta il numero ordinale di settimana di un quadrimestre in un calendario di produzione.|  
|*ManufacturingWeekOfYear*|L'attributo rappresenta il numero ordinale di settimana di un anno in un calendario di produzione.|  
|*ManufacturingYear*|L'attributo rappresenta gli anni in un calendario di produzione.|  
|*Minutes*|L'attributo rappresenta i minuti.|  
|*MonthOfHalfYears*|L'attributo rappresenta il numero ordinale di mese di un semestre.|  
|*MonthOfQuarter*|L'attributo rappresenta il numero ordinale di mese di un trimestre.|  
|*MonthOfTrimester*|L'attributo rappresenta il numero ordinale di mese di un quadrimestre.|  
|*Mese dell'anno*|L'attributo rappresenta il numero ordinale di mese di un anno.|  
|*Mesi*|L'attributo rappresenta i mesi.|  
|*Unità organizzativa*|L'attributo rappresenta un'unità organizzativa.|  
|*OrgTitle*|L'attributo rappresenta una posizione organizzativa.|  
|*PercentOwnership*|L'attributo rappresenta una percentuale di proprietà.|  
|*PercentVoteRight*|L'attributo rappresenta una percentuale di diritti di voto.|  
|*Persona*|L'attributo rappresenta una persona.|  
|*PersonContact*|L'attributo rappresenta le informazioni di recapito per una persona.|  
|*PersonDemographic*|L'attributo rappresenta le informazioni demografiche per una persona.|  
|*PersonFirstName*|L'attributo rappresenta il nome di una persona.|  
|*PersonFullName*|L'attributo rappresenta il nome e il cognome di una persona.|  
|*PersonLastName*|L'attributo rappresenta il cognome di una persona.|  
|*PersonMiddleName*|L'attributo rappresenta il secondo nome di una persona.|  
|*PhysicalColor*|L'attributo rappresenta un colore.|  
|*PhysicalDensity*|L'attributo rappresenta la densità.|  
|*PhysicalDepth*|L'attributo rappresenta la profondità.|  
|*PhysicalHeight*|L'attributo rappresenta l'altezza.|  
|*PhysicalSize*|L'attributo rappresenta le dimensioni.|  
|*PhysicalVolume*|L'attributo rappresenta il volume.|  
|*PhysicalWeight*|L'attributo rappresenta il peso.|  
|*PhysicalWidth*|L'attributo rappresenta la larghezza.|  
|*Point*|L'attributo rappresenta un punto.|  
|*PostalCode*|L'attributo rappresenta un CAP.|  
|*Product*|L'attributo rappresenta un prodotto.|  
|*ProductBrand*|L'attributo rappresenta una marca di prodotto.|  
|*ProductCategory*|L'attributo rappresenta una categoria di prodotti.|  
|*ProductGroup*|L'attributo rappresenta un gruppo di prodotti.|  
|*ProductSKU*|L'attributo rappresenta un codice di riferimento di un prodotto (SKU, Stock Keeping Unit).|  
|*ProjectCode*|L'attributo rappresenta il codice di un progetto.|  
|*Projectcompletion*|L'attributo rappresenta lo stato di completamento di un progetto.|  
|*ProjectEnddate*|L'attributo rappresenta la data di fine di un progetto.|  
|*NomeProgetto*|L'attributo rappresenta il nome di un progetto.|  
|*ProjectStartDate*|L'attributo rappresenta la data di inizio di un progetto.|  
|*Promotion*|L'attributo rappresenta una promozione.|  
|*QtyRangeHigh*|L'attributo rappresenta il valore massimo in un intervallo di quantità.|  
|*QtyRangeLow*|L'attributo rappresenta il valore minimo in un intervallo di quantità.|  
|*Quantitative*|L'attributo rappresenta un attributo quantitativo.|  
|*QuarterOfHalfYear*|L'attributo rappresenta il numero ordinale di trimestre di un semestre.|  
|*QuarterOfYear*|L'attributo rappresenta il numero ordinale di trimestre di un anno.|  
|*Trimestri*|L'attributo rappresenta i trimestri.|  
|*Frequenza*|L'attributo rappresenta un tasso.|  
|*RateType*|L'attributo rappresenta un tipo di tasso.|  
|*Region*|L'attributo rappresenta una regione definita dal cliente.|  
|*Regular*|L'attributo rappresenta un attributo regolare.|  
|*RelationToParent*|L'attributo rappresenta una relazione con un elemento padre.|  
|*ReportingDay*|L'attributo rappresenta i giorni in un calendario di report.|  
|*ReportingDayOfHalfYears*|L'attributo rappresenta il numero ordinale di giorno di un semestre in un calendario di report.|  
|*ReportingDayOfMonth*|L'attributo rappresenta il numero ordinale di giorno di un mese in un calendario di report.|  
|*ReportingDayOfQuarter*|L'attributo rappresenta il numero ordinale di giorno di un trimestre in un calendario di report.|  
|*ReportingDayOfTrimester*|L'attributo rappresenta il numero ordinale di giorno di un quadrimestre in un calendario di report.|  
|*ReportingDayOfWeek*|L'attributo rappresenta il numero ordinale di giorno di un settimana in un calendario di report.|  
|*ReportingDayOfYear*|L'attributo rappresenta il numero ordinale di giorno di un anno in un calendario di report.|  
|*ReportingHalfYears*|L'attributo rappresenta i semestri in un calendario di report.|  
|*ReportingHalfYearsOfYear*|L'attributo rappresenta il numero ordinale di semestre di un anno in un calendario di reporting.|  
|*ReportingMonth*|L'attributo rappresenta i mesi in un calendario di report.|  
|*ReportingMonthOfHalfYears*|L'attributo rappresenta il numero ordinale di mese di un semestre in un calendario di reporting.|  
|*ReportingMonthOfQuarter*|L'attributo rappresenta il numero ordinale di mese di un trimestre in un calendario di reporting.|  
|*ReportingMonthOfTrimester*|L'attributo rappresenta il numero ordinale di mese di un quadrimestre in un calendario di reporting.|  
|*ReportingMonthOfYear*|L'attributo rappresenta il numero ordinale di mese di un anno in un calendario di reporting.|  
|*ReportingQuarter*|L'attributo rappresenta i trimestri in un calendario di reporting.|  
|*ReportingQuarterOfHalfYear*|L'attributo rappresenta il numero ordinale di trimestre di un semestre in un calendario di reporting.|  
|*ReportingQuarterOfYear*|L'attributo rappresenta il numero ordinale di trimestre di un anno in un calendario di reporting.|  
|*ReportingTrimester*|L'attributo rappresenta i quadrimestri in un calendario di reporting.|  
|*ReportingTrimesterOfYear*|L'attributo rappresenta il numero ordinale di quadrimestre di un anno in un calendario di reporting.|  
|*ReportingWeek*|L'attributo rappresenta le settimane in un calendario di reporting.|  
|*ReportingWeekOfHalfYears*|L'attributo rappresenta il numero ordinale di settimana di un semestre in un calendario di reporting.|  
|*ReportingWeekOfMonth*|L'attributo rappresenta il numero ordinale di settimana di un mese in un calendario di reporting.|  
|*ReportingWeekOfQuarter*|L'attributo rappresenta il numero ordinale di settimana di un trimestre in un calendario di reporting.|  
|*ReportingWeekOfTrimester*|L'attributo rappresenta il numero ordinale di settimana di un quadrimestre in un calendario di reporting.|  
|*ReportingWeekOfYear*|L'attributo rappresenta il numero ordinale di settimana di un anno in un calendario di reporting.|  
|*ReportingYear*|L'attributo rappresenta gli anni in un calendario di reporting.|  
|*Rappresentante*|L'attributo rappresenta un rappresentante.|  
|*Scenario*|L'attributo rappresenta uno scenario.|  
|*Secondi*|L'attributo rappresenta i secondi.|  
|*Sequence*|L'attributo rappresenta un attributo di sequenza.|  
|*ShortCaption*|L'attributo rappresenta una didascalia breve.|  
|*StateOrProvince*|L'attributo rappresenta uno stato o una provincia.|  
|*TenDayOfHalfYears*|L'attributo rappresenta il numero ordinale di decade di un semestre.|  
|*TenDayOfQuarter*|L'attributo rappresenta il numero ordinale di decade di un trimestre.|  
|*TenDayOfTrimester*|L'attributo rappresenta il numero ordinale di decade di un quadrimestre.|  
|*TenDayOfYear*|L'attributo rappresenta il numero ordinale di decade di un anno.|  
|*TenDays*|L'attributo rappresenta le decadi.|  
|*TenDaysOfMonth*|L'attributo rappresenta il numero ordinale di decade di un mese.|  
|*Quadrimestre*|L'attributo rappresenta i quadrimestri.|  
|*TrimesterOfYear*|L'attributo rappresenta il numero ordinale di quadrimestre di un anno.|  
|*UndefinedTime*|L'attributo rappresenta un periodo di tempo indefinito.|  
|*Utilità*|L'attributo rappresenta un'utilità.|  
|*Version*|L'attributo rappresenta una versione.|  
|*WebHtml*|L'attributo rappresenta contenuto HTML.|  
|*WebMailAlias*|L'attributo rappresenta un alias di posta elettronica.|  
|*WebUrl*|L'attributo rappresenta un indirizzo URL.|  
|*WebXmlOrXsl*|L'attributo rappresenta contenuto XML o XSL.|  
|*WeekOfHalfYears*|L'attributo rappresenta il numero ordinale di settimana di un semestre.|  
|*WeekOfMonth*|L'attributo rappresenta il numero ordinale di settimana di un mese.|  
|*WeekOfQuarter*|L'attributo rappresenta il numero ordinale di settimana di un trimestre.|  
|*WeekOfTrimester*|L'attributo rappresenta il numero ordinale di settimana di un quadrimestre.|  
|*WeekOfYear*|L'attributo rappresenta il numero ordinale di settimana di un anno.|  
|*Settimane*|L'attributo rappresenta le settimane.|  
|*Anni*|L'attributo rappresenta gli anni.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AttributeType>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi elemento &#40;ASSL&#41;](../../../analysis-services/scripting/collections/attributes-element-assl.md)   
 [Elemento Dimension & #40; ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
