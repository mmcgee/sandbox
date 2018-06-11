Cartographic Scale Recommendations
======================
Linked Data for Production -- Cartographic Materials Working Group   
June 2018

**Table of Contents**
> - [Overview](#overview)
> - [Relevant Documentation](#documentation)
> - [Summary of Recommendations](#recommendations)
> - [BIBFRAME Approach to Scale](#bibframe)
> - [GCRO Approach to Scale](#recommended_approach)
> - [Side-by-side rdf examples](#examples)
> - [Discussion/Future Work](#future-work)

<a name="overview">Overview</a>
---------


<a name="documentation">Relevant Documentation</a>
------------------------


<a name="recommendations">Summary of Recommendations</a>
---------------------------


-   Define the following new classes:
> - gcro:HorizontalScale
> - gcro:VerticalScale
> - gcro:ScaleIndeterminable
> - gcro:ScaleNotDetermined
> - gcro:NotDrawnToScale
> - gcro:ScaleVaries
> - gcro:ScaleNotGiven
> - gcro:ScalesDiffer
> - gcro:ScaleAccuracy   
> > with new Named Individuals:  
> > -grco:ExplicitScale  
> > -grco:ApproximateScale  
> > -gcro:InaccurateScale  
> > -gcro:ScaleAccuracyUnknown
> - gcro:ScaleSource   
> > with new Named Individuals:  
> > -grco:RepresentativeFraction  
> > -gcro:VerbalStatement  
> > -gcro:ScaleBar  
> > -gcro:CalculatedFromPrimarySource  
> > -gcro:DerivedOther

-   Define the following new properties:
> - gcro:scaleAccuracy
> - gcro:scaleSource
> - gcro:representativeFractionDenominator

<a name="bibframe">BIBFRAME Approach to Scale</a>
---------------------------------

### Model Diagram

![Diagram](/modeling_diagrams/Scale.png)

### Involved Classes

### Involved Properties

**bf:dimensions**
> - **Label:** Dimensions
> - **IRI:** [*http://id.loc.gov/ontologies/bibframe/dimensions*](http://id.loc.gov/ontologies/bibframe/dimensions)
> - **Range:** Literal
> - **Definition:** Measurements of the carrier or carriers and/or the container of a resource.

<a name="recommended_approach">Recommended Approach to Scale</a>
------------------------------------
### Model Diagram

### Involved Classes

### Involved Properties

**ex:MeasurementGroup**
> - **Label**: Measurement Group
> - **IRI:** tbd
> - **Definition:** A set of measurements pertaining to a specific resource, part of a resource, or resource in a particular arrangement. For example, a book may have a specified height, width, length, and/or weight, which are all attached to a MeasurementGroup; the binding may have measurements specified independently, which would constitute another MeasurementGroup. A MeasurementGroup has one or more specific Measurements attached to it.

**ex:Measurement**
> - **Label:** Measurement
> - **IRI:** tbd
> - **Definition:** The measurement of a single aspect of a resource, including value, units, and the aspect measured. For example, a book may have a height (aspect) of 10 (value) centimeters (units). Each such measurement is attached to a MeasurementGroup.

**ex:Arrangement**
> - **Label:** Arrangement
> - **IRI**: tbd
> - **Definition:** The arrangement, organization, or configuration of a single object or collection of objects. For example, a parchment may be rolled or unrolled; a collection of visual materials has a specific arrangement; computer files are organized and ordered in a specific way.

### Involved Properties

**ex:hasMeasurementGroup** (Object property)
> - **Label:** has measurement group
> - **IRI:** tbd
> - **Definition:** The relationship of a resource to a measurement group, indicating that the measurement group applies to the resource.
> - **Domain:** Unspecified
> - **Range:** ex:MeasurementGroup
> - **Inverse:** ex:isMeasurementGroupOf

**ex:isMeasurementGroupOf** (Object property)
> - **Label:** is measurement group of
> - **IRI:** tbd
> - **Definition:** The relationship of a measurement group to a resource, indicating that the measurement group applies to the resource.
> - **Domain:** ex:MeasurementGroup
> - **Range:** Unspecified
> - **Inverse:** ex:hasMeasurementGroup

**ex:hasMeasurement** (Object property)
> - **Label:** has measurement
> - **IRI:** tbd
> - **Definition:** The relationship of a MeasurementGroup to a Measurement, indicating that the Measurement is one part of the MeasurementGroup.
> - **Domain:** Unspecified
> - **Range:** ex:Measurement
> - **Inverse:** ex:isMeasurementOf

**ex:isMeasurementOf** (Object property)
> - **Label:** is measurement of
> - **IRI:** tbd
> - **Definition:** The relationship of a Measurement to a MeasurementGroup, indicating that the Measurement is one part of the MeasurementGroup.
> - **Domain:** ex:Measurement
> - **Range:** ex:MeasurementGroup
> - **Inverse:** ex:hasMeasurement

**ex:measures** (Object property)
> - **Label:** measures
> - **IRI:** tbd
> - **Definition:** The relationship between a Measurement and the dimension or other aspect of a resource that is measured by this Measurement. For example, a Measurement may specify the length, height, weight, file size, etc. of a resource.
> - **Domain:** ex:Measurement
> - **Range:** Unspecified
> - **Inverse:** ex:measuredBy

**ex:measuredBy** (Object property)
> - **Label:** measured by
> - **IRI:** tbd
> - **Definition:** The relationship between a dimension or other aspect of a resource and the Measurement that measures it. For example, the length, height, weight, file size, etc. of a resource may be the aspect that is measured by a particular Measurement.
> - **Domain:** Unspecified
> - **Range:** ex:Measurement
> - **Inverse:** ex:measures

**ex:hasUnit** (Object property)
> - **Label:** has unit
> - **IRI:** tbd
> - **Definition:** Relationship between the measurement and the unit used to express the measurement.
> - **Domain:** Unspecified
> - **Range:** Unspecified
> - **Inverse:** ex:isUnitOf

**ex:isUnitOf** (Object property)
> - **Label:** is unit of
> - **IRI:** tbd
> - **Definition:** Relationship between the measurement and the unit used to express the measurement.
> - **Domain:** Unspecified
> - **Range:** Unspecified
> - **Inverse:** ex:hasUnit

**ex:hasArrangement** (Object property)
> - **Label:** has arrangement
> - **IRI:** tbd
> - **Definition:** Relationship between the resource and a specified arrangement, organization, or configuration of it.
> - **Domain:** Unspecified
> - **Range:** ex:Arrangement
> - **Inverse**: ex:isArrangementOf

**ex:isArrangementOf**
> - **Label:** is arrangement of
> - **IRI:** tbd
> - **Definition:** Relationship between a specified arrangement, organization, or configuration and a resource.
> - **Domain:** ex:Arrangement
> - **Range:** Unspecified
> - **Inverse**: ex:hasArrangement

**dcterms:hasPart**
> - **Label:** Has Part
> - **IRI:** http://purl.org/dc/terms/hasPart
> - **Definition:** A related resource that is included either physically or logically in the described resource.
> - **Note:** This term is intended to be used with non-literal values as defined in the DCMI Abstract Model (http://dublincore.org/documents/abstract-model/). As of December 2007, the DCMI Usage Board is seeking a way to express this intention with a formal range declaration.
> - **subPropertyOf:** http://purl.org/dc/terms/relation

**dcterms:description**
> - **Label:** Description
> - **IRI:**http://purl.org/dc/elements/1.1/description
> - **Definition:** An account of the resource.
> - **Comment:** Description may include but is not limited to: an abstract, a table of contents, a graphical representation, or a free-text account of the resource.
> - **Note:** A second property with the same name as this property has been declared in the dcterms: namespace (http://purl.org/dc/terms/). See the Introduction to the document "DCMI Metadata Terms" (http://dublincore.org/documents/dcmi-terms/) for an explanation.

<a name="examples">Side-by-side rdf examples</a>
---------------------


<a name="future-work">Discussion/Future Work</a>
----------------------
