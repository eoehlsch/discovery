---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Configuring your service

Building a {{site.data.keyword.discoveryshort}} service will make it possible to gain useful insights by enriching your own data and then delivering it in a query-able form.
{: shortdesc}

Before you add your own content to the {{site.data.keyword.discoveryshort}} service, you should configure the service to process the content the way that you want.

The first step is to configure the basic parameters of the service ([Preparing the service for your documents](/docs/services/discovery/building.html#preparing-the-service-for-your-documents)), this includes creating an environment and creating one or more collections within that environment. When a collection is created, a set of defaults ([The default configuration](/docs/services/discovery/building.html#the-default-configuration)) are automatically provided. If you are happy with these defaults, you can proceed to uploading your content ([Adding content](/docs/services/discovery/adding-content.html)).

However, you will most likely want to specify one or more custom configurations (see [When you need a custom configuration](/docs/services/discovery/building.html#when-you-need-a-custom-configuration)). If this is the case, you will need to do the following:

-   identify some sample content (documents that are representative of your files)
-   upload the content ([Uploading sample documents](/docs/services/discovery/building.html#uploading-sample-documents))
-   adjust the conversion process ([Converting sample documents](/docs/services/discovery/building.html#converting-sample-documents))
-   define enrichments ([Adding enrichments](/docs/services/discovery/building.html#adding-enrichments))
-   normalize the results ([Normalizing data](/docs/services/discovery/building.html#normalizing-data))

    After you have created your custom configuration, you can upload your documents ([Adding content](/docs/services/discovery/adding-content.html)).

## Preparing the service for your documents
{: #preparing-the-service-for-your-documents}

In the {{site.data.keyword.discoveryshort}} service, the content that you upload is stored in a collection that is part of your environment. You must create the environment and collection before you can upload your content.

-   **Environment** — The environment defines the amount of storage space that you have for content in the {{site.data.keyword.discoveryshort}} service. A maximum of one environment can be created for each instance of the {{site.data.keyword.discoveryshort}} service.

    You have several plans (Lite, Standard, and Advanced) to choose from, see the [{{site.data.keyword.discoveryshort}} catalog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/catalog/services/discovery/){: new_window} for details. Your source files do not count against your file size limit.

-   **Collection** — A collection is a grouping of your content within the environment. You must create at least one collection to be able to upload your content.

    Collections are comprised of your private data, but {{site.data.keyword.discoveryshort}} also includes {{site.data.keyword.discoverynewsshort}}, a pre-enriched, public dataset. You can use it to query for insights; for example: news alerts, event detecting, and trending topics in the news; that you can integrate into your applications.

    {{site.data.keyword.discoverynewsshort}}, a public data set that has been pre-enriched with cognitive insights, is also included with {{site.data.keyword.discoveryshort}}. See [Watson Discovery News](/docs/services/discovery/watson-discovery-news.html#watson-discovery-news) for more information. You cannot adjust the {{site.data.keyword.discoverynewsshort}} configuration or add documents to this collection. See a demo of what you can build with {{site.data.keyword.discoverynewsshort}} [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://discovery-news-demo.mybluemix.net/){: new_window}.

    **Note:** It is not possible to query multiple collections with a single query call.

To create an environment and private data collection with the {{site.data.keyword.discoveryshort}} tooling do the following:

1.  On the **Your Data** screen, click the icon on the upper right ![Cog](images/icon_settings.png) and choose **Create environment**. The environment is created based on the Bluemix plan you selected earlier. The status of your environment is always available from this drop-down.

1.  Once your environment is ready, click the **Create a data collection** button, then you can **Name your new collection**.

    By default, the configuration file will be **Default Configuration**. If you have another configuration file available, you can choose it, or you can create a new one later and apply it to this collection. You can also select the language of the documents you will add to this collection: English, Spanish, or German. There should be only one language in each of your collections. After you click **Create**, your data collection will appear as a tile.

Your environment and data collection are ready! If you wish to use the default configuration file, you can start [Adding content](/docs/services/discovery/adding-content.html) immediately. But if you want to customize your {{site.data.keyword.discoveryshort}} configuration with additional enrichments and conversion settings, you should not begin adding documents right now, you should start creating your custom configuration file. See [Configuring your service](/docs/services/discovery/building.html#custom-configuration).

**Note:** When documents are uploaded to a data collection, they are converted and enriched using the configuration file chosen for that collection. If you decide later that you would like to switch a collection to a different configuration file, you can do that, but the documents that have already been uploaded will remain converted by the original configuration file. All documents uploaded after switching the configuration file will use the new configuration file. If you want the **entire** collection to use the new configuration, you will need to create a new collection, choose that new configuration file, and re-upload all the documents.

### The default configuration
{: #the-default-configuration}

The {{site.data.keyword.discoveryshort}} service includes a standard configuration file that will convert, enrich and normalize your data without requiring you to manually configure these options.

This default configuration file is named **Default Configuration**. It contains enrichments, plus standard document conversions based on font styles and sizes.

First the default enrichments. {{site.data.keyword.discoveryshort}} will enrich (add cognitive metadata to) the text field of your documents with semantic information collected by four {{site.data.keyword.watson}} Enrichments — Entity Extraction, Sentiment Analysis, Category Classification, and Concept Tagging (learn more about them [here](/docs/services/discovery/building.html#adding-enrichments)).

**Note:** Starting on **18 July, 2017** {{site.data.keyword.discoveryfull}} introduced a new enrichment technology, named {{site.data.keyword.nlushort}} (NLU). See [Adding enrichments](/docs/services/discovery/building.html#adding-enrichments) for details. If you applied the **Default Configuration** to a collection prior to this date, that collection was enriched with the {{site.data.keyword.alchemylanguageshort}} enrichments. If you apply the **Default Configuration** to a collection after this date, the {{site.data.keyword.nlushort}} Enrichments will be used.

-   [Microsoft Word conversion](/docs/services/discovery/building.html#microsoft-word-conversion)
-   [PDF conversion](/docs/services/discovery/building.html#pdf-conversion)
-   [HTML conversion](/docs/services/discovery/building.html#html-conversion)
-   [JSON conversion](/docs/services/discovery/building.html#json-conversion)

If you would like to create a custom configuration, see [Custom configuration](/docs/services/discovery/building.html#custom-configuration).

### When you need a custom configuration
{: #when-you-need-a-custom-configuration}

Getting the right information out of your content and returning it to your users is the goal of the {{site.data.keyword.discoveryshort}} service. Identifying what that information is, and how it is stored in your content is defined by the configuration that you use to ingest the content. The content types that the {{site.data.keyword.discoveryshort}} service can ingest are flexible, meaning that even though your unstructured content is saved in a specific format, it is not required that the structure of that content match the structure of other content of the same type.

-   **I understand that my documents may not be structured in the way the default configuration expects. *How do I know if the default
    settings are right for me?***
    -   The easiest way to see if the default works for you is to test it by [Uploading sample documents](/docs/services/discovery/building.html#uploading-sample-documents). If the sample JSON results meet your expectations, then no additional configuration is required.
-   **I understand that default enrichments are added to the text field of my documents. Can I add additional enrichments to other fields?**
    -   Absolutely, you can add additional enrichments to as many fields as you wish. See [Adding enrichments](/docs/services/discovery/building.html#adding-enrichments) for details.

## Custom configuration
{: #custom-configuration}

To create a custom configuration in the {{site.data.keyword.discoveryshort}} tooling, open a Private data collection, and on the **Your Data** screen, click **Switch** next to the name of your **Configuration**. On the **Switch configuration** dialog, click **Create a new configuration**.

After you have named your new configuration file, that name will be displayed at the top of the configuration screen. This new configuration file will automatically contain the settings and enrichments of the [Default configuration](/docs/services/discovery/building.html#the-default-configuration) file to give you a place to begin.

The three steps of customizing a configuration file are: **Convert**, **Enrich**, and **Normalize**.

1.  [Converting sample documents](/docs/services/discovery/building.html#converting-sample-documents)
1.  [Adding enrichments](/docs/services/discovery/building.html#adding-enrichments)
1.  [Normalizing data](/docs/services/discovery/building.html#normalizing-data)

### Uploading sample documents
{: #uploading-sample-documents}

To make the configuration process more efficient, you can upload up to ten Microsoft Word, HTML, JSON, or PDF files that are representative of your document set. These are called **sample documents**. Sample documents are not added to your collection — they are only used to identify fields that are common to your documents and customize those fields to your requirements.

When creating a new configuration file in the {{site.data.keyword.discoveryshort}} tooling, you can upload sample documents via drag and drop or browse. Click on the file name in the **Upload Sample Documents** pane to preview each file.

#### Remember the following items when uploading sample documents:

-   All of your documents are converted to JSON before they are enriched and indexed.
-   Microsoft Word and PDF documents are converted to HTML first, then JSON.
-   HTML documents are converted directly to JSON.
-   The maximum file size for a sample document is 5MB. Sample documents are automatically deleted after 1 month, but you can upload the same documents again if you would like to make additional changes to your configuration.

#### Guidelines for choosing good sample documents:

-   You should have (at minimum), one sample document for each file type you intend to ingest - Microsoft Word, PDF, HTML, and JSON.
-   If you have any unique document types (such as financial reports or press releases), include one of each in your set of sample documents.
-   For HTML documents, you should choose documents that include HTML tags you would like to exclude, as well as tag attributes you would like to include or exclude.
-   JSON documents should include any fields you would like to remove or merge together (for example, zipCode and postalCode).

### Converting sample documents
{: #converting-sample-documents}

Converting your sample documents is the process that will let you define how each input type is handled. The file type of content that you upload dictates the number of conversion steps that you will have to consider.

Before you start, [upload your sample documents](/docs/services/discovery/building.html#uploading-sample-documents), and open a sample document of the file type you'd like to configure in the pane on the right.

To work through the Conversion settings, click through the file types.

![Converting a sample document](images/convert.png)

-   **If you are converting Microsoft Word files you must do the following:**
    -   Set the Microsoft Word conversion options
    -   Set the HTML conversion options
    -   Set the JSON conversion options
    -   Review the result

-   **If you are converting PDF files you must do the following:**
    -   Set the PDF conversion options
    -   Set the HTML conversion options
    -   Set the JSON conversion options
    -   Review the result

-   **If you are converting HTML files you must do the following:**
    -   Set the HTML conversion options
    -   Set the JSON conversion options
    -   Review the result

-   **If you are converting JSON files** you must set the JSON conversion options and review the result.

For each configuration file that you create, there is only one set of conversion options for each step of the process. This means the HTML conversion options will be the same for PDF files, Word files, and HTML. If you require different conversion options for each type of content that you are ingesting (or if you have files of the same type that will require different types of conversion) you will need to store your files in different collections and create separate configuration files for each set of conversion settings.

#### Microsoft Word conversion
{: #microsoft-word-conversion}

Microsoft Word font sizes and font styles are used to convert the headings in your documents properly into H1, H2, and so on. H1's are the document title, and H2's and below are subheadings. Use the text boxes and radio buttons to change the default settings if you wish. You can also add additional heading levels and Word styles. If your Word documents tend to use a specific font or style name for headings, make sure to add that information. This will help improve your conversion, which will yield better query results.

**Example:** If it is common for your Word documents to use a 20 pt font, italic for heading 2s - change the **Font size range** to **20** to **23** and the **Font style** to **italic**.

After making any changes, click **Apply and Save**.

#### PDF conversion
{: #pdf-conversion}

PDF font sizes and font names are used to convert the headings in your documents properly into H1, H2, and so on. H1's are the document title, and H2 and below are subheadings. Use the text boxes and radio buttons to change the default settings if you wish. You can also add additional heading levels. If your PDF documents tend to use a specific font for headings, make sure to add that information. This will help improve your conversion, which will yield better query results.

**Example:** If it is common for your PDF documents to use a 20 pt font, bold for heading 1s - change the **Font size range** to **20** to **80** and the **Font style** to **bold**. Adjust the other levels accordingly.

After making any changes, click **Apply and Save**.

#### HTML conversion
{: #html-conversion}

You can use this step to remove unnecessary tags and other document info so that you retain only the information you need for your queries.

Default HTML settings:

- Exclude these tags, as well as their content: **`script`**, **`sup`**
- Exclude these tags, but keep their content: **`font`**, **`em`**, **`span`**
- Keep these tag attributes: no default
- Exclude these tag attributes: **`EVENT_ACTIONS`**
- Keep content that matches this/these XPath(s): no default
- Exclude content that matches this/these XPath(s): no default

After making any changes, click **Apply and Save**.

#### JSON conversion
{: #json-conversion}

The last step of the conversion is to ensure that the converted (or uploaded JSON) is formed the way that you expect it to be before enrichments are applied to the content. You can create rules {{site.data.keyword.watson}} will use to convert your HTML to JSON.

-   You can move, merge, copy or remove fields. For example: You may want to merge **`zipCode`** and **`postalCode`** because they are two similar terms for the same field.
-   Empty fields (fields that contain no information) will be deleted by default. You can change that using the **Remove empty fields** toggle.

After making any changes, click **Apply and Save**.

## Adding enrichments
{: #adding-enrichments}

**Note:** Starting on **18 July, 2017** {{site.data.keyword.discoveryfull}} introduced a new enrichment technology, named {{site.data.keyword.nlushort}} (NLU).  These enrichments are the same as your existing enrichments but require a slightly different configuration and schema. The original enrichments, named {{site.data.keyword.alchemylanguageshort}} enrichments, will be deprecated. {{site.data.keyword.alchemylanguageshort}} Enrichment support will end on **15 January, 2018**. New collections should be enriched with {{site.data.keyword.nlushort}} and any existing collections with {{site.data.keyword.alchemylanguageshort}} configuration files migrated as soon as possible. For information on migrating collections and configuration files that utilize the {{site.data.keyword.alchemylanguageshort}} enrichments, see [Migrating enrichments to {{site.data.keyword.nlushort}}](/docs/services/discovery/migrate-nlu.html).

The {{site.data.keyword.discoveryshort}} [default configuration](/docs/services/discovery/building.html#the-default-configuration) will enrich (add cognitive metadata to) the `text` field of your ingested documents with semantic information collected by these four {{site.data.keyword.watson}} functions - Entity Extraction, Sentiment Analysis, Category Classification, and Concept Tagging. (There are a total of seven {{site.data.keyword.watson}} enrichments available; the others are - Keyword Extraction, Emotion Analysis, and Semantic Role Extraction.)

**Important:** Only the first 50,000 characters of each JSON field selected for enrichment will be enriched.

You can further augment your documents by adding more enrichments to the `text` field, or enriching other fields. To do so using the {{site.data.keyword.discoveryshort}} tooling, [create a custom configuration](/docs/services/discovery/building.html#custom-configuration), choose the field(s) you'd like to enrich and select from the list of available {{site.data.keyword.nlushort}} enrichments:

### Entity extraction

Returns items such as persons, places, and organizations that are present in the input text. Entity extraction adds semantic knowledge to content to help understand the subject and context of the text that is being analyzed. The entity extraction techniques are based on sophisticated statistical algorithms and natural language processing technology, and are unique in the industry with their support for multilingual analysis, context-sensitive disambiguation, and quotation extraction. View the complete list of entity types and subtypes [here](/docs/services/discovery/entity-types.html)

Example portion of a document enriched with Entity Extraction:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "entities": [
         {
           "count": 1,
           "sentiment": {
             "score": 0
           },
           "text": "Acme Corporation",
           "relevance": 0.98389,
           "type": "Company"
           },
           {
           "count": 1,
           "sentiment": {
             "score": 0
           },
           "text": "Atlanta",
           "relevance": 0.532754,
           "type": "Location",
           "disambiguation": {
             "subtype": [
               "AdministrativeDivision",
               "GovernmentalJurisdiction",
               "OlympicHostCity",
               "PlaceWithNeighborhoods",
               "City"
           ],
               "name": "Atlanta",
               "dbpedia_resource": "http://dbpedia.org/resource/Atlanta"
           }
           },
           {
           "count": 1,
           "sentiment": {
             "score": 0
           },
           "text": "Georgia",
           "relevance": 0.469643,
           "type": "Location",
           "disambiguation": {
             "subtype": [
               "StateOrCounty"
           ]
    }
  }
```
{: codeblock}

In the preceding example, you could query the entity type by accessing `enriched_text.entities.type`

`sentiment` is calculated for entity types even if the **sentiment** enrichment is not selected. To learn more about sentiment scoring, see [Sentiment analysis](/docs/services/discovery/building.html#sentiment-analysis).

The `relevance` score ranges from `0.0` to `1.0`. The higher the score, the more relevant the entity. The `disambiguation` field contains the disambiguation information for the entity, which includes the entity `subtype` information and links to the resource(s), if applicable. The `count` is the number of times the entity is mentioned in the document.

### Keyword extraction

Important topics in your content that are typically used when indexing data, generating tag clouds, or when searching. The {{site.data.keyword.discoveryshort}} service automatically identifies supported languages in your input content, and then identifies and ranks keywords in that content.

Example portion of a document enriched with Keyword Extraction:

```json
  {
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "keywords": [
        {
          "text": "Acme Corporation",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.985203
        },
        {
          "text": "new factory",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.821033
        },
        {
          "text": "stockholders",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.66497
        },
        {
          "text": "title",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.332438
        },
        {
          "text": "Atlanta",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.307723
        },
        {
          "text": "Georgia",
          "sentiment": {
            "score": 0
          },
          "relevance": 0.306485
        }
      ]
    }
  }
```
{: codeblock}

In the preceding example, you could query the keyword text by accessing `enriched_text.keywords.text`

`sentiment` is calculated for keywords even if the **sentiment** enrichment is not selected. To learn more about sentiment scoring, see [Sentiment analysis](/docs/services/discovery/building.html#sentiment-analysis).

The `relevance` score ranges from `0.0` to `1.0`. The higher the score, the more relevant the keyword.

### Category classification

Categorizes input text, HTML, or web-based content into a hierarchical taxonomy up to five levels deep. Deeper levels allow you to classify content into more accurate and useful subsegments. View the complete list of categories [here](/docs/services/discovery/categories.html).

Example portion of a document enriched with Category Classification:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "categories": [
        {
          "score": 0.361614,
          "label": "/business and industrial"
        },
        {
          "score": 0.329377,
          "label": "/business and industrial/company/merger and acquisition"
        },
        {
          "score": 0.154254,
          "label": "/business and industrial/business operations/business plans"
        }
      ]
```
{: codeblock}

In the preceding example, you could query the category label by accessing `enriched_text.categories.label`

The `label` is the detected category. The hierarchy levels are separated by forward slashes. The `score` for that category will range from `0.0` to `1.0`. The higher the score, the greater the confidence in that category.

### Concept tagging

Identifies concepts with which the input text is associated, based on other concepts and entities that are present in that text. Concept tagging understands how concepts relate, and can identify concepts that are not directly referenced in the text. For example, if an article mentions CERN and the Higgs boson, the Concepts API functions will identify Large Hadron Collider as a concept even if that term is not mentioned explicitly in the page. Concept tagging enables higher level analysis of input content than just basic keyword identification.

Example portion of a document enriched with Concept Tagging:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "concepts": [
        {
          "text": "Acme Corporation",
          "relevance": 0.91136,
          "dbpedia_resource": "http://dbpedia.org/resource/Acme_Corporation"
        },
        {
          "text": "Factory",
          "relevance": 0.886784,
          "dbpedia_resource": "http://dbpedia.org/resource/Factory"
        }
      ]
```
{: codeblock}

In the preceding example, you can query the concept text type by accessing `enriched_text.concepts.text`

The `relevance` score ranges from `0.0` to `1.0`. The higher the score, the more relevant the concept. Links to the resource(s) are provided, if applicable.

### Semantic Role extraction

Identifies subject, action, and object relations within sentences in the input content. Relation information can be used to automatically identify buying signals, key events, and other important actions.

Example portion of a document enriched with Semantic Role Extraction:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
      "enriched_text": {
      "semantic_roles": [
        {
          "subject": {
            "text": "The stockholders",
            "keywords": [
              {
                "text": "stockholders"
              }
            ]
          },
          "sentence": " The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
          "object": {
            "text": "pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia",
            "keywords": [
              {
                "text": "Acme Corporation"
              },
              {
                "text": "new factory"
              },
              {
                "text": "Atlanta"
              },
              {
                "text": "Georgia"
              }
            ],
            "entities": [
              {
                "type": "Company",
                "text": "Acme Corporation"
              },
              {
                "type": "Location",
                "text": "Atlanta",
                "disambiguation": {
                  "subtype": [
                    "AdministrativeDivision",
                    "GovernmentalJurisdiction",
                    "OlympicHostCity",
                    "PlaceWithNeighborhoods",
                    "CityTown",
                    "City"
                  ],
                  "name": "Atlanta",
                  "dbpedia_resource": "http://dbpedia.org/resource/Atlanta"
                }
              },
              {
                "type": "Location",
                "text": "Georgia",
                "disambiguation": {
                  "subtype": [
                    "StateOrCounty"
                  ]
                }
              }
            ]
          },
          "action": {
            "verb": {
              "text": "be",
              "tense": "past"
            },
            "text": "were",
            "normalized": "be"
          }
        }
      ]
```
{: codeblock}

In the preceding example, you could query the relation subject text by accessing `enriched_text.relations.subject.text`

`sentiment` is calculated for relations even if the **sentiment** enrichment is not selected. To learn more about sentiment scoring, see [Sentiment analysis](/docs/services/discovery/building.html#sentiment-analysis). It will not extract `entities` or `keywords` (as shown in the example) unless you also select the **entity** and **keyword** enrichments. See [Entity extraction](/docs/services/discovery/building.html#entity-extraction) and [Keyword extraction](/docs/services/discovery/building.html#keyword-extraction) for more information on those enrichments.

The `subject`, `action`, and `object` are extracted for every sentence that contains a relation.

### Sentiment analysis

Identifies attitude, opinions, or feelings in the content that is being analyzed. The {{site.data.keyword.discoveryshort}} service can calculate overall sentiment within a document, sentiment for user-specified targets, entity-level sentiment, quotation-level sentiment, directional-sentiment, and keyword-level sentiment. The combination of these capabilities supports a variety of use cases ranging from social media monitoring to trend analysis.

Example portion of a document enriched with Sentiment Analysis:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "sentiment": {
        "document": {
        "score": 0.459813,
        "label": "positive"
  }
}
```
{: codeblock}

In the preceding example, you could query the sentiment label by accessing `enriched_text.sentiment.document.label`

The `label` is the overall sentiment of the document (`positive`, `negative`, or `neutral`). The sentiment `label` is based on the `score`; a score of `0.0` would indicate that the document is `neutral`, a positive number would indicate the document is `positive`, a negative number would indicate the document is `negative`.

### Emotion analysis

Detects anger, disgust, fear, joy, and sadness implied in English text. Emotion Analysis can detect emotions that are associated with targeted phrases, entities, or keywords, or it can analyze the overall emotional tone of your content.

Example portion of a document enriched with Emotion Analysis:

```json
{
  "text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia.",
    "enriched_text": {
      "emotion": {
        "document": {
          "emotion": {
          "disgust": 0.102578,
          "joy": 0.626655,
          "anger": 0.02303,
          "fear": 0.018884,
          "sadness": 0.096802
    }
  }
}
```
{: codeblock}

In the preceding example, you could query the `joy` Emotion by accessing `enriched_text.emotion.document.emotion.joy`

Emotion Analysis analyzes your text and calculates a score for each emotion (anger, disgust, fear, joy, sadness) on a scale of `0.0` to `1.0`. If the score of any emotion is `0.5` or higher, then that emotion has been detected (the higher the score above `0.5`, the higher the relevance). In the snippet shown, `joy` has a score above 0.5, so {{site.data.keyword.watson}} detected joy.

After making any changes, click **Apply and Save**.

Enrichment pricing information is available on [{{site.data.keyword.Bluemix_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/catalog/services/discovery/){: new_window}.

#### Enrichment language support

{{site.data.keyword.discoveryshort}} supports English, German, and Spanish language collections, however, several enrichments are not supported in German and Spanish. The supported enrichments for each language are:

|  | Sentiment Analysis | Semantic Role Extraction | Keyword Extraction | Entity Extraction | Emotion Analysis | Concept Tagging | Category Classification |
|--|--------------------|--------------------------|--------------------|--------------------|-----------------|-----------------|-------------------------|
| English    | X                        | X                  | X                  | X               | X               | X              | X              |
| German     | X                        |                    | X                  | X               |                 |                |                |       
| Spanish    | X                        | X                  | X                  | X               |                 | X              | X             |

### Understanding the difference between Entities, Concepts, and Keywords
{: #udbeck}

At first glance, **Entity extraction**, **Concept tagging** and **Keyword extraction** appear to be similar enrichments. We'll use the text from the enrichment examples to show the differences between them.

```json
"text": "The stockholders were pleased that Acme Corporation plans to build a new factory in Atlanta, Georgia."
```
{: codeblock}

Since the **Entity Extraction** enrichment extracts persons, places, and organizations in the input text, **Entity extraction** returns the following entity types:

```json
"type": "City"
"text": "Atlanta"

"type": "Company"
"text": "Acme"

"type": "StateOrCounty"
"text": "Georgia"
```
{: codeblock}

Since the **Concept tagging** enrichment understands how concepts relate, it can identify concepts that are not directly referenced in the text. For example, if an article mentions CERN and the Higgs boson, it will identify Large Hadron Collider as a concept even if that term is not mentioned explicitly. Since our example document text is only one sentence, there are no related concepts, so **Concept tagging** returns the following concepts:

```json
"text": "Acme Corporation"
"text": "factory"
```
{: codeblock}

Since the **Keyword extraction** enrichment identifies content typically used when indexing data, generating tag clouds, or searching, **Keyword extraction** returns the following keywords:

```json
"text": "Acme Corporation"
"text": "new factory"
"text": "stockholders"
"text": "Atlanta"
"text": "Georgia"
```
{: codeblock}

These enrichments work together to help you build better queries.

## Normalizing data
{: #normalizing-data}

The last step in customizing your configuration file is doing a final cleanup, also known as normalization.

In the **Normalize** section of the {{site.data.keyword.discoveryshort}} tooling:

-   You can move, merge, copy or remove fields.
-   Empty fields (fields that contain no information) will be deleted by default. You can change that using the **Remove empty fields** toggle.

After making any changes, click **Apply and Save**, then **Done**. You will be returned to the **Your Data** screen, where you can apply this configuration to the collection of your choice.

## Normalizing entities
{: #normalizing-entities}

### Using CSS selectors to extract fields
{: #using-css}

You can perform an additional normalization by using CSS selectors via the Discovery API.

If you are ingesting well-formed HTML, you can normalize it, use CSS selectors to extract JSON fields from it, and then apply enrichments to the extracted fields. Edit your configuration file to enable this feature. Specifically, add an `extracted_fields` element to the `conversions/html` hierarchy, then specify field names, CSS selectors, and field types, as follows:

```json
{
  "name": "Extract JSON config",
  "description": "New configuration enabling extraction of JSON fields from HTML",
  "conversions": {
    ...
    "html": {
      ...
      "extracted_fields": {
        "{field_name_1}": {
          "css_selector": "{CSS_selector_expression_1}",
          "type": "{field_type}"
        },
        ...
        "{field_name_N}": {
          "css_selector": "{CSS_selector_expression_N}",
          "type": "{field_type}"
        }
      }
    ...
    }
  }
}
```
{: codeblock}

Specify values for the new fields as follows:

-   `field_name` — The name of the field that will be added to the JSON output.
-   `CSS_selector_expression` — The CSS selector that is to be run against the input HTML to extract the fields. The expression can have one or more matches.

    Valid CSS selectors are those specified by the [JSoup parser ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://jsoup.org/apidocs/org/jsoup/select/Selector.html){: new_window} and its [selector syntax ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://jsoup.org/cookbook/extracting-data/selector-syntax){: new_window}. A short list is provided at [Common selectors](/docs/services/discovery/building.html#common-selectors).
-   `field_type` — Either `array` or `string`. If the field type is not specified, it defaults to `array`. Note that type `string` can be enriched, but information stored in an `array` cannot be enriched unless the array's items are first extracted into text fields.

**Warning:** If a CSS selector matches both a parent node and one or more of its children, the text content of the nodes will be duplicated in the JSON output.

The following JSON passage shows the relevant section of the Default Configuration to which you add CSS selector information.

```json
{
  "name": "Default Configuration",
  "description": "The configuration used by default when creating a new collection without specifying a configuration_id.",
  "conversions": {
    ...
    "html": {
      "exclude_tags_completely": [
        "script",
        "sup"
      ],
      "exclude_tags_keep_content": [
        "font",
        "em",
        "span"
      ],
      "exclude_content": {
        "xpaths": []
      },
      "keep_content": {
        "xpaths": []
      },
      "exclude_tag_attributes": [
        "EVENT_ACTIONS"
      ]
    }
    ...
  }
}
```
{: codeblock}

The following passage shows the configuration with a new name and description, as well as the location where you can specify CSS selectors.

```json
{
  "name": "Extract JSON config",
  "description": "New configuration enabling extraction of JSON fields from HTML",
  "conversions": {
    ...
    "html": {
      "exclude_tags_completely": [
        "script",
        "sup"
      ],
      "exclude_tags_keep_content": [
        "font",
        "em",
        "span"
      ],
      "exclude_content": {
        "xpaths": []
      },
      "keep_content": {
        "xpaths": []
      },
      "exclude_tag_attributes": [
        "EVENT_ACTIONS"
      ],
      "extracted_fields": {
        "{field_name_1}": {
          "css_selector": "{CSS_selector_expression_1}",
          "type": "{field_type}"
        },
        ...
        "{field_name_N}": {
          "css_selector": "{CSS_selector_expression_N}",
          "type": "{field_type}"
        }
      }
    }
  }
  ...
}
```
{: codeblock}

Finally, the following passage shows the configuration the new name and description as well as some CSS selectors. The selectors match items in an HTML example that is described further down on this page.

```json
{
  "name": "Extract JSON config",
  "description": "New configuration enabling extraction of JSON fields from HTML",
  "conversions": {
    ...
    "html": {
      "exclude_tags_completely": [
        "script",
        "sup"
      ],
      "exclude_tags_keep_content": [
        "font",
        "em",
        "span"
      ],
      "exclude_content": {
        "xpaths": []
      },
      "keep_content": {
        "xpaths": []
      },
      "exclude_tag_attributes": [
        "EVENT_ACTIONS"
      ],
      "extracted_fields": {
        "chapters": {
          "css_selector": ".chapter",
          "type": "array"
        },
        "authors": {
          "css_selector": ".author"
        },
        "authors_str": {
          "css_selector": ".author",
          "type": "string"
        },
        "comments": {
          "css_selector": "[^comments-content]"
        }
      }
    }
  }
  ...
}
```
{: codeblock}

If you load the following HTML document into a collection that uses an updated configuration, the CSS selectors match the appropriate attributes and values in the HTML.

```html
<html>
  <body>
    <div id="authors">
      <div class="author"><span class="first_name">Jane</span> <span class="last_name">Rain</span></div>
      <div class="author">Joe Snow</div>
  </div>
  <div class="chapter"><h1>The Rain in Spain</h1><p>falls mainly on the plain.</p></div>
  <div class="chapter"><h1>How I Learned to Stop Worrying</h1><p>and love my snowblower.</p></div>
  <span id="comments-section">
    <h4>Comments:</h4>
    <span id="comments-content-1">Rain gives me pain.</span>
    <span id="comments-content-2">All snow must go!</span>
  </span>
</body></html>
```
{: codeblock}

After the preceding HTML is ingested and enhanced, the {{site.data.keyword.discoveryshort}} service returns the following JSON:

```json
{
  "extracted_metadata": { ... },
  "html": "...",
  "text": "...",
  "extracted_fields": {
    "authors": [ "Jane Rain", "Joe Snow" ],
    "authors_str": "Jane Rain\n\nJoe Snow",
    "chapters": [ "The Rain in Spain\n\nfalls mainly on the plain.", "How I Learned to Stop Worrying\n\nand love my snowblower." ],
    "comments": [ "Rain gives me pain.", "All snow must go!" ]
  }
}
```
{: codeblock}

After deciding which HTML elements you want to extract, you can then further modify the configuration file to specify the enrichments you want to apply to them.

#### Common selectors

Some common CSS selectors include the following:

  - `tag` — Matches the `tag` name
  - `.class` — Matches the value of `class`
  - `#id` — Matches the value of `id`
  - `[attribute]` — Matches any tag with the specified `attribute`, regardless of value
  - `[attribute=value]` or `[attribute="value"]` — Matches the specified `attribute` and `value`
