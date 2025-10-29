# GS1 Web Vocabulary - development site

The current, ratified, version of the GS1 Web vocabualary is published at https://ref.gs1.org/voc. It is an external extension to schema.org that allows further details about products and assets to be expressed using Linked Data technology. [gs1:Product](https://ref.gs1.org/voc/Product) is semantically equivalent to [schema:Product](http://schema.org/Product). The GS1 Web vocabulary also defines subclasses of [gs1:Product](https://ref.gs1.org/voc/Product)

The GS1 Web vocabulary is released under an Apache 2.0 licence. A further licence statement is provided within the GS1 Web vocabulary files.
 
This repository is intended to encourage suggestions for improvements to the GS1 Web Vocabulary. Please note the license terms (Apache 2.0). 

Most terms within the GS1 Web vocabulary can usually be classified as one of the following:

* [Classes](#classes)
* [Properties](#properties)
* [Code Lists](#code-lists)
* [Defined values within Code Lists](#code-list-values)
* [Link Types](#link-types)


## Classes

One use of a class (rdfs:Class, owl:Class) is to express an entity such as a product, organization, place, postal address.

Another use of a class is to provide a repeatable data structure as a container for a number of interdependent properties.

For example, a [gs1:QuantitativeValue](https://ref.gs1.org/voc/QuantitativeValue)  or [schema:QuantitativeValue](http://schema.org/QuantitativeValue) express both a numeric value and a code for a unit of measure.  

Similarly, [gs1:CertificationDetails](https://ref.gs1.org/voc/CertificationDetails) is used to group interdependent properties such as [gs1:certificationAgency](https://ref.gs1.org/voc/certificationAgency) , [gs1:certificationStandard](https://ref.gs1.org/voc/certificationStandard) and [gs1:certificationValue](https://ref.gs1.org/voc/certificationValue) so that when a product has more than one certification, there is no ambiguity about which standard was evaluated by which agency - or which value was obtained for each standard.

Some classes are defined as subclasses of other classes.

For example, 

[gs1:FoodBeverageTobaccoProduct](https://ref.gs1.org/voc/FoodBeverageTobaccoProduct) is a subclass of [gs1:Product](https://ref.gs1.org/voc/Product)

[gs1:FruitsVegetables](https://ref.gs1.org/voc/FruitsVegetables) is a subclass of [gs1:FoodBeverageTobaccoProduct](https://ref.gs1.org/voc/FoodBeverageTobaccoProduct)

By defining subclasses, we can 'attach' more specialised properties that are relevant to the subclass but not generally relevant to all members of the parent class / superclass.

[Browse all classes within the GS1 Web vocabulary](https://ref.gs1.org/voc/?show=classes)

## Properties
Each property has an expected value type (indicated via rdfs:range)

Each property also has an 'attachment point' (indicated via rdfs:domain)

A property that could apply to all kinds of products will generally have an rdfs:domain of [gs1:Product](https://ref.gs1.org/voc/Product) / [schema:Product](http://schema.org/Product)

Other properties that are only really relevant to a more specialised category of products will have an rdfs:domain that is a subclass of [gs1:Product](https://ref.gs1.org/voc/Product) (such as [gs1:WearableProduct](https://ref.gs1.org/voc/WearableProduct) ) or even a subclass of a subclass of [gs1:Product](https://ref.gs1.org/voc/Product) (such as [gs1:Footwear](https://ref.gs1.org/voc/Footwear) )

For example, 

[gs1:isSeedless](https://ref.gs1.org/voc/isSeedless) is a property of [gs1:FruitsVegetables](https://ref.gs1.org/voc/FruitsVegetables) - and it probably has little relevance to any other kind of product.

Formally, the GS1 Web vocabulary expresses that [gs1:isSeedless](https://ref.gs1.org/voc/isSeedless) has an rdfs:domain of [gs1:FruitsVegetables](https://ref.gs1.org/voc/FruitsVegetables).

[Browse all properties within the GS1 Web vocabulary](https://ref.gs1.org/voc/?show=properties)

## Code Lists
The GS1 Web vocabulary defines a large number of code lists for enumerated values.
Code lists are useful because a globally defined URI can be used for each permitted value.  Each of these URIs may have multilingual labels and descriptions in different human languages but we agree to use the global URI to express the value, to avoid the need to translate 'free text' values expressed in different human languages when exchanging data globally using such code lists.

Each code list is modelled as a class (rdfs:Class, owl:Class) and as a subclass of [gs1:TypeCode](https://ref.gs1.org/voc/TypeCode), the abstract superclass for all GS1 Code Lists within the GS1 Web vocabulary.

For example,
[gs1:SharpnessOfCheeseCode](https://ref.gs1.org/voc/SharpnessOfCheeseCode) is a subclass of [gs1:TypeCode](https://ref.gs1.org/voc/TypeCode)

[Browse all code lists within the GS1 Web vocabulary](https://ref.gs1.org/voc/?show=typecodes)


## Code list values
Each defined value within a code list has its own Web URI and may have multilingual human labels and descriptions.  Membership of a particular code list is indicated via rdf:type

For example,
[gs1:SharpnessOfCheeseCode-EXTRA_SHARP](https://ref.gs1.org/voc/SharpnessOfCheeseCode-EXTRA_SHARP) is an individual code value within the [gs1:SharpnessOfCheeseCode](https://ref.gs1.org/voc/SharpnessOfCheeseCode) code list.

Its rdf:type is [gs1:SharpnessOfCheeseCode](https://ref.gs1.org/voc/SharpnessOfCheeseCode), the code list to which it belongs.

## Link Types
The GS1 Web vocabulary introduced a group of additional properties that connect a [GS1 Digital Link](https://ref.gs1.org/standards/digital-link/uri-syntax/) URI to a target resource URL, such as a product information page, instruction manual, related video, electronic patient information leaflet for a pharmaceutical etc.  

Each link type property expresses a distinct kind of information resource found at the target resource URL.  

In this way, a Web request to a resolver for [GS1 Digital Link](https://ref.gs1.org/standards/resolver) can specify a particular kind of information resource that is desired, e.g. 'give me the instruction manual'.  The Link Type is typically expressed as a compact URI expression (CURIE) within the URI query string, as the value of the special 'linkType' key.  It is also expressed in the linkset of results returned by a [GS1-Conformant resolver](https://ref.gs1.org/standards/resolver/).

The GS1 Web vocabulary defines one abstract property, [gs1:linkType](https://ref.gs1.org/voc/linkType).  

All specific link type values are defined as a subproperty of [gs1:linkType](https://ref.gs1.org/voc/linkType).

For example,
[gs1:instructions](https://ref.gs1.org/voc/instructions) is a subproperty of [gs1:linkType](https://ref.gs1.org/voc/linkType)  

[gs1:instructions](https://ref.gs1.org/voc/instructions) is a typed link that is used to link to instructions related to the product, such as assembly instructions, usage tips etc.

[Browse all link types defined within the GS1 Web vocabulary](https://ref.gs1.org/voc/?show=linktypes)
